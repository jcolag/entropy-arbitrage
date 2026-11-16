---
layout: post
title: Developer Diary, Icelandic Language Day
date: 2026-11-16 07:51:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, chasing-phantoms, common-calendar, earburn, intern, license, multiply, posturing, prim, smoke-alarm, turing-machine]
summary: Progress on assorted projects
thumbnail: /blog/assets/saga-icelanders.png
offset: -26%
description: This week's projects include licensing updates and the blog's code.
spell: Íslendingasögur earburn PosTuring Jónas Hallgrímsson Kabang Gilwellian
proofed: true
---

* Ignore for ToC
{:toc}

Today marks {% wiki Icelandic Language Day %}, celebrating pretty much what it says on the box, via the birthday of Icelandic poet {% wiki Jónas Hallgrímsson %}.  You all know that I can't really resist a language day...

![A reproduction of a page from the Íslendingasögur](/blog/assets/saga-icelanders.png "I like that the illumination has its own illumination...")

And with that, on to the week's projects.

## Itch, Week 2

Continuing a highly irregular addition to these posts, I want to start thanking the---anonymous; the Itch dashboard doesn't provide any further information than daily numbers---people checking out the project pages.

This week, we have ten people.

- Monday, another fifteen people checked out [Open Oubliette!](https://jcolag.itch.io/open-oubliette), plus two on Tuesday, two on Wednesday, and one on Thursday.  I would estimate that at least three people downloaded at least part of the project.
- On Thursday, two people also checked out [Kabang!](https://jcolag.itch.io/kabang).

Thanks to you!  Feel free to follow me, because I do have more projects coming...at some point.

If this insight helps anybody with anything, I can't help noticing that a stripped-down board game has gotten more attention in a bit more than one week than a novel and an arcade-style game combined have gotten in almost three months on Itch.  In total, the novel has gotten six views, the video game seventeen, and the printable game thirty.

## Clearer Licensing, Part 4

To recap the point of this exercise, the public licenses that I use all include an attribution requirement to some extent.  And while the AI industry continues to use its software to launder copyright as "intelligence," it has started to make sense to make a bigger stink about that attribution.  To make this as convenient as possible, I chose the [REUSE](https://reuse.software/) standard that I have used elsewhere, since it ensures that every file has attribution and licensing information; going file by file also nicely resolves some common edge-cases, such as when I include a file from someone else's project or when worrying about whether anybody has the right under the AGPL to see the alterations to a configuration file, revealing API keys and passwords.

This time through, I got the following into shape.

- That low-end [Multiply](https://codeberg.org/jcolag/multiply) game
- My attempt at a [Turing Machine Assembler](https://codeberg.org/jcolag/tmasm)
- My [PosTuring](https://codeberg.org/jcolag/PosTuring) interpreter
- The [Prim](https://codeberg.org/jcolag/Prim)
- [INTERN](https://codeberg.org/jcolag/intern) and its [Ask INTERN](https://codeberg.org/jcolag/ask-intern) client
- [Chasing Phantoms](https://codeberg.org/jcolag/ChasingPhantoms)
- [Smoke Alarm](https://codeberg.org/jcolag/smoke-alarm), the (mostly abandoned) attempt at a burnout tracker
- My [Earburn](https://codeberg.org/jcolag/earburn) browser plugin
- The [Common Calendar](https://codeberg.org/jcolag/common-calendar)

I do have a post in the works describing my workflow for this and the small glitches, but this week has something else happening...

## Entropy Arbitrage, the Code

{% codeberg jcolag/entropy-arbitrage-code %}

Directly connected with the work on licensing clarity, I stumbled across more files where REUSE put the information in a spot that broke pages.

## Next

I'll probably launch a project this week that I don't really have the time to dedicate to (and I still don't like my working names for it) like it deserves.  Otherwise, I'll probably continue with licensing, and Open Oubliette! also needs an update with what I did to produce the book and images that you see up on Itch.

* * *

**Credits**:  The header image comes from [Íslendingasögur](https://commons.wikimedia.org/wiki/File:%C3%8Dslendingas%C3%B6gur.jpg) by [Gilwellian](https://commons.wikimedia.org/wiki/User:Gilwellian) (the photograph, not the page), long in the public domain due to expired copyrights.
