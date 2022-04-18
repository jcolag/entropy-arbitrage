---
layout: post
title: Developer Journal, World Heritage Day
date: 2022-04-18 06:17:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Great-Wall-of-China.png
offset: -25%
proofed: true
---

Today is the [International Day For Monuments and Sites](https://en.wikipedia.org/wiki/International_Day_For_Monuments_and_Sites)---also known as World Heritage Day---meant to draw attention to monuments and cultural heritage sites.

If you don't find that worth celebrating, then you might also or instead find yourself mid-[Passover](https://en.wikipedia.org/wiki/Passover), recovering from [Easter](https://en.wikipedia.org/wiki/Easter), or observing [Ramadan](https://en.wikipedia.org/wiki/Ramadan), in which case, I hope that you have or had a great one.

![The Great Wall of China](/blog/assets/Great-Wall-of-China.png "It feels like a grave historical injustice that Mongolia hasn't built The Awesome Ladder of the Eurasian Steppe as a tourist trap...")

It just occurred to me that a terrifying future probably exists where international organizations designate a day to remind people that code exists, and show that off in strange celebrations...

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Last week, I had some small "maintenance" changes to make to the blog's code, none of them earth-shattering.

Actually affecting the blog, albeit minimally, I changed the Friday [Twitter roundup](/blog/tag/week) post generation script to no longer file those posts under the `media` category.  I never *quite* understood what purpose the post categories served, and they only really seem to complicate guessing at the URL, so I won't use them anymore.  Prior posts will maintain their existing URLs, but the format simplifies, going forward.

In my static analysis script (`check.sh`), I changed the [proselint](http://proselint.com/) configuration file's name to match the program's current convention, since it currently issues a warning.  While there, I also fixed some paths in the script, to make sure that I can launch it from anywhere.

And finally, I explicitly ignored the "file offset-to-line number" map file that I generate when performing static analysis on the posts, to make sure that I don't accidentally publish or commit any of them.

## Small Things

{% github jcolag/SmallThings %}

In my dumping ground of quick experiments, I added [Mermaid](https://mermaid-js.github.io/) code to generate a flowchart for a bubble sort, to make sure that I understood the syntax.

Unfortunately, this process taught me that the Mermaid code...how can I put this delicately?  It doesn't prioritize robustness.  That is, it either produces a diagram from the description, or it produces an unenlightening image stating that the description had an error.  Granted, I have the experience to know how to chop out lines to perform a binary search until I find the offending line.  However, it's 2022, so why does this responsibility get dumped on me?

In any case, once someone squashes the syntax errors, the results look decent.

![A bubble sort flowchart](/blog/assets/assets/bubble_sort_mermaid.png "Don't use this sort in production")

If that design doesn't work, I could add a stylesheet, so this might become my standard format for diagrams, going forward.

I also found an old experiment in getting Elixir to provide a system/user folder's path.

## Library Updates

I needed to bump library versions for [**Uxuyu**](https://github.com/jcolag/Uxuyu), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Bicker**](https://github.com/jcolag/Bicker), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), 

This probably won't remain true for long, but for now, that clears out my backlog.

## Next

This week, now that I've gotten comfortable with Mermaid, I may finally look to find a way to integrate it with **Miniboost**.  Its inspiration project [Boost Note](https://boostnote.io/) announced a similar change *right* around the time that I stopped using it, so it makes sense for compatibility.

* * *

**Credits**:  The header image is [P1090119 Chiny](https://commons.wikimedia.org/wiki/File:P1090119_Chiny.JPG) by [Jsporysz](https://commons.wikimedia.org/w/index.php?title=User:Jsporysz), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
