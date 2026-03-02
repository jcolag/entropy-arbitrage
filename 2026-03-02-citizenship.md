---
layout: post
title: Developer Diary, American Citizenship Day
date: 2026-03-02 07:02:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, ham-newsletter, library-update, oopsie, tool-trunk]
summary: Progress on assorted projects
thumbnail: /blog/assets/5346718319_7d07dd2acc_o.png
description: This week's projects include a server fiasco, the blog's code, the Ham newsletter generator, my Mastodon tool trunk, some library updates, and a suspicious teaser.
spell: oopsie Shafroth Elihu Vedder Revoy Deeplinks citationneeded Roku
proofed: true
---

* Ignore for ToC
{:toc}

Today, we in the United States---those of us trying to stand on the right side of history, at least---celebrate [American Citizenship Day](https://www.pr51st.com/happy-american-citizenship-day/), marking the 1917 passage of the [Jones-Shafroth Act](https://en.wikipedia.org/wiki/Jones%E2%80%93Shafroth_Act), extending birthright citizenship to everyone born in Puerto Rico after 1899 April 11.  The law certainly has its problems that continue to make life more difficult in Puerto Rico, and certainly doesn't go nearly far enough, but at least for a time, the United States realized that people born in territories controlled by the United States should have some say in how the United States functions.

![San Juan, Puerto Rico, from an inbound plane](/blog/assets/5346718319_7d07dd2acc_o.png "I don't think that I have ever seen a city drop that precipitously to suburban-style residential areas...")

And on to the week's projects.

## Administrative Nonsense

This doesn't really show up anywhere, but I should note that the website went down for a couple of hours late Thursday evening.

Checking on something in the post for [the first half of *Emissary*]({% post_url 2026-02-26-emissary-1 %}), I saw the server running incredibly slow, and missing some requests.  I couldn't find any heavy web access, so I started checking out what the system had running.

The process list had a bunch of [Mono](https://www.mono-project.com/) and [Gitea](https://about.gitea.com/) processes running, which seemed...odd.

I started setting up Gitea years ago for repositories that I maintained on the VPS, but abandoned the idea when I realized that I only really had private repositories there, and didn't want to waste limited drive space by moving more projects there.  And somehow, I decided to remove it "later," and then forgot about it.

For the Mono processes, to my best recollection, I only ever installed Mono on the system to showcase [Base Dice](https://codeberg.org/jcolag/basedice) to a few people, probably more than a decade ago.  I also don't know that I even have the Base Dice application anywhere on the server anymore.  But as with Gitea, I left the framework in place and connected to the web server.

Maybe some AI or some other scraper tripped a URL or two that triggered the problems, but since I probably don't need either system, I could drop them and at least solve *that* problem, right?  I shut Gitea down completely and nuked Mono, then restarted the web server, and...nothing.  I had replaced the inconsistent delivery of pages with the web server not starting.

To save you a blow-by-blow of the hour-plus of debugging while desperately wanting to go to sleep, buried behind completely nonsensical errors for non-running modules that definitely worked, I left the Mono module in place, and *that* crashed without any Mono thing to run.  Removing that got me back running in time to collapse in bed...

## Entropy Arbitrage, the Code

{% codeberg jcolag/entropy-arbitrage-code %}

Some of you might have already seen this coming, particularly if you pay attention to the [social media roundup](/blog/tag/link-dump) posts.  I decided that, after six years, the time had come for at least some small changes, so you'll see that the script that creates the next week's post-skeleton now picks a different header image, specifically Elihu Vedder's *Abundance of The Days of the Week* (1893).

![The painting in question, with eleven inset scenes, the corners and central seven depicting the gods that give their names to the days of the week](/blog/assets/Elihu-Vedder-Abundance-Days-Week-1926.png "The spell-checker loathes seeing the artist's name credited every week...")

It has a similar feel as the image that I have traditionally used, but feels more dynamic and the blue inset backgrounds break up the image.  And along with that has come different snarky title-text for the image to randomly choose each week.

In addition, the script also tags the quote post for the month's relevant [history or heritage month]({% post_url 2022-07-03-reading %}) as a reminder when I pick those quotes.

And since the full Markdown link now comes from a script, I no longer include the stub to fill in, calculating that typing `[]()` will take less time on the rare occasions that I fill in a link from outside my RSS feed than it does to delete five or more of them per week...

Then, over in the first-pass proofreading script, it now warns me about time zone mismatches.

For me, this comes up most often for posts where I create the first draft by copying another post for the structure.  These developer diary posts, for example, generally copy and empty out the previous month's before I go hunt for the holidays to use, because I can't think of a reasonable way to name a post after a holiday without spending time looking through the holidays that land on that day.  Similarly, the [*Star Trek* season summary posts](/blog/tag/summary).  Some Sunday posts also grab the heading from a previous week, especially when the posts have some relationship to each other.  In all these cases (and probably a few others), my clocks will sometimes shift into or out of Daylight Saving Time, meaning that running the publication script will either send out a post marked an hour too early, or it won't go out at all because the time-as-parsed won't come for another hour.

## Ham Newsletter

{% codeberg jcolag/ham-newsletter %}

Because I have moved my newsletter drafts into a more sensible structure than "all files in the same place," I changed the top-level script to pick out the file in the folder for that year.

## Mastodon Tool Trunk

{% codeberg jcolag/tool-trunk %}

On the flip-side of updating the social media roundup script, the Friday posts (and the Mastodon posts that match them) have another small change:  When I share an article from somebody or some organization that has an account somewhere on the Fediverse, the articles now mention that account for readers who might want to follow them.

Right now, when generating the Markdown links, *that* script tries to match the domain name to a Fediverse account, which I then copy into place after deciding which of the prior week's links to share.  But by tracking them through the parse-and-schedule script, that ensures that they'll show up properly in the Mastodon toots, as well as give me an opportunity (later on) to maybe rewrite the handle in the blog post into a link.

Actually, in case somebody has a use for the current preliminary list, I might as well show it here.

|Domain|Handle|Site Name|
|------|------|---------|
|404media.co|`@404mediaco@mastodon.social`|404 Media|
|anildash.com|`@anildash@me.dm`|Anil Dash|
|bellingcat.com|`@Bellingcat@mstdn.social`|Bellingcat|
|theconversation.com|`@TheConversationUS@newsie.social`|The Conversation|
|pluralistic.net|`@pluralistic@mamot.fr`|Cory Doctorow|
|davidrevoy.com|`@davidrevoy@framapiaf.org`|David Revoy|
|eff.org|`@eff@mastodon.social`|EFF Deeplinks|
|emptywheel.net|`@emptywheel@mastodon.social`|Empty Wheel|
|globalvoices.org|`@globalvoices@mstdn.social`|Global Voices|
|knowablemagazine.org|`@KnowableMag@mstdn.science`|Knowable Magazine|
|citationneeded.news|`@molly0xfff@hachyderm.io`|Molly White|
|propublica.org|`@ProPublica@newsie.social`|ProPublica|
|therealnews.com|`@therealnews@mastodon.social`|The Real News Network|
|techdirt.com|`@mmasnick@mastodon.social`|Techdirt|
|diff.wikimedia.org|`@wikimediafoundation@wikimedia.social`|Wikimedia|

This only covers sources that I have used regularly (and where I could find their account), so if you need something similar, you'd want to check for what you need.

## Library Updates

I needed to bump library versions for my [Morning Dashboard](https://codeberg.org/jcolag/dash) (probably due for a complete overhaul or replacement) and [Roku Wake](https://codeberg.org/jcolag/Roku-Wake).

## Next

I have a couple of new project ideas that I *may* start working on, though I may also continue pushing through the library updates or go back to an old project.  In other words, guess away...

Actually, I have one project that I worked on during the week that I can't talk about yet, because somebody else will release it first.  When that happens, I'll announce it and make the source files available.

* * *

**Credits**:  The header image is [Flying into San Juan](https://www.flickr.com/photos/60202180@N00/5346718319) by [Breezy Baldwin](https://www.flickr.com/photos/breezy421/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license.
