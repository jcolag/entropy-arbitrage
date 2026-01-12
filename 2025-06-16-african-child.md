---
layout: post
title: Developer Diary, Day of the African Child
date: 2025-06-16 07:19:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [codidact, library-update, stenotype]
summary: Progress on assorted projects
thumbnail: /blog/assets/Fally-Ipupa-joins-MONUSCO.png
offset: -30%
description: This week's projects include stenotype corner, a Codidact answer, and another batch of library updates.
spell: stenotype Typey Chording KPA CamelCase WASD uLauncher Codidact Fýlakas Onomáton Fally Ipupa MONUSCO Bompengo
proofed: true
---

* Ignore for ToC
{:toc}

Though it sounds a bit like a 1950s science fiction flick, today marks the [International Day of the African Child](https://en.wikipedia.org/wiki/International_Day_of_the_African_Child), primarily honoring the participants in the [Soweto Uprising](https://en.wikipedia.org/wiki/Soweto_uprising), but also agitating for improved education across Africa.

I should note that Soweto happened to oppose the South African government imposing cultural requirements---language of instruction, in this case---in schools, already segregated in a culture steeped in apartheid.  Not that I have [any reason](https://www.whitehouse.gov/presidential-actions/2025/01/ending-radical-indoctrination-in-k-12-schooling/) for bringing that up in 2025 or in the United States...

![Musician Fally Ipupa holds a round sign asserting that recruiting children (for armed conflict) violates the law](/blog/assets/Fally-Ipupa-joins-MONUSCO.png "Not currently an African child, but he was...")

On to the week's projects.

## Stenotype Corner

First, I should mention that I finished [**Art of Chording**](https://www.artofchording.com/). I don't know if I'd *strongly* recommend it, but it covered much of what I needed to start after the long introduction, and I actually typed most of this section using stenotype, looking up new words as I went. I'd call that a decent "proof of concept."

In its place, I started reading the apparently non-Free Culture [**Learn Plover**](https://www.openstenoproject.org/learn-plover/lesson-3-english-sounds.html). I don't find it as engaging as the other, but maybe I'll get something out of it.

Next, I managed to start and wrap up the sixth Typey Type drill, *One Syllable Words with Short-I Vowel*, in... more runs than I'd like to admit. But I did get through it, and moved on to *One Syllable Words with Short Vowels*, where I have plodded along fairly slowly, again.

Since I took another speed hit---and I don't really know why, given that this lesson doesn't introduce any new words that I've noticed---I decided to compound it by turning off the keyboard hints.  Especially if I felt tired or unfocused, I noticed that I'd try to split my attention between the fingering diagram and the word to type, which probably caused me to rely on the hints longer than I should have in exercises, especially when I've started typing (some) of my usual work, where I don't have any hints. We'll see if that helps. Or rather, it definitely will in the long term, but we'll see if it does anything for me in the next few weeks.

### Extracurricular Finds

As I've started to use the stenography keyboard in real situations, such as these posts, I've also needed to track down some other briefs that don't show up in any of the major literature, so I wanted to document them here. We can start with capitalization.

{% steno KPA* %}

This ("cap," but all on the left hand) sets the keyboard to capitalize the next word and suppress the space between the words. It works for starting paragraphs or adding a sentence in after the fact and for, say, CamelCase words...

Without the star, it capitalizes the next word, but includes/retains the space.

{% steno TK-LS %}

Then, this TK-LS brief only suppresses the space[^1]. I needed this, in referring to Jellyfin, my media server of choice, which that lets me type the name as gel-ly-(suppress)-fin.

[^1]:  It took me a while to work out that TK-LS probably abbreviates something like "delete space," since {% key T %}{% key K %} represents a /d/ sound.  That gives something like D-L S.

### Dictionary Work

In addition to learning, I also started customizing the Plover system to help me along.  Most of it centers on the blog, such as a stroke to create the template for a Markdown link---`[]()`---or insert one of the more-common plugins instead of working out how to insert curly braces.  But with some help from the [Plover wiki](https://plover.wiki/index.php/Dictionary_format), I also created little commands to issue {% key CTRL %}-{% key S %} to save in most programs can, one to force the next word to lowercase (opposite to the capitalize brief, above), some to enhance the [WASD](https://en.wikipedia.org/wiki/Arrow_keys#WASD_keys)-like cursor movement, and one to open that uLauncher program that I think I probably mentioned last time, giving me an extra route to practice. Oh, and one for my family name (Colagioia), mostly as a test, but which I certainly don't want to finger-spell every time that it comes up...

I'll probably publish my user dictionary at some point, in case anybody finds something useful in there, but mostly so that I always have a backup.  Maybe it'll go in my [**Periodic Scripts**](https://github.com/jcolag/periodic-scripts) repository, the closest I have to a dumping ground of configuration files.

## Codidact

It doesn't amount to much, but I supplied at least the kernel of a possible answer to [What makes a riddle both poetic and clever?](https://writing.codidact.com/posts/294121#answer-294145).

## Library Updates

Continuing from last week, I needed to about bump library versions for [**Bicker**](https://github.com/jcolag/Bicker), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Renewal Database**](https://github.com/jcolag/RenewDB).

## Next

I may continue to clear up the backlog of pull requests, or---as I've mentioned---some new projects could plausibly show up, maybe even a project that a person might find useful instead of my usual nonsense...maybe.

* * *

**Credits**:  The header image is [Fally Ipupa joins MONUSCO to fight against the recruitment of children](https://www.flickr.com/photos/monusco/27925850607/) by John Bompengo for [MONUSCO Photos](https://www.flickr.com/photos/monusco/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) license.
