---
layout: post
title: Bicker Progress - (Almost) Inventors' Day
date: 2020-02-10 06:41:55-0500
categories: programming
tags: [ruby, rails, programming, project, devjournal, bicker]
summary: Progress report on Bicker
thumbnail: /blog/assets/New_Inventions_of_Modern_Times_-Nova_Reperta-_The_Invention_of_the_Compass_plate_2_MET_DP841121.png
offset: -8%
---

As [previously discussed]({% post_url 2020-01-06-bicker %}), I am currently in the process of remaking [Bicker](https://bicker.colagioia.net/) with modern technologies and architecture, hopefully along with lessons learned over the last decade about what makes a good community system.  In the interest of transparency, I'm using the blog as a kind of developer journal while I work, posting occasional updates as to where things stand.

![Invention of the Compass](/blog/assets/New_Inventions_of_Modern_Times_-Nova_Reperta-_The_Invention_of_the_Compass_plate_2_MET_DP841121.png "Invention of the Compass")

If you want to read the other posts in the series, you can get a full list of posts under [the "bicker" tag](/blog/tag/bicker).

Unfortunately, this has been another busy week, so I didn't accomplish as much as I'd like, but there's still *some* progress.

## Testing, Preliminaries

As mentioned [last time]({% post_url 2020-02-03-bicker-pre-reply %}), it's time to add tests to see if adding them after the code has already been written is significantly more painful than starting development with them.

I settled on [RSpec](https://rspec.info/), which was trivial to get running.  Add the `rspec` gem to the `Gemfile`, install, and run...

```sh
rspec --init
```

That creates a configuration file (`.rspec`) and helper object (`spec/spec_helper.rb`).  Running `rspec` now shows exactly what we'd expect:  Nothing to do, so no failures.

That'll have to do, for now...

## Inserting Replies

We could get away with posting the reply form to the server and retrieving the updated page.  That would follow the same scheme as posting messages already do.  But that's a little bit out of date, in terms of user experience, and is also slower and clunkier than necessary.

Instead, what makes more sense is to *just* send the reply information to the server and change the [DOM](https://en.wikipedia.org/wiki/Document_Object_Model) for the target paragraph.

### Added Instrumentation

Either way, something we definitely need is more tracking.  We need the ID of the paragraph---something we already have, but aren't yet passing into the React components---and we need the distance into the string where each punctuation mark sits.

The latter sounds easy enough, of course.  The paragraph controller already splits the string into an array of substrings---alternating text with punctuation, in most cases---and each of those substrings obviously has a length.  However, that's a bit more naïve than we want, because the length of our punctuation in Markdown (which is how the paragraphs are stored, remember) isn't always the same as the length of our punctuation in HTML.

We can fix that by adding a mapping in the Paragraph component.

```javascript
const lengths = {
  '.': 1,
  ',': 1,
  '!': 1,
  '?': 1,
  ';': 1,
  ':': 1,
  '(': 1,
  ')': 1,
  '&': 1,
  '/': 1,
  '&ndash;': 2,
  '&#8212;': 2,
  '&mdash;': 3,
  '&#8211;': 3,
  '&hellip;': 3,
  '&#8230;': 3,
};
```

If our fragment is a key in the object, we have a new length.  Otherwise, we can use `c.length` as we normally would.

### Mark the Replies

Now, we get to the meat of things.  Our various React components need paragraph-id and paragraph-offset properties, now, and these trickle down to the reply form, itself.  There, we can add an `offset` and `pid` attribute to the button.

While we're here, we also need to change the button type to simply `button` and give it an `onClick` handler.  This solves our unnecessary problem from last time of how to prevent the submission from refreshing the page.  We can start with something simple, like this.

```javascript
function submitReply(e) {
  e.persist();
  var target = e.target;
  var offset = Number(target.attributes.offset.value);
  var paraId = Number(target.attributes.pid.value);

  console.log(`${paraId} - ${offset}`);
}
```

Now, the reply form should have enough information to pack up the reply to send it back to the controller.

### Sending the Reply

We now need to expand our `submitReply()` function to also retrieve and escape the reply message, then send it off.  It's not a great move, but for now, I'm going to exploit the fact that the `textarea` control is the first child of the reply form.  There's a better way to find it, but it's not something I have time to test and debug, right now.

```javascript
function submitReply(e) {
  e.persist();
  var target = e.target;
  var offset = Number(target.attributes.offset.value);
  var paraId = Number(target.attributes.pid.value);
  var parent = target.parentNode;
  var textarea = parent.childNodes[0];
  var message = encodeURIComponent(textarea.value);
  var request = new XMLHttpRequest();
  var url = `/api/v1/messages/reply?paraId=${paraId}&offset=${offset}&message=${message}`;

  request.open(
    'GET',
    url,
    true
  );
  request.onload = function() {
    if (this.status >= 200 && this.status < 400) {
      var resp = this.response;
      console.log(this.response);
    } else {
      console.error(this);
    }
  };

  request.onerror = function() {
    // There was a connection error of some sort
  };

  request.send();
}
```

Note that we:

 * Pull the offset and paragraph ID off of the button attributes,
 * Assume the `textarea` is the first child of the button's parent,
 * URL-encode the reply text so that it can be inserted into the request path, and
 * Send the AJAX request.

We also need to adjust the routes.

```ruby
namespace :api do
  namespace :v1 do
    resources :messages, only: [
      :index,
      :create,
      :destroy,
      :update,
      :reply
    ] do
      collection do
        get 'reply'
      end
    end
  end
end
```

We allow the new action and create a path for it.  And then restart the server, since we need to reload the routes.

Obviously, the responses need to be filled in, once we start getting useful responses.

## Receiving the Reply Information

Over in `app/controllers/api/v1/messages_controller.rb`, we need to create our `reply` action.  We'll just go with a stub, for now, to confirm that *something* happens.

```ruby
def reply
  args = {
    paraId: params[:paraId],
    offset: params[:offset],
    message: params[:message],
  }
  respond_with args
end
```

So, now when we try to post a reply, the server sends back something like the following.

```json
{
  "paraId": "4",
  "offset": "189",
  "message": "This is a reply..."
}
```

That's clearly only a dumb echoing of the parameters we submitted, but it validates that we now have enough information to get the relevant paragraph, replace it with two pieces, and add the reply as a child to the first part.

## Splitting the Paragraph

Now that we have the above working, we can get to messing around with the data.  After we get rid of that `args` object, we need the paragraph object and the two halves of the text.

```ruby
paraId = params[:paraId].to_i
offset = params[:offset].to_i
message = params[:message].strip
paragraph = Paragraph.find(paraId)
firstPart = paragraph.content[0..offset].strip
lastPart = paragraph.content[offset + 1..-1].strip
```

The parameters are passed in as text, of course, meaning that we want them converted to integers for IDs and indices.  Since we know that all of these divisions are happening at a punctuation mark, we also want to `strip` the resulting fragments, so that we aren't left with any dangling whitespace.

From here, we already know how to handle the replacement, because we already did something very much like this to insert the message paragraphs in the first place!

Specifically, we want to work backwards:

 * Create a new paragraph with `lastPart` as the `content` and its `next_id` pointing to whatever our existing paragraph currently does.
 * Update the existing paragraph so that its `content` is `firstPart` and its `next_id` to point to our new paragraph.  We don't want to create a new one, because there's (usually) another paragraph out there already pointing to this one.
 * Note that, if `lastPart` is empty, we can skip both steps, since there isn't a second paragraph.
 * Create any paragraphs needed for the reply, with their `parent_id` set pointing to the original paragraph.

We already have code to handle that last step, so we only really need to copy it over from the original messages controler, for now, and come back to refactor it later.

## Next

That's it for this time.  From here, we need to *show* the replies, both when adding the replies to finish the circuit we've started here and on displaying the message in its entirety...probably in the reverse order.  And now that we have RSpec in place and we have most of the base functionality running, it's a good time to start writing some tests.

Oh, and it looks like there's a small bug in escaping the message text.  The punctuation in the escaped text gets transformed into buttons and we also miscount the length of the strings due to the extra characters in an escaped string.  Small issue, but I'll still want to deal with it.

#### <i class="fas fa-gem"></i>

* * *

**Credits**:  The header image is [Invention of the Compass](https://commons.wikimedia.org/wiki/File:New_Inventions_of_Modern_Times_-Nova_Reperta-,_The_Invention_of_the_Compass,_plate_2_MET_DP841121.jpg) from **New Inventions of Modern Times**, circa 1600, courtesy of [The Metropolitan Museum of Art](https://www.metmuseum.org/art/collection/search/659663).
