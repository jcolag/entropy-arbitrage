---
layout: post
title: Developer Diary, Child Health Day
date: 2024-10-07 06:55:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [codidact, library-update, lights-edge]
summary: Progress on assorted projects
thumbnail: /blog/assets/DPLA-4461efafd5c4ba7fde8eedb1f13f439e.png
offset: -30%
teaser: This week's projects include Codidact answers and a question, The Light's Edge (website, episodes, and toys), and a bunch of library updates.
spell: Codidact Bisheng CPREP Fýlakas Onomáton OpenSCAD
proofed: true
---

* Ignore for ToC
{:toc}

In the United States, in accordance with [36 U.S.C. § 105](https://www.law.cornell.edu/uscode/text/36/105), the first Monday in October designates [Child Health Day](https://en.wikipedia.org/wiki/Child_Health_Day), bringing awareness to the need for year-round health programs.

![International children dressed in their native costumes participate in the 100th anniversary of the Statue of Liberty](/blog/assets/DPLA-4461efafd5c4ba7fde8eedb1f13f439e.png "I now live in fear that I might have actually known some of these kids...")

Anyway, off we go to the projects.

## Codidact

This time through, I provided answers for [Would it make sense for an organization that has existed for centuries not remember its own origins](https://proposals.codidact.com/posts/292717/292719#answer-292719) and [What are reasonable limitations for probability-manipulating magic?](https://proposals.codidact.com/posts/292716/292720#answer-292720).  And I decided to finally *ask* a question, looking for [Fonts That Support the Creative Commons Unicode Symbols](https://powerusers.codidact.com/posts/292744).

## The Light's Edge

{% codeberg jcolag/thelightsedge %}

The repository for the project website should now fully conform to the [REUSE](https://reuse.software/) standard, other than---as far as I can tell---the single proprietary license.  The couple of licenses that I expected to need but didn't, because I used the images within more complex images, no longer appear in the repository.  And the final files got license specifiers.

This ended up taking longer than I expected, suggesting that REUSE makes much more sense at the start of a project instead of something applied later, although this may also save effort down the line, especially if people borrow aspects of the project for other things, so don't go by my uninformed opinions.  That said, it'll definitely take a lot to convince me to use this for any pre-existing repositories, especially considering how most repositories only really need one license.

## The Light's Edge (Episodes)

{% codeberg jcolag/lights-edge-episodes %}

While I haven't yet added anything of substance to it, the actual contents of **The Light's Edge** now have a home waiting for them.  I have enough written now that I expect to start serializing the story sometime this month, assuming that you don't count the in-universe work that I've sprinkled around the Internet.

I haven't decided how I'll use the repository, other than as a distribution site and a way to manage any contributions.  For example, I don't know if I'll push Markdown and HTML files here before their official release, or if the "official" versions go out first.  Bear with me, then, and I encourage people to make the story theirs.  While I chose the sources with an intent of making something that feels like it would fit in the mainstream and have a lot of possible directions to go in, I also realize that it should work as a new setting for any &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608; fan fiction that people want to separate from the big franchises.  And I also see plenty of room for people to reinterpret the characters and events to better suit their needs.  I won't always make changes to my version that don't work for me, but I don't necessarily have the "correct" version of events, only the version that I put on the website...

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

On a whim, I decided to model the Rail Runner in OpenSCAD.  I don't expect that anybody will use it without a ton of added work, but I liked the idea of proving that the same idea would work in other media.  It scales nicely, changing the scale factor in the `unit()` function to shift from quartets-of-millimeters (the current default) to inches or whatever.  If you want one big enough to sit in yourself, I say go for it, provided that you can find the printer with that kind of capacity.

Eventually, I'd like to parameterize the cabin shape, too, based on the rear-facing angle, similar to what I did for the "wing" angles.  That'll take more trigonometry than I feel like doing right now, though, so it'll wait.

## Library Updates

I needed to bump library versions for [**Bicker**](https://github.com/jcolag/Bicker), [**Bisheng**](https://github.com/jcolag/bisheng), [**CPREP**](https://github.com/jcolag/background-generator), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Renew DB**](https://github.com/jcolag/RenewDB), and [the blog's code](https://github.com/jcolag/entropy-arbitrage-code).

## Next

Honestly, I have no idea what I have coming up.  I have many projects that I'd *like* to return to, but many of them require research or inspiration, so we'll have to see what comes up.

* * *

**Credits**:  The header image is [International children dressed in their native costumes participate in the 100th anniversary of the Statue of Liberty](https://dp.la/item/4461efafd5c4ba7fde8eedb1f13f439e) by a Department of Defense photographer, in the public domain as a work of the United States government.
