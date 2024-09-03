---
layout: post
title: Announcing...Iungimoji
date: 2022-03-06 07:09:12-0500
categories:
tags: [announcement, puzzle]
summary: A second daily puzzle
thumbnail: /blog/assets/iungimoji.png
offset: -13%
proofed: true
---

* Ignore for ToC
{:toc}

![An Iungimoji game in progress](/blog/assets/iungimoji.png "Stage 2:  Force the player to write a story based on the emoji and the order they were revealed?")

Sour grapes:  Admittedly, I have no interest in jumping on the [Wordle](https://en.wikipedia.org/wiki/Wordle) bandwagon, even though I *did* do it with my [Daily Nonogram]({% post_url 2021-02-21-nonogram %}) before anybody had ever considered playing [Bulls and Cows](https://en.wikipedia.org/wiki/Bulls_and_Cows)---or whatever your local version might be---with words[^1].  I'm exaggerating for effect, of course.  Josh Wardle seems to be a nice guy who did a clever thing well-designed to become popular, and deserves the rewards that he's received.  It's a far cry from my approach of dumping out something with no feedback, mentioning it on my blog, and basically just tinkering with it for my use.

Today, all of that...well, it doesn't actually change at all.  But I *am* releasing a [Daily 4x4 Pair-Matching Game](/iuengimoji), which I call **Iungimoji**, after the Latin verb "I connect/pair."  Oh, and it's also named for "emoji," obviously.  Latin verb conjugations can be irregular, but certainly not irregular enough to use the letter *j* centuries before it was added to anybody's alphabet.

As with the nonogram, I wrote this primarily for my use, so there's no state-tracking work.  There's no work to prevent the player from cheating.  There isn't even a string of {% emoji green_salad %}{% emoji green_square %}{% emoji yellow_square %}{% emoji purple_circle %}{% emoji green_square %} emoji or whatever to flood every marginal online social space that you can find.  However, if you follow the [developer diary posts](/blog/tag/devjournal), you already know that there *is* [source code](https://github.com/jcolag/iungimoji) available.  The code currently generates square puzzles of any size, with odd-sizes getting a dumb-looking extra card to flip over.  It wouldn't take much work to separate a width and height, or to limit it to an even number of cells.  I just didn't bother, since I mostly planned to play 4x4 and 6x6 puzzles.

Like the **Daily Nonogram**, the **Daily Iungimoji** updates a bit after midnight.  Unlike the **Daily Nonogram**, the infrastructure for archiving old puzzles already exists, instead of me patching it in weeks later, so you can see and play the past couple of weeks that I have generated for myself as a proof of concept.

And as a word of warning, there might be a third puzzle game coming.  I like these as a start to my day.

And who knows?  Maybe someday, I'll revisit the code and have them save progress to your browser and generate some emoji strings to alienate your friends.  Or I could combine all the pandemic obsessions and have a daily game that mints an emoji NFT of sourdough bread when you win.  Note to investors:  I'm joking, but for a large enough sack of cash, I'll absolutely build a dystopian business that's guaranteed to fail once the fads have been forgotten...

* * *

**Credits**:  The header image is a screenshot from the game.

[^1]: OK, that's definitely a lie, since [Jotto](https://en.wikipedia.org/wiki/Jotto) is definitely something near two-thirds of a century old, which predates *anything* that I have ever done...
