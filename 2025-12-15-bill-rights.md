---
layout: post
title: Developer Diary, Bill of Rights Day
date: 2025-12-15 07:27:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, salavi]
summary: Progress on assorted projects
thumbnail: /blog/assets/Bill-of-Rights-Pg1of1-AC.png
description: This week's projects include the blog's code and SaLaVI.
spell: salavi Notoboto SaLaVI
proofed: true
---

* Ignore for ToC
{:toc}

In the United States, for the 150th anniversary (1941) of its signing, President Franklin Delano Roosevelt declared today [Bill of Rights](https://en.wikipedia.org/wiki/United_States_Bill_of_Rights) day.  The first batch of amendments to our Constitution, as many of you already well know, represent something of a mixed bag.  On one hand, they codify the idea that everybody in United States territory has the right to a fair trial that can't force them to incriminate themselves (the sixth and fifth), whereas it also has the occasional wedge (the second) slowly used by conservatives over the past century to make people feel less safe by interpreting it increasingly broadly.  On the whole, though, having an explicit list of fundamental laws has probably done us more good than harm, at least until we stopped teaching it to children...

![Most of the first page of the original twelve proposed amendments](/blog/assets/Bill-of-Rights-Pg1of1-AC.png "We still don't have legitimate apportionment, amazingly...")

If you'd like something more global, the Esperanto-forward folks celebrate [Zamenhof Day](https://en.wikipedia.org/wiki/Zamenhof_Day), this year celebrating the 166<sup>th</sup> birthday of the language's creator.  Arguably, it also celebrates the "prototype" of Esperanto, which he presented to his friends at his nineteenth birthday party.

And on to the week's projects.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

As mentioned last time, the [post calendar](/blog/calendar) needed some work to clean up the days between the last post of one month and the first post of the next.  Because I relied on the list of publication dates and used some trickery to fill in the gaps, it never got anything important wrong, but didn't fill in those edge cases correctly.  Now it does.

In addition, the title text/tool tip for the month-headings now includes the year, to make it more difficult to get lost wandering around the calendar, and the full title similarly goes in the tool tip for the links to each post, even if it removes part of the title to make the posts more distinct, such as "Developer Diary" in this post's title.

## SaLaVI

{% codeberg jcolag/salavi %}

The game now has almost all its parts, including an *About* dialog and an *Options* dialog to set the board size.  It looks like it has a couple of bugs, which I'll talk about next.

## Next

This week, I'll need to fix two problems with the SaLaVI dialog boxes.  First, the *Options* dialog box refreshes the board, even if you don't change the size, which I could have sworn has code to specifically prevent that.  When it does reset, it also doesn't yet know how to remove the snakes and ladders.  Second, the *Statistics* dialog box currently won't open, because it doesn't have a function to implement populating the list...which makes sense, since the game also doesn't yet store information such as wins.

After that, I have begun building the semantic search index for my notes.  I won't share the index itself, since that won't do you any good without my notes, but I'll share the scripts that I wrote to build and eventually[^i8Bn5B] maintain them.

[^i8Bn5B]:  My current notes---the material that I created [Notoboto](https://codeberg.org/jcolag/Notoboto) to work with---span about seven hundred files with more than eighty thousand lines between them.  I don't bother to index short or empty lines, which should trim this by about half, but this also leaves me waiting for forty thousand requests to the low-end embedding model.  My setup seems to handle slightly less than two requests per minute, meaning that ignoring outages and machines sleeping, this initial indexing can't take less than two weeks and could take as much as twice that, and can't usefully run "nightly maintenance" updates until then.

* * *

**Credits**:  The header image is the [The Bill of Rights](https://commons.wikimedia.org/wiki/File:Bill_of_Rights_Pg1of1_AC.jpg) by the United States Congress, in the public domain as the work of the United States government.
