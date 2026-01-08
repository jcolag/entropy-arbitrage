---
layout: post
title: Developer Diary, US Continental Army
date: 2025-11-03 07:18:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, codeberg-move, library-updates, notoboto]
summary: Progress on assorted projects
thumbnail: /blog/assets/Seal-US-Board-of-War-and-Ordnance.png
description: This week's projects include the blog's code, the Concept-Net Random Walk, Notoboto, a multiplication game, an alternate Type Time, my class management scripts, uManage's reports, a color namer, a keyword search, my Twitter archive, and some library updates.
spell: Notoboto uManage EIID GJHF GBBDD nhTaQr OKLCH Scuttlers Zoea
proofed: true
---

* Ignore for ToC
{:toc}

On this day in 1783, the United States disbanded the [Continental Army](https://en.wikipedia.org/wiki/Continental_Army), the military force that fought our revolution.  I can't imagine why I'd have [dismantling a militarized government agency operating on domestic soil](https://en.wikipedia.org/wiki/Abolish_ICE) on the mind, these days, but hey, the precedent exists.

![The seal of the United States Board of War and Ordinance](/blog/assets/Seal-US-Board-of-War-and-Ordnance.png "Please tell me that they made the cannons wear dresses and hats...")

With that, on to the week's projects.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Looking at the results over the past week, I noticed that the "recipe cards" needed some space after them to look consistent with the rest of the layout, so I added half a line-height.

## Concept Random Walk

{% codeberg jcolag/concept-random-walk %}

Following up on last week's post, I quickly tested this project that meanders around the Concept Net semantic database and adjusted the base URL to their current setup.  It still seems off, so they may have changed the API, but at least the code no longer screams about not finding the end-point.

## Notoboto

{% codeberg jcolag/Notoboto %}

We have two small updates, here.

First, inexplicably, the regular expression to detect URLs didn't recognize hyphens, so now they do.

Then, it occurred to me that it has no way of marking useless notes as deleted.  While it doesn't have the functionality wired in, then, I have added the deletion (Material Design's trash can) icon for use soon.

## Multiply

{% codeberg jcolag/multiply %}

A long while ago, I threw together one of those little multiplication puzzles, where the digits get replaced by letters, and the "player" needs to work out the correspondence.  That may need an example.

```
  BFG
x  DA
-----
 EIID
GJHF 
-----
GBBDD
```

From this, we know that `G` times `A` is some number of tens plus `D`, and so forth.

It doesn't have the best interface, even for a terminal application, because I didn't need anything more than a quick diversion, but it does work, and it now resides on Codeberg.

## Type Time for .NET

{% codeberg jcolag/type-time-net %}

Since I carried over [Type Time](https://codeberg.org/jcolag/typetime) itself, I figured that I should move what I once considered the project's successor over to Codeberg, too.

## Class Management

{% codeberg jcolag/class-management %}

I don't think that this will serve a purpose for anybody else, but in the later years of my teaching, after moving my lecture notes from word processor to word processor and sometimes back, I decided to future-proof the setup by moving everything to Markdown.  This repository has the scripts that I used to do the conversion to Markdown, the assorted scripts that package up a week's notes to my outline, an outline to pass out for students, any supplemental material, and so forth, as a single PDF that I could send to the school's printer before driving over.

Despite the lack of direct application, you might find *something* useful in there, since I used a bunch of tools to make that work.  And you can see what the input files look like in the `examples` folder, all neatly on Codeberg.

## uManage Reports

{% codeberg jcolag/uManage-reports %}

Since I moved [uManage](https://codeberg.org/jcolag/uManage) over to Codeberg, it seemed appropriate to move its (preliminary and unfinished) partner repository over, as well.  It has an [R](https://www.r-project.org/) script to start summarizing the data.

## Color Namer

{% codeberg jcolag/color-namer %}

I forget why I put this together, and looking at the code, I do *not* endorse the current method of finding the nearest color[^nhTaQr], but at some point, I decided that I needed a tool that takes an input color and finds the closest named color from [Wikipedia's list](https://en.wikipedia.org/wiki/List_of_colors_%28compact%29).

[^nhTaQr]:  I should have converted the input color to a cylindrical color space such as HSV, or now something more like OKLCH.

And now it sits on Codeberg.

## Keywords

{% codeberg jcolag/keywords %}

Another one-off project that I probably created to try out a hypothesis, here.  It works to flag hoax content.  In short, it tries to strip input down to some minimal set of statistically improbable words that characterize the contents, then searches a typical fact-checking site to see if they have any information on the topic.

I don't expect to return to it, though I suppose something like it still has value.  If you want to mess with it, though, or snag the list of two-thousand words that probably don't matter, you can find it on Codeberg along with the rest.

## Twitter

{% codeberg jcolag/twitter %}

One last project moved to Codeberg, I decided to copy over my archive of [posts from Twitter](https://jcolag.codeberg.page/twitter/).  You can find the same [archive on GitHub](https://jcolag.github.io/twitter/), but Microsoft taking firmer control of GitHub makes me wonder how long they'll keep maintaining GitHub Pages in the same form that they do now.  I expect to do the same with my other social media archives, and will update my [main page](/) to link there.

## Library Updates

I needed to update library versions for [Little Scuttlers](https://github.com/jcolag/LittleScuttlers) and [Zoea](https://github.com/jcolag/zoea).

## Next

Expect more of the same, while I hope that I don't over-burden Codeberg with nonsense like the Twitter archive...

* * *

**Credits**:  The header image is the [Seal of the Board of War and Ordnance](https://etc.usf.edu/clipart/57200/57231/57231_war_ordnance.htm) by the agency in the title, in the domain as a work of the United States government.
