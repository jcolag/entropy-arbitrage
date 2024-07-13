---
layout: post
title: Free Culture Book Club — Raiders of the Unix Seas
date: 2024-07-13 07:50:12-0400
categories:
tags: [freeculture, bookclub]
summary: Discussing a command-line game
thumbnail: /blog/assets/black-pearl.png
offset: -20%
teaser: This week sees a Linux- or similar-system-based pirate adventure.
spell: Unix Rampoina Catburglar Aether
proofed: true
---

* Ignore for ToC
{:toc}

This week, our [Free Culture Book Club]({% post_url 2020-05-02-freeculture %}) plays **Raiders of the Unix Seas**.

![The Black Pearl, Classic Edition](/blog/assets/black-pearl.png "Why yes, I DID run ASCII art through software to generate a rasterized image of that art, because the SVG always came out empty...")

To give this series some sense of organization, check out some basic facts without much in the way of context.

 * Full Title:  **Raiders of the Unix Seas**
 * Location:  <https://jamgaroo.xyz/games/2>
 * Released:  2023
 * License:  CC BY
 * Creator:  [Rampoina](https://jamgaroo.xyz/users/Rampoina)
 * Medium:  Programming exercise posing as a game
 * Length:  Probably an hour or two if you know the tools, more if you need to learn along the way
 * Content Advisories:  Nothing that I could find.

This should go without saying---even though I plan to repeat it with every Book Club installment---but *Content Advisories* do not suggest any sort of judgment on my part, only topics that come up in the work that I noticed and might benefit from a particular mood or head space for certain audiences.  I provide it to help you make a decision, rather than a decision in and of itself.

## Raiders of the Unix Seas

The Game Jam entry provides the following blurb.

 > Embark on a thrilling pirate adventure, wielding Unix command line tools to solve puzzles and unearth Blackbeard's legendary treasure.

And while I won't quote the entire thing, the read-me file that kicks off the game has a five-hundred word introduction setting up the game, starting with this.

 > Once upon a time, in a bustling coastal town, rumors circulated of a lost treasure buried deep beneath the ocean's surface. Legend had it that the notorious pirate Captain Blackbeard, before meeting his untimely end, hid his vast riches within the depths of the sea. Many adventurers had tried to uncover the treasure, but none had succeeded.
 >
 > One fateful day, as you wandered through the town's marketplace, you stumbled upon a weathered parchment hanging on a notice board. It was a faded map, believed to be a crucial clue leading to the lost treasure. The map indicated that the sunken ship, the Black Perl, held the key to unimaginable wealth.

That, and the recommendation to read `HELP` and `README` before starting to dig in, should give you an idea of what you have ahead of you.

## What Works Well?

While it comes to a matter of taste, I guess, I do like the format.  As far as I know, other entries in this space have relied on directly locating information, which works, but also doesn't have much to learn.  By contrast, this game plays with a wider variety of tools and functions, which requires a bit more thinking and experimenting.  And unless you spend a lot of time hacking up text on the command line like I have over the years, you'll probably learn something useful.

Several of the puzzles also feel impressively satisfying.  On more than one occasion, the clue gives a tenuous idea of what you need to do, and running through the possibilities almost always produces one clear response that moves things along.  Similarly satisfying, it feels nice to play one of these games that *doesn't* center (but also inexplicably ignore) our lives in a world constantly under surveillance, piecing together clues that people deliberately left behind, instead of using their leaked metadata.

And speaking of things moving along, I can't think of any situations where the game doesn't have at least a couple of next steps.  You might not have a clear idea of *how* to get through a step---arguably the point of the game, in fact---but you probably won't ever find yourself reviewing notes to guess what you need done.

## What Works...Less Well?

{% include lesswell.md %}

I should point out that none of these feels particularly significant, both because they don't heavily impact playing and because somebody could probably fix them with only a few minutes' worth of work.  This makes sense, since it came out of a game jam, much like [**Catburglar**]({% post_url 2024-05-18-catburglar %}).

The game has some inconsistencies at the start.  For example, you want to read `HELP` before `README`, despite something like half a century of tradition saying that you always read `README` before anything, in any situation.  And then `HELP` points you to `STORY`, which...doesn't exist.  Similarly, Blackbeard's ship changes from the *Black Perl* (cute) to the *Black Pearl* to the *Crimson Pearl*, but never the *Queen Anne's Revenge*---see the next paragraph for why I would bring that up---and it doesn't seem to impact anything[^3].

[^3]:  It occurs to me that I may have a particular sensitivity to this specific issue.  I spent the early years of my life in a town with an exaggerated attachment to pirate lore despite little to no actual history of piracy in the area that I've ever heard about.  As such, when I see a cluster of shops with pirate themes, references to real-world pirates relocated in time and context, and changing terminology, it might trigger an unshared desire for all that to make narrative sense, even when it doesn't need to...

The story also seems peculiar, to me, though I admit that it only *needs* to hold together well enough to give the player directions, and the game does that.  Even so, [Edward "Blackbeard" Teach/Thatch](https://en.wikipedia.org/wiki/Blackbeard) really existed, but not in 1987 except maybe as some surviving bones.  But the real Edward Teach *also* probably wouldn't know much about the POSIX-compliant command line.  And while we can all play along with it for the purposes of participating, it feels like a twentieth century pirate inviting people to go on a puzzle-crawl to find their sunken treasure could benefit from more back-story, especially when we accidentally find the map on a notice board and the journal already in our belongings, as if the dead pirate or somebody else chose us.  All of it seems both odd and consistent, which seems to make it fertile ground for that sort of expansion.

Finally, and maybe most significant of these minor issues, I haven't the foggiest idea how to "really" solve two of the puzzles.  Without giving any significant details away, I figured out how the "flashes" needed to pan out accidentally, trying to confirm a wrong answer, but don't have any thoughts on how to get it the right way[^1].  And other than "seems similar"---and because a specific letter-or-digit coincidentally appears in the target file, as I discovered---I don't know how to correctly solve the "boot" puzzle, though it might not have more to it than my guess[^2].

[^1]:  After a quick chat with the author, it looks like my accident let me skip an entire puzzle, which probably also benefited me, because a clue at the "flashes" location leads to a missing clue that *would* have pointed to where my accident led me.  These things happen, especially in game jams.

[^2]:  I overthought that, and the first impulse that feels like a guess does deliberately solve the riddle.

## Opportunities

I don't see any means to contribute, yet, since the game comes packaged as an archive file.

## What's Adaptable?

Primarily, we have the five shops in the market, Captain's Cove Trading Post, Pirate's Booty Bazaar, Seafarer's Delights, Shipshape Supplies, and The Treasure Trove Emporium, along with almost ninety ASCII art images of various artifacts.  We also have some fancy trained fish that spell out convenient messages.

## Next

Coming up next week, we'll start reading **The Aether Age Codex:  Helios**, a themed anthology.  It runs longer than the books that we generally cover, so rather than risking letting it take over the blog for months, we'll cover the early stories over three weeks, starting next week with the first three stories in the book *Phobos*, *Flight of the Ibis*, and *The Bounds of Set*.

{% include fchelp.md %}

Anyway, while we wait for that, what did everybody else think about the game?

* * *

**Credits**:  The header image derives from in-game art, via [Carbon](https://carbon.now.sh/).
