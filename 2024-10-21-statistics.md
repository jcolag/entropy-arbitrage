---
layout: post
title: Developer Diary, World Statistics Day, Belated
date: 2024-10-21 07:13:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Standard-Normal-Distribution.png
offset: -30%
description: This week's projects include the blog's code, my Cohost archive, and (documentation for) both toys and episodes for The Light's Edge.
proofed: true
---

* Ignore for ToC
{:toc}

Yesterday marked [World Statistics Day](https://en.wikipedia.org/wiki/World_Statistics_Day), though we apparently only actually celebrate it every five years and this one doesn't count.  Maybe this looks more like a year early than a day late, then.  I don't know.  It celebrates statistics, though, and that seems interesting...

![A graph of the normal distribution](/blog/assets/Standard-Normal-Distribution.png "Perfectly normal, nothing to see here...")

Anyway, on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

After many, many trials trying to work with the Diaspora API, and after formalizing my process for posting blog announcements to various services, I have finally given up and commented out the attempt to automatically post the announcements to [my Diaspora account](https://nota.404.mn/people/e4313920967a0136074b076893c08a76).  For whatever reason, presumably a deliberate decision made by my server, I can't get a request to authenticate.  And since I now have a system to publish approximately the same thing to every platform, it didn't seem worth having the reminder in my publication script to print something similar.

## Cohost Archive

{% github jcolag/cohost %}

I have now finally published [my Cohost archive](https://jcolag.github.io/cohost/), for the most part.  At some point, I'll want to make some small corrections, and will replace some media items---which I haven't uploaded---that don't have public licenses with links to them.  But as of yesterday morning, you can now read all my posts from Cohost.  I put it all on one page, because I recycled many post titles, and some posts had no titles, making an index unusable.

Even though I only used Cohost for about a year and ten months, the archive interests *me* to see the evolution of my blog announcements.  It took me a couple of weeks to realize that I could---and should---use that space to talk about the post (which became the post teasers/descriptions), another few weeks to realize that the [Free Culture Book Club](/blog/tag/book-club) posts could benefit from showing an image related to the work, and then around a year and a half until I realized that every blog announcement should have the header image attached, except for the [Social Media Roundup](/blog/tag/link-dump) posts that always use the same image.

*You* might want to read through, if any of the following interest you.

- The posts that I made for that specific audience, which I haven't cataloged, yet.  Some of these may eventually get "reconditioned" into posts here.
- The extra comments that I made about posts, especially for the [Real Life in Star Trek](/blog/tag/star-trek) posts.
- The subset of the previous items that inspired the creation of the post-teasers.

I should also note that the time-stamps link to the read-only version of the post.  Oh, and the repository complies with [REUSE](https://reuse.software/), so if you want to use anything from there, you have the terms of use for especially the media files.

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

I updated the documentation to include the skateboard model added last week.  I don't know how that slipped past me, though it happens often enough that it doesn't surprise me...

While there, I also cleaned up some comments about the other models, to improve their clarity.

## The Light's Edge (Episodes)

{% codeberg jcolag/lights-edge-episodes %}

I still haven't pushed any actual episodes, there, but I have extended and overhauled parts of the README documentation, now including places to contribute and guidelines for it, broken into sections of their own.

Watch the space, because the story *should* start soon, with my (mild) apologies for it taking so long...

## Next

I have some last additions or changes for my Cohost archive---the non-Free media need replacements, and I want to indicate when I wrote a post in response to someone else---and **The Light's Edge** documentation, plus some changes for the blog.  I also have the code that I used to create the Cohost archive.  And I *may* have a surprise or two after that, time permitting...and if I actually have something.

* * *

**Credits**:  The header image is [Standard Normal Distribution](https://commons.wikimedia.org/wiki/File:Standard_Normal_Distribution.png) by [D Wells](https://commons.wikimedia.org/wiki/User:D_Wells), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
