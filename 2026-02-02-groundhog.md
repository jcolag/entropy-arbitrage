---
layout: post
title: Developer Diary, Groundhog Day
date: 2026-02-02 07:59:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, open-letter]
summary: Progress on assorted projects
thumbnail: /blog/assets/mr-ground-hog.png
description: This week's projects include continuing to label blog posts.
spell: H_NJVw Twitterbot
proofed: true
---

* Ignore for ToC
{:toc}

Probably because we have holiday-ed ourselves out for the solstice and know that we have another batch of holidays incoming as we approach the equinox, we mostly only have [Groundhog Day](https://en.wikipedia.org/wiki/Groundhog_Day) to work with, though Alaskans have adapted(?) the idea as [Marmot Day](https://en.wikipedia.org/wiki/Marmot_Day).  Does anybody actually still remember the quaint days when the public could act like they didn't have a more pressing issue than when the winter weather would end...?

![A postcard from the 1930s introducing us to Mr. Ground Hog, the original weather prophet](/blog/assets/mr-ground-hog.png "Who has got two thumbs and you, babe...?")

And on to the week's projects, before we start thinking about how a one-off comedy film almost completely replaced what comes to mind when people talk about the day.

## Entropy Arbitrage, the Posts

{% codeberg jcolag/entropy-arbitrage-posts %}

It certainly took long enough, but the [developer diary](/blog/tag/dev-journal) posts should have all the labels[^H_NJVw] that might prove useful to a reader, finally reaching the start of 2020.  Of particular interest to me, once I stopped working exclusively on [Bicker](/blog/tag/bicker) as my "official blogging project," I actually *tried* to tag posts with the projects (and sometimes technologies) discussed.  After a couple of weeks, though, it looks like I copied-and-pasted the tags without checking to see what I had listed.

[^H_NJVw]:  If anybody happens to spot something that I have overlooked, get in touch.  It doesn't seem worth listing every project where I bumped a library version, for example, but if somebody does anticipate wanting to read that way, I could consider it.

Anyway, now if you need to track down posts where I dropped in a snippet of [JavaScript](/blog/tag/javascript) or worked on [Slack Backup](/blog/tag/slack-backup) or whatnot, or *both* with the [multi-tag search](/blog/tag-search), that should all work out right.

With that done, I have started on the next-most-useful batch of posts, the [Free Culture Book Club](/blog/tag/book-club) series.  They *should* move significantly faster than two months at a time, because I already have the media type and license near the top of the post, so I shouldn't need to skim everything to figure out what matters.

## OSI Election Results Petition

{% codeberg OSI-Concerns/election-results-2025 %}

For a while, now, the [Open Source Initiative](https://opensource.org) has acted in shady ways.  Granted, they exist purely to push the idea Free Software and copyleft need to fall away for code that big companies can exploit without compensating developers, so maybe shadiness shouldn't surprise us.  But last year, this shadiness went significantly further, when they adjusted their election rules *at the end of the election*, disqualifying (mostly pro-copyleft, probably coincidentally...) several candidates.  On top of that, they didn't publish their election results.

That seems...I don't know, *bad*, so I [signed the petition](https://codeberg.org/OSI-Concerns/election-results-2025/pulls/128).

## Library Updates

I needed to bump library versions for my now-out-of-date [Library Twitterbot](https://github.com/jcolag/library-twtterbot).  Well, "need" probably exaggerates significantly, in this case, given that neither Twitter nor its public API really exists anymore.  And I stopped running the bot, because nobody used it[^Lvtr7n].

[^Lvtr7n]:  The bot maintained a list of articles debunking various right-wing talking points, and would reply to requests based on keywords in the thread.  While I liked the idea, envisioning that it could provide readers with more reasonable views without engaging with the creeps, but it took so much presence of mind that even I didn't bother to use it...

## Next

For this week, I want to make progress on labeling the Free Culture Book Club posts.

* * *

**Credits**:  The header image is [T-26. Mr. Ground Hog, the original weather prophet](https://www.flickr.com/photos/boston_public_library/5755491865/) by the [Boston Public Library](https://www.flickr.com/photos/boston_public_library/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license...though probably in the public domain with no copyright statement.
