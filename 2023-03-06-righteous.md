---
layout: post
title: Developer Diary, European Day of the Righteous
date: 2023-03-06 06:35:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/European-Day-of-the-Righteous-logo.png
teaser: This week's updates include new calendars and sentiment analysis for my Morning Dashboard, finally getting my Mastodon scheduler script working, and adding these teasers to all blog announcements.
proofed: true
---

* Ignore for ToC
{:toc}

Today, in a self-explanatory part of the world, people celebrate the [European Day of the Righteous](https://en.wikipedia.org/wiki/European_Day_of_the_Righteous), originally a memorial for the Armenian Genocide, but now more broadly honoring people who have taken stands against authoritarians or crimes against humanity.

![All in blue, the European circle of stars logo to the left of the words "European Day of the Righteous"](/blog/assets/European-Day-of-the-Righteous-logo.png "I don't think that I've ever seen a holiday with its own logo")

While we talk about code, we should also all aspire to taking similar stands.  As I often mention, because we often *see* this situation, it doesn't generally take much actual resistance for authoritarians to walk away, so even small acts to help people can---at least in theory---make a difference.

## Morning Dashboard

{% github jcolag/dash %}

I concluded last weekend that I need more calendars on my **Morning Dashboard**.  I don't *use* the dates for anything, yet, but watching the ebb and flow of the various cycles interest me on a peculiar level.  As a result, I added the Islamic, Tibetan, and Ethiopian calendars.

I then took on a small project that I've wanted to kick around for a while.  As readers may know from my [*things that work* post]({% post_url 2022-11-27-worked %}) late last year, I type up a quick journal entry every night as a memory aid, reviewing what I worked on, watched, ate, and otherwise spent my time, along with any miscellaneous thoughts that the day might have brought up.  I don't do much with those files after writing them, so they have always seemed ripe for analysis.

I decided to start with word count and sentiment, the total sentiment per word, specifically.

![A bar chart representing, for the past ninety-one days, the sentiment as height and the length as opacity, most prominently featuring a spike in sentiment around two months ago and a precipitous dip about a week ago](/blog/assets/morning-dashboard-journal-sentiment.png "I expected less stability than that, honestly.")

As you might already know, sentiment doesn't necessarily map to mood, especially for someone like me, who has a habit of describing things as "not good" or "not bad," which muddles word-by-word sentiment.  However, this information does turn up some interesting ideas to investigate further.  For example, check out my older analysis of sleep time.

![A bar chart representing, for the past ninety-one days, the length of sleep as height and my morning reaction time as opacity, most prominently featuring a sudden jump up around two months ago and a sudden dip about a week ago](/blog/assets/morning-dashboard-sleep-time.png "I agree that I need to put more effort into consistent sleep patterns.")

While they don't match perfectly, do you maybe notice the suspicious items on these charts?  You can't and shouldn't need to see the dates, but a couple of days before Christmas, I wrote the highest-sentiment journal entry, despite its brevity, and then I slept the longest that I have for three months.  The broad shape of the graphs generally match, but the next time something distinctive happens on both brings us to about a week ago, when I wrote the journal entry with the *lowest* sentiment, followed by the second-shortest time asleep.  I could pick out a few more close correlations, but as I said earlier, the correlation on these two items seems strong enough to warrant some investigation on their own.

Now, correlation doesn't equate to causation.  I don't believe that writing an angry or disappointed journal entry---much of which *probably* hinges on what I think about what I watch on television, since that probably includes the most emotional language---leads to a bad night's sleep.  It could happen, sure, that harsh words work me into an insomniac lather.  But more likely, something causes both my mood (to the extent that sentiment maps to mood) and sleep schedule to shift.  Regardless of whether I have found causation, though, I probably have something that I should work on, even if it involves something as minor as breaking my habit of hedging how I write about my assessment of things, or accelerating my time to dropping television shows that I don't immediately find myself enjoying.

In fact, in the spirit of full disclosure hoping to help someone in the future, without bothering with *what* I watched, I present relevant phrases from my assessment of those shows on that may have contributed to low sentiment.

 * Not bad
 * Nothing exciting
 * It really annoys me...half-asses these...
 * Enough going on, certainly
 * ...someone who he *doesn't* constantly complain to...he's an ass...Probably not

This goes back to what I said about the sentiment words probably resting heavily on my media consumption.  I watched five things (television shows, movies, and/or videos, but definitely on my television), of which I had harsh things to say about two, ambivalent reactions that include literally negative *words* for another two---the algorithm would consider "not bad" as two negative words, rather than a slightly positive phrase---and one ambivalent and oddly cryptic comment.  I see three possibilities, here.  First, maybe my phrasing really does weigh on my mind, when I go to bed.  Second, I don't like these shows all that much, and should stop watching anything open-ended that I don't love...which probably makes sense, regardless of the effect on sleep.  And third, something happened that both put me in an uncharitable mood for the shows and later disrupted my sleep.

Anyway, I get excited about this sort of thing to a rather embarrassing degree.  Part of me wants to check this new data against weather, communications, social media, and more...

## Mastodon Tool Trunk

{% github jcolag/tool-trunk %}

It took me more than long enough to get around to it, but I *finally* got my Mastodon scheduler script working, though based on my changes, I couldn't tell you if my problem came from my procedure, a server glitch, or my code.

To spare you the long story---I'll probably write something up on using the Mastodon API, soon---I would frequently receive an error telling me "record not found."  That seems like a problem *somewhere*, since the ["post a status" endpoint](https://docs.joinmastodon.org/methods/statuses/#create) doesn't list an [HTTP 404](https://en.wikipedia.org/wiki/HTTP_404) code as a possible output.

While I need to investigate further, I *suspect* that my use of an "idempotency ID" might have sidelined me, again, either because I misused it or because the server had problems.  Itempotency refers to (idempotent) operations, where you can apply them repeatedly to your system state---usually a database, these days---and not worry if you've made repeated changes.  We care about idempotency in distributed systems, where the connection might drop, without you knowing exactly where the operation interrupted; for idempotent operations, you retry without checking, because it won't do any damage.  For example, you generally idempotently delete things, but you can't idempotently give someone money, because you can't delete a record "too many times," but you *can* transfer the wrong amount of money by repeating a payment.  In Mastodon's case, the API makes posting *optionally* idempotent, by allowing the application to provide the ID to say that it should treat all the toots identically.

In any case, I suspect that my idempotency ID might not have had any content in it, leading to "collisions" with every other ID for an empty message.  Fixing a typo or two, adding a delay before sending the media and toot, and updating my test script to include the current time in my test message seems to have fixed everything.

Did I say *fixed*?  No, not quite.  I mean that fixed the "not found" error.

Once I cleared the idempotency problem, I discovered that my toots wouldn't post with the images attached.  After more research than I honestly care to admit, I discovered that I had overcomplicated things by trying to explicitly set the parameters as HTTP form data.  Doing so creates a request body that looks like a URL query string, such as `status=Hello, Fediverse&cw=Greetings`.  For reasons that I don't understand---or care about, at the moment---the server only pulls certain information out of such a request, and ignores the rest.

Instead, I needed to format the request parameters as a JSON object.  That, as it turns out, takes care of itself, for the most part.

```ruby
response = http.request request, parameters.to_json
```

Now it picks up my `media_ids` property, and therefore attaches images to toots.  This week's pre-scheduled toots all come from scheduling with this script, in fact, so please contact me if you see one of them go rogue.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

As mentioned [last week]({% post_url 2023-02-27-marathi %}), if you follow me on social media---and really, why *wouldn't* you?---you might have noticed that the last week or so of announcement posts across [Buy Me a Coffee](https://www.buymeacoffee.com/jcolag), [Mastodon](https://mastodon.social/@jcolag/), [Diaspora](https://nota.404.mn/people/e4313920967a0136074b076893c08a76), [Post.News](https://post.news/@/jcolag), [Cohost](https://cohost.org/jcolag/), and [Spoutible](https://spoutible.com/jcolag) now bear some resemblance to each other, plus or minus message lengths and URL previews.  If you've investigated this further---or if you remember last week's post---you might also have noticed that new blog posts also carry that "teaser" blurb.

As a result, I have updated my build script for the blog, so that it adds that blurb to the announcements.  Most of the platforms require me to manually create the post, because they haven't published an API, yet, but this process at least helps me to not scramble at the last minute to think of something to say when I send the e-mail notifications through Buy Me a Coffee, for example, then feel guilty that I didn't bother to write anything useful on Mastodon, where I have my largest audience.

## Next

Now that I seem to have a handle on posting to Mastodon through the API, I need to start parsing my [Friday posts](/blog/tag/linkdump) to provide the parameters used by the script.  As I've mentioned, I can probably "parse" fairly loosely by checking lines.  Each entry in the source file for the posts includes, at most, the following.

 * A second-level header (`##`) with the time and date when I expect the toot to appear.
 * A content warning, as a Liquid tag that I call `cw`.
 * A header image, as a Liquid tag that I call `embed`.
 * The optional article link, including the headline, URL, and news source, as a Markdown link.
 * The quote that gives the general idea.
 * A citation for the quote, as a liquid tag that I call `cite`.
 * The hashtags that I connected to the article.
 * Anything that I have to say.

Some of those have blank lines following them.  Not all entries have every line.  In fact, I don't think that *any* entry has every line.  For the most extreme, the "quote of the day"---for lack of a better name to pin on them---generally get by with only the header, the quote itself, the citation, and the hashtag.  I could add a content warning to certain quotes, but I have yet to find one where the quote might reasonably bother someone; someone talking about bigotry doesn't count.  By contrast, the articles don't have any citation.  It shouldn't take much work to take those lines, remove the Markdown/Liquid overhead, turn them into a command-line for the Mastodon scheduler script, and reset on the next heading.

I may need some trickery to avoid the "bonus" articles, but I'll have to see how that goes.

Oh, and I want to clean up the scheduler, too.  I see some places where I can improve that code without much work.

In addition, now that my **Morning Dashboard** has three graphs in it, maybe I should ditch the cutesy HTML-and-CSS bars and replace them with something like [D3.js](https://d3js.org/)?  I like D3 a lot, and it would enable me to add axes and trend-lines to the graphs.  But I'd also need to either maintain the library with the project, or rely on downloading it from a CDN, and neither of those sounds appealing.

* * *

**Credits**:  The header image is [European Day of the Righteous' logo](https://commons.wikimedia.org/wiki/File:European_Day_of_the_Righteous%27_logo.png) by [Ruggibrante](https://commons.wikimedia.org/wiki/User:Ruggibrante), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
