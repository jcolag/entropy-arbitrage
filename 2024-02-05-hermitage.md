---
layout: post
title: Developer Diary, Hermitage Museum
date: 2024-02-05 07:07:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/NewHermitage.png
offset: -15%
teaser: This week's projects include Notoboto, the blog's code, my Morning Dashboard, and the Ham Newsletter generator.
spell: Notoboto Unported Pandoc Sdobnikov
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the 260<sup>th</sup> anniversary of the opening of the [Hermitage Museum](https://en.wikipedia.org/wiki/Hermitage_Museum) in Saint Petersburg.  While Russia has---and, honestly, has always had---its problems on the world stage, they have managed to maintain one of the largest and oldest museums in the world...which also carries the dubious distinction of carrying a lot of art and history that we would now call *stolen*, sadly.

![The New Hermitage from the street entrance](/blog/assets/NewHermitage.png "I can fault the Russians for many things in their history, but careful attention to subtle ornamentation does not appear on that list...")

Do my projects look more like museum pieces than actual work?  Maybe...

## Notoboto

{% github jcolag/Notoboto %}

Searches now default to case-insensitive, since that seems like the more likely scenario for general notes.  This has bothered me more than I'd like to admit, *especially* since I still don't have a user interface to modify the search types, yet.

More importantly, I added the highlighting code to the same timer-expiration handler that saves changes to the notes.  I have one "accidental stress test" of a note, a list of book recommendations that caught my interest, currently hundreds of titles, each bolded, and grouped with about two hundred headings.  And when updating it recently, I noticed that trying to update the formatting while I typed took a significant toll on my system.  By moving the activity to during pauses in typing instead of every key-press, it now moves much faster.  If only I could remember why I didn't think to write it that way in the first place...

I also fixed some ugly mistakes in the overview.  And I snuck in some stub code that will eventually become the "replace" part of search-and-replace.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Recently, I had some trouble publishing a blog post.  I forget which one, but I ran my rebuild-and-republish script multiple times, only to get hit with an opaque error that forced me to quit.  Debugging things, I traced the problem to my Codeberg plugin.  Or, rather, the problem stemmed from failing to access [Codeberg](https://codeberg.org/) itself; I don't know if they went down or if some transient connection flaked out, but I stubbed out the plugin to get the new post out the door.  And when I had to send out the *next* post, Codeberg had come back, so I ignored the problem.

However, this happened again, and I realized that I would need something resembling a permanent solution.  Therefore, the Codeberg plugin now emits "Codeberg unavailable at page creation" for the repository preview.  I can always try to clean that up later, and I'll eventually want to add a hyperlink to the repository, even if I can't get the full information.

For a tinier change, I updated the name for the mouse {% emoji mouse face %} emoji for clarity.

## Morning Dashboard

{% github jcolag/dash %}

I had some recent problems with the National Weather Service API not returning complete data from the call, which makes the API result something less than entirely useful.  While I don't expect this to cause problems on a regular basis, it does jam up my morning, as I need to figure out why the dashboard didn't show up, patch the problem, then re-run the generator.

In this case, I took the relatively expedient route of checking the weather data before using it.  If the API didn't provide anything, then it substitutes a blank weather alert.

## Ham Newsletter

{% github jcolag/ham-newsletter %}

Earlier this week, for reasons unrelated to the [**Entropy Arbitrage** Newsletter](https://www.buymeacoffee.com/jcolag), I upgraded to the latest version of [Pandoc](https://pandoc.org/).  But when the January newsletter---which you can still sign up for, if you want to read it in tomorrow morning's e-mail---went out over the weekend, that new version of Pandoc informed me of the following.

 > `[WARNING] Deprecated: --self-contained. Use --embed-resources --standalone`

The creation script did, indeed, use `--self-contained`, so I corrected it to use the more modern syntax.  I apologize if anybody uses this with an old version of Pandoc, because that change will probably cause problems.

## Next

I got a bit distracted from my big project, last week, so I'd like to get back to finishing off the search-and-replace bits of **Notoboto**.

* * *

**Credits**:  The header image is [New Hermitage](https://commons.wikimedia.org/wiki/File:NewHermitage.jpg) by [A. Sdobnikov](https://commons.wikimedia.org/wiki/User:%D0%A1%D0%B4%D0%BE%D0%B1%D0%BD%D0%B8%D0%BA%D0%BE%D0%B2_%D0%90.), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
