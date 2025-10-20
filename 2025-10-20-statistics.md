---
layout: post
title: Developer Diary, World Statistics Day
date: 2025-10-20 06:59:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/WorldStatsDay-Logo-ES-b.png
offset: -30%
description: This week's projects include a Codidact answer, Key Wand, the blog's code, GenAudio scripts, an old attempt at a card game, Type Time reaction-tracker, x-Gamebook, Auto Story, two time-tracking applications.
spell: Codidact GenAudio gamebook Nanomonestotse keywand Wikiversity ffmpeg typetime xGamebook autostory uManage
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate [World Statistics Day](https://en.wikipedia.org/wiki/World_Statistics_Day), which to absolutely nobody's surprise honors statistics.  Possibly more surprising, we only celebrate it every five years, so get ready for some pent-up percentage jokes, I suppose.

![A poster for World Statistics Day 2015, in Spanish](/blog/assets/WorldStatsDay-Logo-ES-b.png "You all realize that I used this for the horrifying ASCII mascot ⹛%, right...?")

More routine, we have [Nanomonestotse](https://en.wikipedia.org/wiki/Nanomonestotse), a modern Native American celebration of peace starting on the third Monday of October.

With that, on to the week's projects.

## Codidact

[Search tool for PDF content with verbatim text including special characters](https://powerusers.codidact.com/posts/294742/294743#answer-294743) caught my interest, so I did some quick research and turned up an interesting tool.

## Key Wand

{% codeberg jcolag/keywand %}

I believe that I have finished all the work that I considered necessary for [Key Wand](https://jcolag.codeberg.page/keywand/).  Beyond the default functionality, it now saves and applies data to and from local storage, wipes the password if you delete the name/domain, and cleaned up the styles for the sliders, including---in the clunkiest way possible, because alternatives didn't work for me---adding little show/hide icons (open and closed eyes) to indicate the state of the switch.

By the way, did I mention that, for the color scheme, I went with [Rosé Pine](https://rosepinetheme.com/)?  Well, it at least uses my extended interpretation of it as built for [Boring CSS](https://codeberg.org/jcolag/boring-css).

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

I needed to make two small updates to the blog.

First, a little late, but specifically for the [Wikiversity Science Fiction Challenge]({% post_url 2025-09-27-wsfc-mnemtronium %}), arbitrary embedded `video` elements have a maximum width of the blog's width.

Then, I needed to bump the version of one of the libraries.

## GenAudio

{% codeberg jcolag/GenAudio %}

Even though I don't actually have anything to say about the project beyond "I moved it to Codeberg," this might warrant some explanation, partly because it gets deep in the weeds, but also because I don't think that I've really touched it since starting the blog.

About a decade ago, maybe more, I had the idea of treating television much like software.  Generally speaking, software and video have two broad parts.  You start with a vision of operation, a script if you will, usually cheap to produce, if only because you can find one person with the right kind of vision and lock them in a room until they deliver.  Once you have that conceptual frame ready, you throw labor at the effort of realizing the vision.  And in cases where some pieces will cost a lot, in software we usually fake it, creating placeholders for everybody to work around until the real version fits into place.

In the spirit of web application frameworks, I slapped together these scripts, which at least *try* to take a screenplay written in Markdown-like [Fountain](https://fountain.io/) (with some small extensions) and turn it into a video.  Because of what I had to work with ten years ago, it used pre-supplied portraits to illustrate each character speaking with the text shown under their faces, while a computer-generated voice brought them to clunky life.

I stopped playing with it after a while, because I couldn't convince all the pieces to pull together.  Specifically, to model a typical hour-long drama, my (I think unpublished) experiment had a teaser, opening credits, five acts, and closing credits.  To make those happen, it uses `ffmpeg` in three ways.

To create the scenes with dialogue, it generated the voice-over and the correct image, then called `ffmpeg` to turn the static image into video of twenty-four (I think) frames per second while the voice plays, then calls `ffmpeg` to combine all the lines into a single video representing the entire act.

Then, to create the credits, it did something similar, but changed the static image a few times to create a silent video running for the same length of the music, then added the music.

Each of those plays fine, and I can't see any structural difference between them, but then finally *combining* the eight videos (teaser, two credit blocks, and five acts) with `ffmpeg` somehow went wrong, with the credits no longer synchronized with the much, which then pushed the remainder of video out of synchronization.  And I never had the patience to debug it.  I *believe* that I posted a Stack Overflow or similar question at the time, and didn't get more than a shrug telling me that the video fragments probably differ in some way that matters to `ffmpeg`, which...yeah, no kidding; guess why I asked in the first place.

Anyway, I have always wanted to get this running again, so I dragged it over to Codeberg.  These days, I have to assume that we have a Free Software voice-cloning solution---that works; I hear that the old Python thing no longer does---where using snippets from [LibriVox](https://librivox.org/) would keep everything as ethical as possible while also making characters sound less like irritated German robots.

## Card Players

{% codeberg jcolag/card-players %}

Since I moved the other pieces of the prospective card game that I looked at about a decade ago over to Codeberg, it only seemed right to drag this part over, which takes the cards and the action-resolution and uses them to operate a web app to play.

Or, rather it *did* all that years ago.  Whether any of this works *today*, I couldn't tell you.  Back then, the Phoenix web framework didn't have a comprehensive way of seeding a database, so the seed code manually inserts each row manually using their ORM, to give you an idea of how far behind the times this might have fallen.

## Type Time

{% codeberg jcolag/typetime %}

Another project over to Codeberg, this falls into the category of something that I (still) use every day.  It doesn't have much to it, generating a random string of a given length and, after waiting a random time before displaying it, times how long it takes the user to repeat the string back.

For years---except for the few months when I returned to running Windows at home---it runs at the exit of my overnight script, logging my reaction time.  I use that as a rough proxy for recent sleep quality.  Rested, I generally manage to react, read, and type in about one-and-two-thirds seconds with no errors; sleep-deprived, it takes as much as eight seconds as I keep trying to fix my mistakes.  And in my favorite case, I woke up sufficiently groggy to not even notice the task until I got back from the bathroom...

## x-Gamebook

{% codeberg jcolag/xGamebook %}

Another maybe-obsolete project for the Codeberg pile, I tried using Elixir to simulate a "gamebook," the closest that I could find to a generic term for the "Choose Your Own Adventure" brand.  You can see in the limited documentation that I saw this as a possible frame for solo role-playing adventures with the previously discussed combat mechanics.

## Auto-Story

{% codeberg jcolag/autostory %}

Yet another project for Codeberg, this I did a *lot* of work on but never finished.  But it does at least the initial work of creating a random story outline by picking a subset of steps of the so-called Hero's Journey and, for each, picks a *dramatic situation* such as the following.

> [Protagonist] tries to overcome remorse for injury to someone for the common good.

And then it fills in the character archetypes with random names, with the sample list drawn from computer security examples, so these stories will probably have Alice and Bob joined by Wendy the Whistleblower, Paul the Questioner, and so forth.

I liked this, despite never finishing out my adaptation of the dramatic situations book, because tying a random situation to a given step in the Hero's Journey story suddenly gave the pairing meaning.  For example the overcoming of remorse mentioned above rings differently if you say that the situation describes the "Refusal of the Call" (early in the story) or the "Escape."  And it changes more if the program chose Arthur (the Seeker of Truth) or Trudy (the intruder) as the protagonist.

Now, the obligatory point that you all know that I'd make:  I chose the Hero's Journey because it has many steps, each with fairly firm specifications, *not* because I care about stories where a callow young man needs to grow up by venturing through the Underworld to claim his reward.  I used the computer security "character" names for the same reason even though they have no cultural diversity to them.  Because I constructed the "database" out of three CSV files, it doesn't take much effort to change the plot structure to some other tradition and fit the characters to the relevant culture.

## uManage

{% codeberg jcolag/uManage %}

Still moving things to Codeberg, this project fell by the wayside, but I still like the premise, and for a while, this (and the Windows version that I'll probably move to Codeberg this week) formed the backbone of my notes.  It periodically queries the (Linux, probably only GNOME) desktop for the active window and logs (among other things) the title of that window.

And yes, it recognizes idle time.

I got frustrated with time-tracking applications that forced *me* to do all the actual time-tracking...

For applications that show the current *document* in the title bar, this provides a record of everything worked on and for how long.  When I tried juggling multiple small consulting gigs, that let me quickly determine how many hours to bill each client for the day.  And more broadly, it let me pick up signals such as "I seem to spend too much of my day in e-mail," or playing some silly game, or any number of other things that I didn't want to lose so much time to.

If you try to get it running, I *would* suggest lengthening the polling time from the default.  I vaguely remember this occasionally crashing or locking the database.  And while I never ran down why it happened, in retrospect, I'd bet that it happened because the software didn't have enough time to check everything *and* report it before starting again.

## Track Time

{% codeberg jcolag/track-time %}

If you liked the idea of uManage but run on Windows, this C#/.NET application *should* still work, importing Win32 API functions directly from the Windows libraries to expose them to the application.  Unlike uManage, though, this doesn't maintain a database or do any side-work.

Oh, as I recall, though, Track Time should work a bit more intelligently.  If I remember correctly, it registers to handle a window-changed event, so it doesn't need to poll for updates.  When a new window gets focus, it *should* find and report that window's title, then goes back to doing nothing.

## Next

Eventually, I'll run out of projects to move to Codeberg.  But that might not happen this week...

* * *

**Credits**:  The header image is [World Stats Day Logo ES b](https://commons.wikimedia.org/wiki/File:WorldStatsDay_Logo_ES_b.png) by the United Nations Statistics Division, and doesn't really meet the threshold for copyright.
