---
layout: post
title: Developer Journal, Day of the Programmer
date: 2021-09-13 07:29:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/25392390163_d6a5321bfb_o.png
offset: -31%
---

* Ignore for ToC
{:toc}

I've never heard of [Day of the Programmer](https://en.wikipedia.org/wiki/Day_of_the_Programmer) before, but I happen to *be* a programmer, and it has a great name.  The date was chosen as the 256<sup>th</sup> (2<sup>8</sup>) day of the year.  In leap years, it's September 12<sup>th</sup>.

![A woman at a small table transferring code from her laptop to her phone](/blog/assets/25392390163_d6a5321bfb_o.png "Large windows don't make these multi-device moments any less tedious.")

And what better way to celebrate Day of the Programmer than to talk about what a programmer---such as myself---has done recently?  Probably a lot, but this is what I have to work with, so that's what you're getting.  Unfortunately, it took forever to dedicate time to the thing that I *wanted* to figure out, so it's mostly random other issues filling the week.

## Miniboost

I updated libraries for [**Miniboost**](https://github.com/jcolag/Miniboost), again.

## Entropy Arbitrage

The [blog's code](https://github.com/jcolag/entropy-arbitrage-code) now has improvements that are entirely invisible to readers and are purely for my benefit.  The deployment notifications that I get are now far clearer.  I have also finally published the script that I run to keep the Internet Archive up to date.

I wanted to add [Archive Today](https://archive.today/) to the script, because I think it has a more usable interface than the [Internet Archive](https://archive.org).  However, they protect every page access with a [CAPTCHA](https://en.wikipedia.org/wiki/CAPTCHA), which...I'd rather not go down the path of paying a shady company to farm out the piece-work to people who only solve these things for hours at a time.

## Quotation Extractor

I don't generally do much with the [**Quotation Extractor**](https://github.com/jcolag/quotation-extractor), but I finally added a script to sift through the generated files and print one random quote.  That includes a character count, since I wanted to use it for Twitter and wanted to be able to rule out quotes that wouldn't fit.

## Fýlakas Onomáton

Because the [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton) pages looked pretty sad, I took the little logo that I whipped up---the letter F, made from a public domain fountain pen image---and turned it into a background image.

## Doritís Onomáton

Well, [**Doritís Onomáton**](https://github.com/jcolag/doritis-onomaton) will now point to <onomaton.club>, the pop-up message for saving a name is now a bit clearer, and---most importantly, and it took most of the week to figure out how to get it to work---the app sends device information along when it requests an activation code.

Along the way, I also bumped the Flutter version.

This now requires testing with a real device---I think that I have a cheap Android tablet handy---but the app and server are both now what I would consider to be "feature complete."

## Next

I should clean up the **Doritís Onomáton** code, but this week will almost certainly otherwise go to cleaning up the library updates that have been backing up.

* * *

**Credits**:  The header image is [wocintech (microsoft) — 42](https://www.flickr.com/photos/wocintechchat/25392390163/in/photostream/) by [WOCinTech Chat](https://www.flickr.com/photos/wocintechchat/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
