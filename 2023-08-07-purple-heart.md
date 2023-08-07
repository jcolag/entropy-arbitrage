---
layout: post
title: Developer Diary, Purple Heart
date: 2023-08-07 07:08:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/badge-of-military-merit.png
teaser: This week's projects include reporting back on Saturday's "office hours," new project Notoboto, and a batch of library updates.
spell: Lemmy notoboto Jectoons Miniboost Tcl Tk boto botos nonogram Replybrary Slackup Zoea Husnock
proofed: true
---

In the United States, today marks the 241<sup>st</sup> anniversary of the creation of the [Badge of Military Merit](https://en.wikipedia.org/wiki/Badge_of_Military_Merit), now known---or, arguably, succeeded by---the [Purple Heart](https://en.wikipedia.org/wiki/Purple_Heart).  While I don't generally go in for militarism, even I can accept that maybe we should at least briefly applaud those who sacrificed their bodies or entire lives to defending their country, even (or *especially*) if they didn't believe that the situation warranted military action.

![A Badge of Military Merit](/blog/assets/badge-of-military-merit.png "Not to derail the topic, but it vaguely surprises that, at least to my knowledge, nobody produces a military-themed parody of Lucky Charms cereal...")

I could get into massive arguments about the specific criteria, as you might guess, but I'll save my pedantry for talking about projects.

## Social Media

As teased for arbitrarily chosen parts of last week, on Saturday, I experimented with an "office hours" format on Matrix and Cohost.

I "only" had one person showed up on Matrix---someone who you might recognize from [**Random Vignettes**]({% post_url 2023-05-13-vignettes %}), now in its third season---but we had a pretty great, wide-ranging conversation for a couple of hours.  To my eyes, that qualifies as a success, but don't fret if you feel left out.

I may do this again in the future, but more importantly, I want to suggest that *other* people (like you, or maybe even literally you) hold their own office hours.  I realize that the premise feels a lot like something that only makes sense if you frequently use the phrase "personal brand" non-ironically, but you can get a Matrix chatroom running in seconds, and it feels like a fairly good platform for casual discussions.  Really, if you have any people interacting with what you do voluntarily, set it up; it can't go worse than giving you time to work on something.

Meanwhile, I appear to have had a *second* problem with Lemmy.  In this case, based on some quick debugging, my server doesn't seem to send the multifactor authentication code to the right location, so I can't log in.  I'll give it another day or two before seeing if I can find a way to report the issue, since I don't know why it changed.

## Notoboto

{% github jcolag/notoboto %}

I finally decided to give up on [Valence Native](https://github.com/valence-native/valence-native).  After more than three years, they still haven't even really updated their documentation, let alone fixed issues or advanced the functionality that they provide.  In addition, I've started to conclude that JavaScript might make a poor choice for "light-weight" desktop applications.

Given that, I have decided to mostly abandon work on my [**Miniboost**](https://github.com/jcolag/Miniboost) note-taking application and develop something that'll actually do the job without much overhead or concerns of incomplete features.  And after more research and discussions than I care to admit, I landed on [Tcl](https://en.wikipedia.org/wiki/Tcl)/[Tk](https://en.wikipedia.org/wiki/Tk_%28software%29).

Why use a programming language and toolkit released over thirty years ago that almost nobody else uses?  I'd call that a good question, especially since I went to the trouble of installing [Qt](https://www.qt.io/) instead.

It started to take too long to figure out how to use Qt's various tools, though.  And short on time, I couldn't work out how to put anything useful together, probably due to prerequisites.

By contrast, Tcl/Tk seems stable, and people have run such applications for long enough that I *probably* don't need to care much about CPU and memory footprints for my notes; in 1988, the [most powerful computer in the world](https://en.wikipedia.org/wiki/Connection_Machine) had less than a hundredth of the processing power on modern commodity graphics processors, and a high-end home computer would have had about a hundredth of *that* supercomputing power.  Tcl has a *slightly* more pleasant syntax for laying out user interfaces (to my eyes) than most of the languages boasting Tk libraries.  The ecosystem has a distribution format, so that people can run applications without worrying about installing anything special.  And my note-taking doesn't seem to have any extreme requirements that will make me wish that I had access to the breadth of libraries available for languages like Ruby, JavaScript, or Python.

Currently, the program doesn't do much.  I created the repository and added an empty window.  But I can see it taking shape quickly and feel optimistic that this will survive longer than **Miniboost** did.

Oh, and the name jokingly plays around with the name of [Boost Note](https://boostnote.io/), the original version of which created the notes that **Miniboost** uses and **Notoboto** will use.  Looking for anagrams of "boost," to both retain aspects of the name but also push away from it, I discovered [botos](https://en.wikipedia.org/wiki/Boto), South American dolphins.  The similar and repeated vowel led me to replace the silent-e in "note" to conform, and drop the plural.

## Library Updates

I needed to bump library versions for the [**Daily Nonogram**](https://github.com/jcolag/picture-nonogram), my [**Mastodon Tool Trunk**](https://github.com/jcolag/tool-trunk), my [**Morning Dashboard**](https://github.com/jcolag/dash), [**Replybrary**](https://github.com/jcolag/library-twtterbot), [**Slackup**](https://github.com/jcolag/slackup), and [**Zoea**](https://github.com/jcolag/zoea).  Somewhat shockingly, that clears out my queue, at least for now.

## Next

Now that the queue of library updates has finally cleared out, I'll probably continue with **Notoboto** and go back to the **Mastodon Tool Trunk**.  Maybe more the former than the latter, since I actually *need* a working program for notes, whereas Mastodon already works, even if not how I'd prefer.

* * *

**Credits**:  The header image is adapted from [Badge of Military Merit, an award in the United States](https://commons.wikimedia.org/wiki/File:MeritBadge.jpg) by [Husnock](https://en.wikipedia.org/wiki/User:Husnock), placed in the public domain by the photographer.  The badge itself would have no copyright, both as a work of the United States government and its age.
