---
layout: post
title: Developer Diary, Balipratipada
date: 2026-11-09 07:44:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [basic, board-games, etched-windows, glade-glue, library-update, license, mini-server, mystic-t-square, social-media, thue]
summary: Progress on assorted projects
thumbnail: /blog/assets/annakut.png
offset: -26%
description: This week's projects include social media updates, an Itch update, my mini-server, license work, my board game work, and some library updates.
spell: Balipratipada Dīpāvalī Annakut Padyami Pratipada Goverdhan puja Kartik Shukla Padwa Shree Swaminarayan thue Disroot Webmentions Kabang Pinebook dnf Twitterbot Scuttlers Nonogram SaLaVI
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the fourth day of {% wiki Diwali %} (Dīpāvalī), the (not exclusively) Hindu festival of lights, known---the day, I mean---by many names including Annakut, Bali Padyami, Bali Pratipada, Goverdhan puja, Kartik Shukla Pratipada, Padwa, and others.  Regardless of the name, most Hindu-influenced communities use it to celebrate the bond in marital relationships, though the implied fertility aspects also go well with agricultural symbols and harvests.

![Annakut community meals at Shree Swaminarayan Temple Auckland, New Zealand](/blog/assets/annakut.png "You can't go wrong with snacking holidays")

And with that, on to the week's projects.

## Social Media

I should note that [Fe.Disroot](https://fe.disroot.org/@jcolag) came back online as Disroot works out what data they can salvage from their disaster, so if you follow me there to avoid [my Mastodon account](https://mastodon.social/@jcolag) or want the Webmentions back, both should now have returned.

As a similar problem, my Diaspora "pod" (server) had a snag with its domain name, so [my account](https://nota.404.mn/people/e4313920967a0136074b076893c08a76) went silent for most of the week while they resolved that.  Admittedly, I briefly half-considered abandoning the network, since I had already lost most of my correspondents when a major server shut down a few years back, and I haven't seen much growth or activity.  As long as the server runs, though, I might as well continue doing what little I can to support the network.

## Itch

This feels like it'll end up a highly irregular addition to these posts unless I spontaneously become popular, but since the initial flurry of activity tapered off last month, I want to start thanking the---anonymous; the Itch dashboard doesn't provide any further information than daily numbers---people checking out the project pages.

This week, we have ten people.

- On Friday, somebody at least looked at [Kabang!](https://jcolag.itch.io/kabang)
- Shortly after I uploaded it Sunday (yesterday) evening---more about that later---nine people almost immediately checked out [Open Oubliette!](https://jcolag.itch.io/open-oubliette), including a...poorly counted number of downloads, considering that I uploaded all the parts separately.

Thanks to you!  And I only now realized that I have multiple projects with exclamation points in the title, each because the works that most directly inspired them used exclamation points.

## Mini-Server, Part 38

I continue to find NetBSD on the Pinebook somewhat confounding.  I spent a while trying to search for the magic words to install software---equivalent to `apt`, `dnf`, and the like---hoping to get a usable desktop environment to work with, only to realize that it didn't matter yet, because I haven't attached to the network.  And then I spent a lot more time trying to figure out how to convince it to recognize anything but the loop-back adapter that would let me run servers local to the computer.  And I call this "confounding" rather than "annoying that I don't have more time to sink into this," because they ship a Pinebook-specific build.  They know the hardware, so I feel like I shouldn't need to jump through these hoops.

And no, I still haven't installed NetBSD to the internal drive, because until I work out problems like this, I don't see much point.

## Clearer Licensing, Part 3

To recap the point of the exercise, the public licenses that I use all include an attribution requirement to some extent.  And while the AI industry continues to use its software to launder copyright as "intelligence," it has started to make sense to make a bigger stink about that attribution.  To make this as convenient as possible, I chose the [REUSE](https://reuse.software/) standard that I have used elsewhere, since it ensures that every file has attribution and licensing information; going file by file also nicely resolves some common edge-cases, such as when I include a file from someone else's project or when worrying about whether anybody has the right under the AGPL to see the alterations to a configuration file, revealing API keys and passwords.

This time through, I got the following into shape.

- My [BASIC Interpreter](https://codeberg.org/jcolag/basic-interpreter)
- [Etched Windows](https://codeberg.org/jcolag/etched-windows)
- [Glade Glue](https://codeberg.org/jcolag/glade-glue) glue-code generator
- [Mystic T-Square](https://codeberg.org/jcolag/mystic-t-square)
- The [Thue](https://codeberg.org/jcolag/Thue) programming language interpreter

At some point, I should probably write something about the tool, because I keep running into small annoyances or weird design decisions for their tooling.

## Board Games

{% codeberg jcolag/board-games %}

To get it to render correctly when embedded in an EPUB file, the Open Oubliette! game board SVG file now has the [Bangers](https://fonts.bunny.net/family/bangers) font embedded in it.

Why?

As mentioned earlier, you can now find [**Open Oubliette!** on Itch](https://jcolag.itch.io/open-oubliette) as well as the prototype/preview posted last week on Buy Me a Coffee, name-your-own-price as usual on Itch.  I wanted to supply the rules in both PDF and EPUB formats, and then spent *far* too much time trying to work out how to convince the vector image to render the font properly.

## Library Updates

I needed to bump library versions for [Ham Newsletter](https://codeberg.org/jcolag/ham-newsletter), the obsolete-except-for-learning [Library Twitterbot](https://github.com/jcolag/library-twtterbot), [Little Scuttlers](https://github.com/jcolag/LittleScuttlers), [Picture to Nonogram](https://codeberg.org/jcolag/picture-nonogram), [SaLaVI](https://codeberg.org/jcolag/salavi), and [VS Code Rat](https://codeberg.org/jcolag/vscode-rat).

## Next

I need to clean up some problems that REUSE caused the blog.  And I'll add the code and other changes made to turn my earlier Open Oubliette! work into a "product."  Otherwise, I have started planning a fairly large project---clear hints dropped on Mastodon, in the blog, and in the newsletter over the past couple of months---and it'll probably require my learning at least three different technologies/techniques to do right, so I'll probably continue on with lower-effort changes so that I can focus.  And that doesn't even get to the sewing project(s) that I need to get back to.

* * *

**Credits**:  The header image comes from [Annakut](https://commons.wikimedia.org/wiki/File:Annakut.jpg) by [Around the Globe](https://commons.wikimedia.org/wiki/User:AroundTheGlobe), made available under the terms of the [GNU Free Documentation License v1.2 or later](https://www.gnu.org/licenses/old-licenses/fdl-1.2.html), which I *think* that I can get away with using here.
