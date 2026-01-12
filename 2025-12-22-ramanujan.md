---
layout: post
title: Developer Diary, Srinivasa Ramanujan
date: 2025-12-22 06:59:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, graphite, mini-server, salavi]
summary: Progress on assorted projects
thumbnail: /blog/assets/Srinivasa-Ramanujan.png
description: This week's projects include SaLaVI and the blog.
spell: SaLaVI salavi
proofed: true
---

* Ignore for ToC
{:toc}

Lacking a holiday for today, we can celebrate the 138<sup>th</sup> birthday of [Srinivasa Ramanujan](https://en.wikipedia.org/wiki/Srinivasa_Ramanujan), the mathematician with no formal training who advanced the state of the art in continued fractions, Bernoulli numbers, and a few more fields.

![Ramanujan's 1913 passport photograph](/blog/assets/Srinivasa-Ramanujan.png "Action movie tagline:  He will math you up")

And on to the week's projects.

## Mini-Server, Part 17

For anybody wondering what happened with the "refreshed" server that I mentioned a couple of weeks ago, it didn't go well.  Debian installed fine, and everything *looked* normal for about a week while I let it run in the corner.  But things didn't go well, maybe predictably, once I decided to trust the thing.

As far as I could tell without actively monitoring anything, the machine stayed running consistently for about a week and a half, the later part of which I started slowly installing things.  I set up NGINX without any trouble, followed by Jellyfin.  I didn't *do* anything with Jellyfin, because I hope that whatever new media server that I use can import everything from the existing but under-powered server.

Before I did that---because the server running Windows *also* seemed to generally run until I tried to stream something to the television---I decided to try something more taxing.  I landed on building [Graphite](https://graphite.art/), since I would like to get that running but don't want to set up all the requirements on a Raspberry Pi.  And wouldn't you know it, any part of the installation that took a while, the system would abruptly shut down, with no way of restarting it until it spontaneously decided to turn back on.

This more or less reflects how it would work under Windows, available if I logged in through Remote Desktop or looked through my library on Jellyfin, but as soon as I played something, it'd crash after a few minutes with the same behavior.  I guess that I can't blame this one on Microsoft.

Does it overheat?  Does the memory have problems?  Loose connection?  A "don't let me do anything useful" setting in the BIOS?  Something else?  I don't know, but it shows that I can't use it until I figure that out.

## SaLaVI

{% codeberg jcolag/salavi %}

The game, which [you can play](https://jcolag.codeberg.page/salavi/), continues its polishing round.  It now counts games started, has a minimum board size of two-by-two, and tears down the board before creating a new one.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Most prominently, though, the little pull-out tray urging people to sign up for the [newsletter](https://buymeacoffee.com/jcolag) no longer has the Mailchimp form or references Mailchimp in any way.  As a reminder, with the new year, the Intuit-owned site has decided that **not** using their visual e-mail designer should cost money, and so will remove the "take this HTML and do whatever you need to do with it" approach out of the free tier.

Much as I love the newsletter and take pride in the work that I did to streamline assembling and preparing the e-mail every month, I considered the 2021 acquisition a flaw in a project that largely avoids large companies, and couldn't bring myself to subscribe to an Intuit service even if I felt like throwing that money somewhere.  I may migrate the mailing list to another, smaller service, if I can find one with a similar set of features that I care about.  But until I take the time to do that, I'll send out the unfinished December newsletter to Mailchimp subscribers one final time on New Year's Eve, then mostly forget about the account.

Anyway, all that to say that encouraging people to sign up on Mailchimp seemed like a terrible idea, if I didn't plan to send out another full newsletter from there, so I overhauled the "sales pitch."

In addition, as I look ahead to posts coming in the next weeks, it seemed worth adding annotation icons for links to [Inkscape](https://inkscape.org) and [Font Forge](https://fontforge.org/en-US/).

For behind-the-scenes improvements, I added Jekyll's "live reload" feature to the internal server, so that I don't need to guess when internal builds have finished.  And I finally committed my changes to the [Jekyll-feed](https://github.com/jekyll/jekyll-feed) plugin---based on a pull request, there---to ignore posts marked as *hidden*, so that I don't need to track down the change if I need to set everything up from scratch again at some point.

## Next

I have more cleanup for both SaLaVI and the blog, plus the scripts that I have *slowly* used to build the semantic index for my notes, but otherwise, I don't know.  Maybe I'll scale back for the holidays...but probably not.

* * *

**Credits**:  The header image is the [Add.Ms.a.94.7](https://mss-cat.trin.cam.ac.uk/manuscripts/uv/view.php?n=Add.Ms.a.94.7#?c=0&m=0&s=0&cv=6&xywh=-945%2C-274%2C5431%2C5258) by an uncredited photographer, made available under the terms of the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/deed.en) license by Trinity College.
