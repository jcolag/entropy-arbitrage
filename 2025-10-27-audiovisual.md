---
layout: post
title: Developer Diary, Audiovisual Heritage
date: 2025-10-27 07:21:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, codeberg-move, codidact, library-updates, newsletter]
summary: Progress on assorted projects
thumbnail: /blog/assets/Dukane-Record-Automatic-Filmstrip-Projector.png
offset: -38%
description: This week's projects include the blog's newsletter, a Codidact answer, the blog's code, board game(s), procedural storytelling, the Fish Scala go-fish game, the Concept Random Walk, Glade Glue to ease GTK+ work, a credit card validator, the Base Dice game, and some library updates, mostly migrations to Codeberg.
spell: Miniboost Zoea Dukane Codidact Quarkdown endcook CPREP P44_dz Luhn
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate the [World Day for Audiovisual Heritage](https://en.wikipedia.org/wiki/World_Day_for_Audiovisual_Heritage), highlighting the need for preservation of audio and visual works, pushing for and celebrating accessibility of such archives, the relationship to other heritage issues, and so forth.

![An early filmstrip projector with integrated record player](/blog/assets/Dukane-Record-Automatic-Filmstrip-Projector.png "I first realized that I had gotten significantly older at a previous job where a colleague had concerns about teleconferencing in one of their advisors for their PhD thesis, and I suggested having them synchronizing the presentation slides with a beep like filmstrips...only for the entire group to stare at me as if I made up a bunch of words...")

And with that, on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the first.
4
If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the fourth of November.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For October, I wrote a piece on my likely next books now that I have gotten my "sea legs" on [Quarkdown](https://quarkdown.com/), discussed my media consumption slanted a bit towards Hispanic American Heritage Month and Filipino American History Month, and provided some background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Codidact

Yesterday, surprisingly close to my heart, I provided an answer for [How to refresh hard, dried bread](https://cooking.codidact.com/posts/294847/294849#answer-294849).  Short version, heat it.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

For the smallest change, because I needed it for a recent post, the circus tent {% emoji circus tent %} emoji now has a readable name in the blog's lookup file.

Larger, specifically for the introduction of the post on [Framework's myopic obsession with big tents]({% post_url 2025-10-19-big-tents %}), the plugin to create pull quotes now processes Markdown, because the joke of fake ads---all pointing to [my web store](/store), by the way, despite their appearances---wouldn't make sense if it couldn't actually link.

And finally, I created a plugin for quick "recipe cards."  Here, let's take and formalize a recent not-quite-a-recipe that I posted a few weeks ago as an example of what this new plugin can do.

{% cook 1|Granola Butter %}
Toast @rolled oats{2%c} until golden brown.  Blend/process with at least half the @oil{1/2%c}, @coconut butter{1/4%c}, @cinnamon{2%tsp}, and @salt{1/4%tsp} until smooth, increasing the amount of oil to thin out the paste.

Add @honey{1%T} to sweeten, adding more of the oil if the emulsion becomes too stiff again.
{% endcook %}

Not bad, right?  It took the following input, by the way, as you can see in the post's [Markdown source](https://codeberg.org/jcolag/entropy-arbitrage-posts/raw/branch/main/2025-10-27-audiovisual.md).

> Toast @rolled oats{2%c} until golden brown.  Blend/process with at least half the @oil{1/2%c}, @coconut butter{1/4%c}, @cinnamon{2%tsp}, and @salt{1/4%tsp} until smooth, increasing the amount of oil to thin out the paste.
>
> Add @honey{1%T} to sweeten, adding more of the oil if the emulsion becomes too stiff again.

The plugin calls the [Cook Language](https://cooklang.org/)---yes, I found a programming language for cooking...---conversion utility to translate its language into Markdown, saving the trouble of an explicit ingredients (and equipment) section and the like.  It then does some minor post-processing to better fit the blog's format, and renders the result to HTML inside a [field set](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/fieldset) element, because I couldn't think of another element that supports a [legend](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/legend) or similar element to give the impression of a card tab with the title.

I don't like that it renders fractions as decimals, and feel like it should sort the ingredients to catch repetition; on the latter, if I `@` the subsequent mentions of oil, which seems like an entirely reasonable thing to do, each reference gets listed as a separate ingredient.  But it certainly works a lot better than what I've done to date for recipes.  And I have started collecting my recipes---some of which I'll probably post to the blog as the holidays approach, and I put most of them together for holiday dinners---to Cook's syntax.

## Board Games

{% codeberg jcolag/board-games %}

Years back, though recent enough that I [wrote a blog post]({% post_url 2020-03-22-oubliette %}), I had a few ideas for small board games that a group of players could quickly try alone *or* attach to some version of [*The Landlord's Game*](https://en.wikipedia.org/wiki/The_Landlord%27s_Game).

Only one got through enough of the development process to release, *Open Oubliette*, something for *Landlord* players to do while in jail.  And in my quick tests, I'd also call it reasonably fun for a game designed to end in three turns.

In any case, you can now find the game---and any similar games that I get back to in the future---on Codeberg.

## Procedural Stories

{% codeberg jcolag/procedural-stories %}

After working on [Auto Story](https://codeberg.org/jcolag/autostory/), I created this repository of tools to help flesh out a story's world.  It includes a prototype version of what became [CPREP](https://codeberg.org/jcolag/cprep-background-generator), an attempt to simulate a solar system's position and apply (what I could glean of) astrology's methods to spin out the start of a "reading" for a character, and a couple of other items.

Again, I have moved this over to Codeberg.

## Fish Scala

{% codeberg jcolag/fish-scala %}

At some point, despite my general distaste for the Java ecosystem[^P44_dz], I decided that I wanted to check out Scala's usefulness for a project.  Without much time on my hands for the experiment, I put together a Go Fish game.  It came to two hundred lines, with plenty of comments and space for readability, so I considered it a minor success, though not enough to use the language for much else.

[^P44_dz]:  Maybe I resent it more than dislike it, since it launched with the "write once, run everywhere" idea, but made the virtual machine so complicated that it could only run on (at the time) high-end systems.  But it also has weird file-system-based permission rules and other aspects that don't seem serious.

In any case, yes, I have moved the repository to Codeberg.

## Concept Random Walk

{% codeberg jcolag/concept-random-walk %}

Long before Large Language Models began polluting the "how do we generate relevant text" space, I stumbled on [Concept Net](https://www.conceptnet.io/) and its minimal API.  It doesn't look like I had much of a *plan* for it, but the program---which needs an *HTTPS* URL, these days, before the code will work---takes an input word and tries to find an "interesting" associated word, not building a sentence, but a chain of thought.

It also caches the API responses as it runs, speeding up the responses when you later need the same run and reducing the load on their servers.  A smarter version could use more targeted parts of the API response, in theory, keeping random text generation somewhere in the conceptual neighborhood.

Again, the repository has moved over to Codeberg, if I get back to it.

## Glade Glue

{% codeberg jcolag/glade-glue %}

This might take some work to explain...

GTK+ user interfaces describe the layout of the user interface.  An application, generally written in C, reads that description and populates the interface, then sets variables and handlers to attach elements of the interface to functionality in the program.

[Glade](https://glade.gnome.org/) reduces the first part of the process by making it possible to lay out the user interface visually, an old enough application that it still calls itself a "Rapid Application Development" (RAD) tool.

When I tried working with this, I found one significant problem in developing applications this way:  The C code still needed to have some way of knowing about the elements of the user interface in advance.  And yes, you can do that by reading the GTK+ layout file, but who the heck wants to do *that*?

This script does that work in advance, creating C source with a header file to "operate" the user interface on behalf of the main program, so that the main program can focus on what it needs.

And yes, you can now find the repository on Codeberg.

## Credit Card Validator

{% codeberg jcolag/credit-card-validator %}

A long while ago, I thought that I might need to validate credit card numbers on the server.  Since most people do this on the client, I don't imagine that anybody will need this code except as a guide, unless it happens to work well under [Blazor](https://en.wikipedia.org/wiki/Blazor).  However, it has a comprehensive (as of a decade ago) list of bank card number ranges, a check for the proper length for the issuer, and validates the number via the [Luhn algorithm](https://en.wikipedia.org/wiki/Luhn_algorithm) for those issuers that use it.

And you guessed it, it has landed on Codeberg, too.

## Base Dice

{% codeberg jcolag/basedice %}

A long while ago, somebody whose name I have lost outlined an idea for a web-based bar-style game that combined [baseball](https://en.wikipedia.org/wiki/Baseball) and [craps](https://en.wikipedia.org/wiki/Craps).  When I found the rules many years later, since any non-disclosure agreement that I might have signed surely expired, you can't copyright rules, and so forth, I decided to implement the thing for my amusement.

Neither the web version nor the console version uses any permanent storage, which I feel undermines some of the fun, but it does work, if you get the infrastructure running.

Honestly, if I had to do it again, I probably wouldn't do it in C#.

In any case, this makes the last of this week's projects moving to Codeberg.

## Library Updates

Back over on GitHub, I needed to bump a library versions for [Miniboost](https://github.com/jcolag/Miniboost) and [Zoea](https://github.com/jcolag/zoea), largely to make sure that I didn't break the "streak" of commits that has lasted a while.

## Next

Expect more migrations from GitHub to Codeberg.  I think that we've gotten near the end of the list, but I have probably also said that for the last few weeks...

* * *

**Credits**:  The header image is [Dukane Record Automatic Filmstrip Projector](https://commons.wikimedia.org/wiki/File:Dukane_Record_Automatic_Filmstrip_Projector.jpg) by [Toy Polar Bear](https://commons.wikimedia.org/w/index.php?title=User:Toy_Polar_Bear&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
