---
layout: post
title: Developer Journal, Indigenous Peoples Day
date: 2020-08-10 07:07:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Guarani_Family.png
---

* Ignore for ToC
{:toc}

Yesterday was the [International Day of the World's Indigenous Peoples](https://en.wikipedia.org/wiki/International_Day_of_the_World%27s_Indigenous_Peoples), which has the virtue of being extremely precise in what it wants to be about and isn't trying to sell something.

![People indigenous to Paraguay or Brazil](/blog/assets/Guarani_Family.png "People indigenous to Paraguay or Brazil")

Anyway, this week was relatively light work, overall, because I had other responsibilities to take care of.

## Entropy Arbitrage

The [Ham Newsletter](https://github.com/jcolag/ham-newsletter) code should now be stable enough to work for people...assuming that those people use the same services I do, at least, and unless there are bugs.  If you have all the credentials set up, you should get a newsletter with some header content, a list of blog posts, saved articles from the RSS feed, and recent browser bookmarks.  Well, you'll get that *usually*.  I don't have any error checking, so some visual inspection is warranted before sending, since sometimes the services just silently reject a request; which you'll notice I didn't bother to do for my first newsletter.  Oops...

## Non-Projects

I added some additional sample code to my [Small Things](https://github.com/jcolag/SmallThings) repository.  It's mostly for proof-of-concept/test code that eventually gets wrapped into another project, rarely useful except as a historical record.

In this batch, it includes some hacky code to simulate color-blindness on colors, written a while ago when putting together my [post on color]({% post_url 2020-03-11-colors %}), a failed attempt to determine where the Sun is in the sky, and a non-melodic mess to make sure I understood how [Alda](https://alda.io/) works.

And the rest of the week mostly went to checking out and merging those little dependency/library updates for different projects.

## Next

I may continue on with the library updates to clear out that queue of annoyance.  I also want to set up a pull request for [**Manuel, the Magnificent Mechanical Man**]({% post_url 2020-07-11-manuel %}), since I reflexively fixed some typos as I read it for the Free Culture Book Club.

With any time remaining (which may not be much), it's probably worth going back to [**Uxuyu**](https://github.com/jcolag/Uxuyu).  In addition to the issues I've mentioned in the past that I should probably nail down, there seems to be a rough standard emerging for storing avatars that might not be *too* painful to adapt.

* * *

**Credits**:  The header image is [Guarani Family](https://commons.wikimedia.org/wiki/File:Guarani_Family.JPG) by [Robertobra](https://commons.wikimedia.org/wiki/User:Robertobra), released under the terms of the [Creative Commons Attribution-Share Alike 3.0 Unported license](https://creativecommons.org/licenses/by-sa/3.0/deed.en).
