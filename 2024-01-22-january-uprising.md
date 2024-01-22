---
layout: post
title: Developer Diary, January Uprising
date: 2024-01-22 07:21:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Jan-Matejko-Polonia-1863-Poland-Enchained-MNK-XII-453-National-Museum-Kraków.png
offset: -15%
teaser: This week's projects begin and end with Notoboto, mostly.  If you want to hear about searching in Tcl/Tk, then I guess that I wrote this for you.
spell: Polonia Matejko Notoboto
proofed: true
---

Today marks the 161<sup>st</sup> anniversary of the start of Poland's [January Uprising](https://en.wikipedia.org/wiki/January_Uprising) against the Russian occupation.  It didn't completely succeed, in that the Russian Empire continued to occupy the region---the Kingdom of Poland would get handed over to Germany in 1915, and finally regain its independence in 1918---but it connected a lot of society and still influences the region's culture.

![The 1863 painting "Poland Enchained"](/blog/assets/Jan-Matejko-Polonia-1863-Poland-Enchained-MNK-XII-453-National-Museum-Kraków.png "The poster in the background looks like a prop from Doctor Who so that the characters can gasp at their new locale...")

Nothing in this batch that I can remember, but a couple of my projects may have actually taken some inspiration from what I might call a disproportionately large number of Polish colleagues---you know if I mean you, I suppose, if you ever read this---so...

## Notoboto

{% github jcolag/Notoboto %}

I believe that most of my time---well, time for projects, at least---went to improving **Notoboto**'s search capabilities.  It now tracks the search location properly, always starting from the caret location (the logical position in the document of the cursor image) unless the document has no caret.  Briefly, I had wasted a bit of time trying to maintain an explicit position state, but that required updates whenever I moved to a different spot in the note, which made no sense.

Beyond searching, I also added syntax highlighting rules for over-strike text.  I don't use it much in my notes, but it made sense to support as much of the "standard" as I can.  And you never know when I'll want to fake redacting ~~a snotty comment~~ obsolete ideas.

## Next

Now that I think that **Notoboto**'s core search functionality works as expected, I'll probably want to dress it up a bit.  I'd like to have the typical three options of searching case-sensitive, whole-word, and by arbitrary regular expression.  Wrapping the search to the beginning, if it can't find another instance of the search text, would also improve things.

If that goes well, I might also look at replacing search results, for a full search-and-replace feature, and maybe searching across notes.

* * *

**Credits**:  The header image is [Polonia 1863 (Poland Enchained)](https://zbiory.mnk.pl/en/search-result/advance/catalog/325087) by Jan Matejko, long in the public domain due to expired copyright.
