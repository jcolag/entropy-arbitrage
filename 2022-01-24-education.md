---
layout: post
title: Developer Journal, International Day of Education
date: 2022-01-24 07:36:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Khamla-Panyasouk-of-Big-Brother-Mouse-reads-to-children.png
update: [
  2020-04-27-april.md
]
proofed: true
---

Today is the [International Day of Education](https://en.wikipedia.org/wiki/International_Day_of_Education), adopted in only 2018, specifically celebrating the role of education in peace and sustainable development.

![Reading lessons in Laus](/blog/assets/Khamla-Panyasouk-of-Big-Brother-Mouse-reads-to-children.png "It worries me that this is the first that I'm learning about outdoor reading festivals")

Otherwise, welcome to the first [developer journal](/blog/tag/devjournal) post of the year.

## Morning Dashboard

{% github jcolag/dash %}

The dashboard now combines data from [Open Weather Map](https://openweathermap.org/) with that from the [National Weather Service](https://www.weather.gov/).  You might question this decision, of course, because it seems like a waste to make two requests for what should mostly be the same data.  The issue---at least in my experience, living where I do---is that Open Weather Map has seemed to have a lower probability of being accurate, but when it *is* accurate, it's also far more precise and thorough.  So, this uses the National Weather Service data for the "broad strokes" of the day ahead, while filling in details like precipitation amounts and the UV index from the Open Weather Map API.

In addition to that, I also cleaned up some silly issues, like pointing the wind direction arrows where the wind is *going*, rather than where it comes from---an east wind blows to the west---and not showing `null` values when data isn't relevant.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

I have spent more time with the blog plugins, this week.

The simpler story is that I have started running the plugin code against [Rubocop](https://rubocop.org/), so that I'm no longer showing fragile code that only makes sense to me.

More intricate has been continuing work to improve the GitHub plugin.  I fixed a really silly bug that was cutting apart the repository titles.  The code also---as predicted---now *caches* GitHub's OpenGraph metadata, so that rebuilding the blog doesn't require repeatedly making the same network request.

### Testing

Maybe interesting to some readers, while the actual caching code was mostly straightforward, *testing* the caching code was more of an adventure.  As far as I can tell, the state of the art of testing Jekyll plugins has been to just rebuild the blog and watch for errors.

Now, I freely admit that I'm not as diligent a tester as I should be.  I'm old enough to have always wanted automated testing systems, but spent at least a decade without them available.  However, even I can see that this is a *terrible* process, especially when rapid but minor changes are expected, especially when it's not being developed alongside changes to posts, so I tried to do better.  Waiting a minute or two just to find out that there's a bug is not only a delay, but also prevents my local server from running until I can patch the code and start over, meaning that I can't change tasks.

The plugins are written in [Ruby](https://www.ruby-lang.org/en/), after all, so it would only be reasonable that a plugin can be tested using the same processes used to test any Ruby code.  However, my first attempts didn't go well, leading me to post [a question on Stack Overflow <i class="fab fa-stack-overflow"></i>](https://stackoverflow.com/q/70779122/3438854).

That question didn't bring in any responses beyond an up-vote, so I continued investigating and tinkering, leading to answering my own question, the next morning.  So, I now have a basic test harness for my GitHub plugin.  On Wednesday, I'll turn the aforementioned question, answer, and other thoughts into a [tech tips](/blog/tag/techtip) post to walk people through the process.

## Cooking

If I remember correctly, I haven't posted anything like a recipe since an [attempt at baked oatmeal]({% post_url 2020-04-27-april %}) almost two years ago, when the blog was still new.  This week's big culinary discovery, though, was the humble "cabbage steak"...which doesn't appear to be traditional.

I won't bother with pictures---not that any have been taken---so the short version is that you start with the densest cabbage that you can get your hands on.  The tighter the leaves are, the better this will hold together during and after cooking.  "Carve" the head of cabbage into roughly inch-thick slices, first halving through the stem, each steak a disk parallel to that first slice.  I ended up with six of the disks, with two (from either side) that obviously retain their round side, coming from the outside of the head.

Lay the steaks out on a sheet tray---line with parchment paper, to minimize clean-up---brush both sides with olive oil, and add whatever spices you want.  I remember using coarse-ground pepper, garlic powder, and paprika.  Bake at 400 °F (200 C) for at least twenty-five minutes.  Flipping them and rotating the sheet tray halfway through cooking seemed like a good idea, but may not be.  If the outside leaves aren't browning or the center of the biggest steaks are still tough, give them more time in the oven.

This certainly won't pass as meat, if that's a concern in your household, but it makes a great center dish for dinner.  It's nothing like the sulfurous boiled cabbage that we were subjected to in the 1970s.  The larger steaks have been substantial enough---and tasty enough, especially given how little work is involved---that I regretted adding a side dish, though I can't speak to the nutritional aspects of *only* eating cabbage for dinner on a regular basis.

I normally don't write about what I cook, since I've made many of the same dishes for years and even those dishes are mostly just improvised, but this was novel enough and specific enough to warrant a mention in a "developer diary" entry.

## Next

I suspect that I'll continue on these projects, though as I've mentioned, I also see library updates piling up.

* * *

**Credits**:  The header image is [Khamla Panyasouk of Big Brother Mouse reads to children](https://commons.wikimedia.org/wiki/File:Khamla_Panyasouk_of_Big_Brother_Mouse_reads_to_children.jpg) by [Blue Plover](https://commons.wikimedia.org/w/index.php?title=User:Blue_Plover&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license.
