---
layout: post
title: Developer Diary, United States Constitution
date: 2024-03-04 07:18:05-0500
categories:
tags: [programming, project, devjournal]
labels: [json-resume, newsletter, notoboto, tcl]
summary: Progress on assorted projects
thumbnail: /blog/assets/us-constitution-signing.png
offset: -15%
teaser: This week's projects include Notoboto, my little JSON Résumé theme, and some miscellaneous housekeeping.
spell: Notoboto sup tcl searchText $widget $searchTerm sel $replaceTerm jsonresume
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the 235<sup>th</sup> anniversary of the [United States Constitution](https://en.wikipedia.org/wiki/Constitution_of_the_United_States) taking effect.  The law had and continues to have some spectacular flaws, but on the whole represented a milestone in the nature of governance that I can't help respecting.  Seriously, strip away that monster of an explanatory comma from the Preamble, and consider the core idea remaining.

 > We the People...do ordain and establish this Constitution for the United States of America

The people---not directly, sadly not everyone, and at the remove of representatives, but not a hereditary elite allegedly chosen by mystical powers, military powers, or the wealthiest---take almost religious authority to define the nature of the country in explicit terms for everybody to see.

![The famous painting showing the signing of the Constitution](/blog/assets/us-constitution-signing.png "Also shown:  Too many flags on the rear wall.")

Anyway, on to the week's projects.

## Miscellaneous

I should mention that the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) will go out tomorrow (Tuesday), for those subscribed on Buy Me a Coffee.  You'll get an inside scoop into what might become an important part of [**The Light's Edge**](https://www.thelightsedge.com/), along with a rundown on the collapse of what I imagined would become a fun Free Culture property, along the lines of my irregular [*Let's Fix...*](/blog/tag/letsfix) posts.

Otherwise, while I never intended to do it, the news that Framework now sells their factory seconds laptop bases for about five hundred dollars---more, after adding memory, storage, network, and so forth---convinced me that I could use a spare or travel laptop.  As such, I've started setting that up.  I'll give the full story in the newsletter for March.

## Notoboto

{% github jcolag/Notoboto %}

The application can now handle menu-based cut-and-paste (as opposed to strictly copy-and-paste), through both the context menu and the top menu.  I didn't care about this all that much, since the difference between "cut" and "copy and delete" doesn't strike me as significant, but for the sake of consistency, it seemed worthwhile.

In addition, I'd call it an early stages feature, but the program can also handle find-and-replace.  For now, it only works on a single instance of the text per run, so the user will need to repeatedly click *Replace* to change an entire note.  However, that lays out the broad logic, like so.

```tcl
searchText $widget $searchTerm
if {[$widget tag ranges sel] != ""} {
  $widget delete sel.first {sel.last + 1 char}
  $widget insert [$widget index insert] $replaceTerm
}
```

This uses the already-present search feature.  If the search found a match, then it replaces the selected text.  At some point, I can loop this for the entire file.

Finally, I don't know when I'll get to the feature, but I have added one Material Design icon for searching across notes, and another to slot in to represent the replacement action.

## Thorough (JSON Resume Theme)

{% github jcolag/jsonresume-theme-thorough %}

I have neglected this little project for a long while, but I recently noticed---or maybe I already knew and noticed it anew---that pages after the first don't have any margins.  I needed to undertake a bit of research to fix that, but the [`@page` CSS rule](https://developer.mozilla.org/en-US/docs/Web/CSS/@page) does allow `margin-top` and `margin-bottom`.

Unfortunately, this took me longer to make work than I expected, because I *also* tried to add a page number with `@top-right`.  Unfortunately, whatever JSON Resume uses to generate the output doesn't seem to recognize the rule, silently counts it as an error, and fouls up the margins in the same `@page` rule.

## Next

I see them building up again, so I'll probably handle the outdated libraries that GitHub has tried to warn me about recently.

* * *

**Credits**:  The header image is [Scene at the Signing of the Constitution of the United States](https://www.aoc.gov/explore-capitol-campus/art/signing-constitution) by Howard Chandler Christy, long in the public domain due to an expired copyright and/or as a work of the United States government.
