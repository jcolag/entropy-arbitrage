---
layout: post
title: Developer Journal, Geography Awareness Week
date: 2021-11-15 06:40:03-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/world_phy.png
proofed: true
---

As we approach "the holiday season," minor holidays dry up.  So, this week marks the start of Geography Awareness Week, a celebration that has sprouted around [Geographic Information System (GIS) Day](https://en.wikipedia.org/wiki/GIS_Day).  Normally, I'd ignore this as an industry patting itself on the back, but the United States Geological Survey and the Library of Congress have both sponsored it, so it's at least *slightly* more than satellite/mapping companies inflating their importance.

![A physical world map](/blog/assets/world_phy.png "The Earth, presented in the famous UFO projection")

And while my code rarely deals with geographic data at this time, that's still at least a plausible excuse to change the topic to code.

## INTERN

As I hinted [last week]({% post_url 2021-11-08-rememberance %}), I needed to clean up the [**INTERN**](https://github.com/jcolag/intern) code, fixing the parsing for the new `@ago` command and refactoring the similar code from `@ago` and `@on`.

## Ask INTERN

So...Haskell.

The good news is that Haskell is a fairly nice [functional](https://en.wikipedia.org/wiki/Functional_programming) programming language, but it's frankly peculiar how dismal the ecosystem seems to be, in terms of standardization and documentation.

For example, it *appears* that tooling is supposed to be handled by [Stack](https://haskellstack.org)---which is what I used---but it's not really discussed anywhere other than its own site and an occasional blog post.  So, is it really the Haskell equivalent of [Yarn](https://yarnpkg.com/) or [Cargo](https://doc.rust-lang.org/cargo/)?  It's unclear whether this is unique or just one of many possible systems.

Likewise, while it's obviously somewhere in the Stack documentation, general documentation and tutorials don't bother to acknowledge that acquiring libraries is necessary to using them.  It seems to be the only language where the community can't be bothered to start an explanation with "add the following line to your `package.yaml` file," or often even mention the libraries being used in an example.

The upshot is that [**Ask INTERN**](https://github.com/jcolag/ask-intern) isn't going particularly well, and I'm not pleased.  It creates a query string from the command-line arguments, and the documentation is now readable, but I haven't had any luck sending the query over a socket, despite working from multiple tutorials and (alleged) working examples.

## Entropy Arbitrage

I updated the scripts for [this blog](https://github.com/jcolag/entropy-arbitrage-code), the more interesting change being that the script to move parts of a series ahead a few weeks finally works.  That was needed for reasons that will probably become clear in this Thursday's [Real Life in *Star Trek*](/blog/tag/startrek) post.

## Prototypes

I added a simple [Fyne](https://fyne.io) application and a script to calculate the number of days between reboots to my [**Small Things**](https://github.com/jcolag/SmallThings) repository.

For the former, since nothing has happened since [Valence Native](https://github.com/valence-native/valence-native) replaced [Proton Native](https://github.com/kusti8/proton-native), I have decided to go back to evaluating desktop application frameworks.  While I'm still not sold on [Go](https://golang.org/), Fyne isn't bad.

## Library Updates

While buying myself time to figure out the network stack in Haskell, I updated some libraries in [**Bicker**](https://github.com/jcolag/Bicker) and [**RenewDB**](https://github.com/jcolag/RenewDB).

## Next

My plan is to keep working at getting that network connection.  Eventually, *something* has to work.  Other than that, expect me to just making small changes.

Actually, now that I've re-familiarized myself with Rust, this might be a good time to get the [**Common Calendar**](https://github.com/jcolag/CommonCalendar/) back up to date, while I'm trying to figure **Ask INTERN** out.

* * *

**Credits**:  The header image is the [Physical Map of the World, February 2021](https://www.cia.gov/the-world-factbook/static/2ea375ba452947cfe77e5a3d6cd7c1c5/world_phy.pdf) by uncredited Central Intelligence Agency workers, in the public domain as a work of the United States Government.
