---
layout: post
title: Developer Diary, Art Nouveau Day
date: 2024-06-10 07:44:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/80130778-panoramio.png
offset: -15%
teaser: This week's projects include social media updates, my morning dashboard, the CPREP character background generator, The Light's Edge, and a straggling library update.
spell: Nouveau Fýlakas Onomáton CPREP Gran Vitral del Ciudad Unported

---

Today marks [World Art Nouveau Day](https://en.wikipedia.org/wiki/World_Art_Nouveau_Day)---sometimes referred to as "WAND," because we almost never get a long name with a pronounceable acronym---celebrating...well, the [Art Nouveau](https://en.wikipedia.org/wiki/Art_Nouveau) movement, often trying to convey a sense of dynamism and movement.  When you see works, from line art up to architecture, with little asymmetries, organic lines, and especially lines that seem to indicate motion, then you probably have something relevant.

![Gran Vitral Tiffany del Hotel Ciudad de Mexico](/blog/assets/80130778-panoramio.png "I spent far too long deciding which appropriately licensed picture I wanted to use to represent the Art Nouveau movement, suggesting that maybe I like the style a bit...")

And on we go to the projects.

## Social Media

I don't have a real update quite *yet*, but I've reviewed the contents of the data export from Post.News, and have at least a prototype for exporting it to HTML in a reasonable way.  I'll post the code and the archive soon.

## Morning Dashboard

{% github jcolag/dash %}

I don't have much of an update, here, especially considering that someone changed their data format for weather, but I *have* started adding a quick overview of the day's expected television, courtesy of [TV Maze](https://www.tvmaze.com/)'s API.  It either doesn't cover everything or I haven't figured out how to extract all the data from its output, yet, but it does a credible enough job warning me to make time for certain shows.

Because I don't watch much, but would like to cast as wide a note as possible in case something interesting sneaks through, I keep the interface minimal.  For each day, it generates a bulleted list with the name and network/service, which---through the magic of the `details`/`summary` elements---expand to show the episode description.

## CPREP

{% github jcolag/background-generator %}

While I haven't *done* anything with it, yet---I do hope to get back to this project, one day, because I still see some potential in it---I have added [faces.js](https://zengm.com/facesjs/) to replace the almost worthless code that I wrote to try to draw faces.

I'd love to fix my own face code, and invite anybody with an interest to do so, but this library has a bank of head, eye, nose, and mouth shapes, which honestly looks a lot more like what I wanted in the first place.  My original vision for that code hoped that I would find a public domain [facial composite](https://en.wikipedia.org/wiki/Facial_composite) system, but since the field of modular face systems started in 1959, that seems unlikely.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Primarily, I finally added a little "insert" to explain the *What Works...Less Well?* sections of the [Free Culture Book Club](/blog/tag/bookclub) posts.  I haven't added them to old posts, yet, but new posts now include a collapsed paragraph---using the same `details`/`summary` gimmick mentioned above---explaining that I level my critiques to highlight that Free Culture enables people to fix those issues.  And OK, sure, sometimes I rant about my frustrations with particularly irksome works, but *mostly* the empowering thing.

A couple of scripts needed cleaning up, improving the reliability of the syntax, here and there.  I also updated my open-upcoming-posts script to open everything in the `_drafts` folder, so that I don't forget about the drafted posts.

## The Light's Edge

{% codeberg jcolag/thelightsedge %}

Once again, I haven't pushed the changes out to the server, but the background pages have gotten some new attention, too.  The tagline---*The sci-fi saga that needs you to join the fight for a free galaxy*---now has links to explain the relevant terms, following the lead of Wikipedia's tagline.  The main page also now includes the Free Culture works logo and my "JC" logo.

The project now has a code of conduct, modeled on the [Contributor Covenant](https://www.contributor-covenant.org/), as well as broader contribution guidelines.  And I changed the ZIP Code to something slightly less conspicuous, but identifying a similar non-destination.

## Library Updates

I needed to bump library versions for [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton).

## Next

I expect that Post.News will take up a lot of the week, both publishing my export-to-archive script, and publishing my resulting archive.  If anybody has an export of their own, I'd love to know how many of my assumptions pan out for other people.

* * *

**Credits**:  The header image is [Gran Vitral Tiffany del Hotel Ciudad de Mexico](https://web.archive.org/web/20161024202755/http://www.panoramio.com/photo/80130778) by [Octavio Alonso Maya Castro](https://web.archive.org/web/20161024202757/http://www.panoramio.com/user/5358119?with_photo_id=80130778), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
