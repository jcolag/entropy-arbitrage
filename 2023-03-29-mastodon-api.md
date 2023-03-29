---
layout: post
title: Mastodon's API (The Pitfalls)
date: 2023-03-29 06:43:05-0400
categories:
tags: [mastodon, programming, techtips]
summary: What I learned on my first couple of projects
thumbnail: /blog/assets/wavKNbT207mwbN89FSIs--2--4v242.png
teaser: The API doesn't really need much explanation, though I found a couple of potential traps.
proofed: true
---

Over the past couple of months, I've started a handful of [tools for working with Mastodon](https://github.com/jcolag/tool-trunk), based on---as you can probably guess---the [Mastodon API](https://docs.joinmastodon.org/client/intro/).  Initially, I planned to write up a post about the entire experience of working with the API, but things mostly flowed so smoothly that I couldn't see writing a post about things working.

![An AI-generated image of a brown and gray robot mastodon moving through a valley jungle](/blog/assets/wavKNbT207mwbN89FSIs--2--4v242.png "Not how I expected the server room to look, honestly...")

I could show the code that I created to make an HTTP GET request, like this...

```ruby
def make_http(server, path)
  url = URI "https://#{server}/#{path}"
  http = Net::HTTP.new url.host, url.port
  http.use_ssl = true
  [url, http]
end

def error(response)
  puts "Error: #{response.code} - #{response.body}" unless response.code == '200'
  response.code != '200'
end

def call_http_get(server, path, token)
  header_token = "#{token['token_type']} #{token['access_token']}"
  url, http = make_http server, "api/v1/#{path}"
  request = Net::HTTP::Get.new url, { 'Authorization' => header_token }
  response = http.request request

  return nil if error response

  JSON.parse response.body
end
```

You can see that I wouldn't really have much to say, though.  The `call_http_get()` method gets the HTTP `Authorization` token from configuration, points at the API endpoint, and makes the request.  Post complete.  Let's go home, right?

Instead, I'll talk about the tiny handful of stumbling blocks that I hit, while working.  Some of this might seem Ruby-specific, because of the tools and approaches that programmers will more likely talk about, but not entirely.

## Authenticating

I should note, first, that I haven't done authentication work, yet.  I wrote code for it, but I soon realized that creating connection information for a developer/test application, it already includes the access token.

![A table from Mastodon's app developer configuration, showing a (fake, spelling out a warning not to use them) client key, client secret, and access token](/blog/assets/Mastodon-dev-application-keys.png "I don't know why it bothers with the client key and secret")

*Requesting* an access token with the client key and secret provides a bogus token.  As a result, until I polish my tools for use by non-developers, I don't have a reason to exercise that authentication code.  If anything goes wrong, I'll write a post about it.

## POST Arguments

Largely because of the discussions that show up when you search for specifying parameters in HTTP POST messages using Ruby, I spent longer than I'd like to admit trying to make this code work.

```ruby
request.set_form_data parameters
response = http.request request
```

The [`.set_form_data()`](https://apidock.com/ruby/Net/HTTPHeader/set_form_data) method doesn't do what the name suggests that it does---hence deprecating it---so it didn't help.  And while I assume that the API documentation says so, somewhere, I eventually read through someone's library code in another language to discover that we actually need to specify the parameters as a JSON string *as* the request body.

```ruby
response = http.request request, parameters.to_json
```

Not only does this work, but it takes substantially less work, and needs one less library.

## Using Idempotency Correctly

I mostly attribute the problems, here, to my not thinking things through.

If you don't already know the term, I [described idempotency recently]({% post_url 2023-03-06-righteous %}) as follows...with some light editing.

 > Itempotency refers to (idempotent) operations, where you can apply them repeatedly to your system state---usually a database, these days---and not worry if you've made repeated changes.  We care about idempotency in distributed systems, where the connection might drop, without you knowing exactly where the operation interrupted; for idempotent operations, you retry without checking, because it won't do any damage.
 >
 > For example, you generally idempotently delete things, but you can't idempotently give someone money, because you can't delete a record "too many times," but you *can* transfer the wrong amount of money by repeating a payment.  In Mastodon's case, the API makes posting *optionally* idempotent, by allowing the application to provide the ID to say that it should treat all the toots identically.

In other words, if we make twelve posts with the same Idempotency ID---an arbitrary string---then the server will discard the later eleven, because we called them all the same message.

Anyway, while I may have had more problems than this, I definitely didn't think through my strategy for using idempotency, and the documentation has a minor flaw on the topic.  Specifically, when testing, I used the same test/warning message, in case I had a sudden network problem, and so couldn't catch and delete successful messages.

 > Ignore me.  I am testing a script, and will probably delete this before you can finish your reply, assuming that it posts at all...

If you saw that while following me, now you know why.

In any case, in my posting/scheduling script---posting and scheduling use the same API endpoint, which I appreciate, but also makes me wonder why Mastodon's standard web interface doesn't already expose scheduled toots---uses an SHA-256 hash, as a Base-64 string.

```ruby
request = Net::HTTP::Post.new url,
                              { 'Authorization' => header_token,
                                'Content-Type' => 'application/json',
                                'Idempotency-Key' => Digest::SHA256.base64digest(parameters[:status]) }
```

Not having thought this through, many of you have already guessed, I did a *lot* of testing, where my test message provided the same hash/digest value, and so didn't have meaning to the server.  🤦

However, I blame Mastodon for some of my confusion.  If you read the documentation for [posting a toot](https://docs.joinmastodon.org/methods/statuses/#create)---apparently, I should call them "statuses," but I consider the inner part of the toot a status, so I won't do that...---you find [three responses](https://docs.joinmastodon.org/methods/statuses/#response), and HTTP 200 (OK) when the toot goes through, 401 (Unauthorized) when we don't have a valid access token, or a 422 (Unprocessable entity) when it can extract enough information.

When I got what I now identify as an idempotency conflict, though, I get an HTTP 404 (Not found) error.  It makes some sense, but I assumed that I had a problem with the attached media.  And speaking of media...

## Media IDs

Here, my problems mostly came from the prior issue struggling with Idempotency IDs through proxy wars.  However, I will point out one issue that periodically tripped me up.  When you [upload media](https://docs.joinmastodon.org/methods/media/#v2) for an upcoming toot, you get an object back describing what the server has determined (so far) about the file.  That includes a numerical ID.

Meanwhile, carefully note how the "post a new status" documentation describes the `media_ids[]` parameter.

 > Array of String.

Most interpreted languages don't care about data types, and as far as I knew, they develop Mastodon with Ruby, so it doesn't often matter if you send media IDs as an integer or string.  However, in the conversion to JSON---remember the [POST arguments](#post-arguments) section, above---and back, it does seem to at least occasionally make a difference, with integer media IDs silently failing to match anything.

## Overall

As I mentioned, things have gone far more smoothly than I expected.  For many kinds of work, like pulling your notifications or a user's most recent toots, you can mostly find the API endpoint in the documentation, call it, and format the output.  For other work, it honestly doesn't take much more effort.

Seriously, I can't think of another API that I've used where I've created full applications and only had three (and maybe a half) significant issues, none of which need more than *slightly* better documentation to solve them.

#### <i class="fab fa-mastodon"></i>

* * *

**Credits**:  I (John) built the header image on an image (generated by John) on [NightCafé Studio](https://nightcafe.studio/), and hereby released under the same CC BY-SA 4.0 terms as the blog.
