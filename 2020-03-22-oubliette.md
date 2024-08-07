---
layout: post
title: Open Oubliette
date: 2020-03-22 06:59:12-0400
categories:
tags: [boardgame, announcement, creativecommons]
summary: An attempt at a Free Culture board game
thumbnail: /blog/assets/wood-white-play-food-color-community-730015-pxhere.com.jpg
---

* Ignore for ToC
{:toc}

One of my long-term projects that I never seem to actually get around to touching is to resurrect Elizabeth Magie's [**The Landlord's Game**](https://en.wikipedia.org/wiki/The_Landlord's_Game), the forerunner of [**Monopoly**](https://en.wikipedia.org/wiki/Monopoly_(game)) that was designed to contrast unregulated markets with [Georgism](https://en.wikipedia.org/wiki/Georgism), a proposed economic system where everybody is taxed for sitting on resources (primarily land, because this is an old idea), rather than taxing income or spending, to discourage centralized ownership of resources by making it too expensive to resell or rent unused resources.

![Game pieces](/blog/assets/wood-white-play-food-color-community-730015-pxhere.com.jpg "Game pieces")

While I wouldn't be surprised if **The Landlord's Game** or Henry George's ideas showed up, someday, this isn't a post about any of that.

One of the projects *related* to the game is imagining what a modern **Landlord**-like game might look like with additional subsystems, especially the stranger systems people use as house rules.  For example, favorite addition to **Monopoly** in some circles is to replace the jail (where a player is sidelined for some length of time, which isn't any fun) with a roleplaying-like dungeon crawl, often using TSR's [**Dungeon!**](https://en.wikipedia.org/wiki/Dungeon!) board game.

While I appreciate the broad concept, I don't like the implementation of the idea for a few reasons.

 * It's relatively hard to find a copy of **Dungeon!** and probably not worth the trouble in general, so very few people would even recognize the game, let alone having the ability to play it.
 * **Dungeon!** has a very large board, making it inconvenient and unwieldy to use for an uncommon occurrence like Jail.
 * The **Dungeon!** rules are fairly complicated and meant to serve as a sort of simplified "Dungeon Master," instead of blending quietly into a host game.
 * While I can justify thinking about **Monopoly** as preparation for an eventual return of **The Landlord's Game** (long fallen into the public domain), there is no Free Culture equivalent of **Dungeon!**.

Of course, I can solve problems like that, if I want.  So, exit **Dungeon!** and enter...**Open Oubliette**!  Errr...The latter exclamation point is part of the exclamation, not the game's name.

## Open Oubliette Overview

An [*oubliette*](https://en.wiktionary.org/wiki/oubliette) (from the French, "to forget"), is a kind of dungeon that is only accessible through a single trapdoor in the ceiling.  The name isn't terrible and it justifies the idea that the Jail square has an entire dungeon "underneath" it.

What I think I want out of the game is something where we get the combat/treasure/event flow of a fantasy roleplaying game, but without the time spent making strategy decisions or resolving rules.  It should also be set up in such a way that, if **Open Oubliette** (or just **Oubliette**, informally) is used as part of another game, there should be an easy "checkpoint" that can be used as a winning condition.

I suspect that I can solve the first problem by simplifying fights to one "round" and using cards to define the outcomes.  And of course, the game will be licensed [CC-BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/).  That only seems right.

Since a Jail sentence is (a maximum of) three turns, we presumably want to solve the second problem with some goal that *can* be reached, but might not be, so that the time spent in the Oubliette might not be useful.  If we assume that each roll (just like the main game) involves adding the values on two six-sided dice, that means we want something that takes somewhere in the neighborhood of twenty-one (three, times the most likely roll of seven) spaces.  For the prototype, that'll be twenty spaces (spaces along the perimeter of a six-by-six square), where one square---the Entrance or Exit space---might be considered "inside" or "beneath" the jail of another game.

And we'll need space for cards, so this gives a board that (in the abstract) might look a little bit like the following.

![An example Open Oubliette board](/blog/assets/oubliette-board.png "An example Open Oubliette board")

And broadly, we want a fight over treasure with occasional complications that should be at least somewhat interesting.  That should give us a basic process.  On each player's turn, the player will:

 * Roll the dice.
 * Move the number of spaces equal to the sum of both dice.
 * Draw a *Monster* card.
 * Fight the monster on their card; see below for those rules.
 * If the fight is successful, draw a *Treasure* card.
 * If the player has landed on one of the corner spaces, draw and apply an *Event* card.
 * If the player rolled doubles in the first step, take another turn.

Fighting the monsters, of course, would have its own rules.  As mentioned, this should be reduced to just one attempt, rather than a back-and-forth until someone loses.

### Combat

The basic flow of a fight follows.

 * The player attacks, rolling the dice.
 * If the player rolls a number equal to monster's power level or higher, the player wins and the process is over.
 * If the player rolls less than the monster's power level, the monster rolls the dice to retaliate.
 * If the monster's roll is equal to eight (8) or higher, the monster succeeds and the player draws a *Wound* card.
 * If the monster's roll is less than eight (8), the monster's attack fails and the monster leaves with its treasure.

Combat ends here, regardless of the conditions.  That was about as simple as I could get it.

However, some Treasure cards---armor or weapons---give the player who holds them the ability to change the player's attack or defense.  Use of the card means that it no longer qualifies as Treasure for the remainder of the game.

If a Treasure card improves the attack, it's a weapon, so add its value to the to the sum of the dice when attacking.  If the Treasure card improves the defense, it's armor, so add its value to the standard defense (8) whenever a monster attacks the player.

Similarly, *Wound* cards make fighting more difficult.  The sum of a player's two highest *Wound* cards is added to the power level of every monster the player attacks and added to the roll of any monster attacking the player.  Being hurt makes it harder to attack and easier to get hit.

If a player lands on a space where another player is already waiting, the arriving player can opt to attack the other before interacting with a monster with the same rules.  The player winning the fight takes three (3) random *Treasure* cards from the loser, but the attacker will always draw a *Wound* card to represent damage taken in the ambush.  Because of the risks, the arriving player can also choose to not attack.

### The Exit

Whenever a player lands on or passes the *Exit* space, the player can opt to take a couple of actions that end the turn.

 * **Recovery**:  The player places up to three of their current *Wound* cards back in the pile, essentially resting to recover.
 * **Treasure**:  All the player's *Treasure* cards that haven't been used for their functionality as weapons or armor are cashed in for their face value.  Treasure that has been cashed in cannot be stolen by other players.

If the player lands on the *Exit* space, the player also gains the ability to move in either direction, deciding the direction after their roll.

### Win Conditions

The game is over when one of the two following conditions is met.

First, the first player to cash in a total of $6,000 in *Treasure* cards at the *Exit* automatically wins the game.

Second, in cases where **Oubliette** runs out of unclaimed *Treasure* cards or where there is a tie in the previous case, the player who has the highest value from cashed-in *Treasure* cards wins the game.

In the event of a tie in the second case, *Treasure* cards that have **not** been cashed in, excluding those being used for weapons or armor, can count towards the total for the purpose of breaking the tie.

If the score is **still** even, *Treasure* cards used as weapons and armor can count.

### Landlord's Game Rules

If using **Oubliette** in place of the Jail in **The Landlord's Game** (or **Monopoly**), make the following changes to game play:

 * The player only has three Turns, taken instead of their **Landlord's Game** turns waiting in Jail; no business may be transacted from the oubliette.
 * Any *Treasure* cards that haven't been cashed in at the *Exit* by the end of three turns are lost.
 * Any *Treasure* cards that **have** been cashed in are converted to money in the host game at the rate of g10 to $1...€1, 元1, or whatever.
 * There is no Win Condition.  After three Turns, the player leaves the oubliette and returns all **Oubliette** cards to their appropriate decks.

In all other cases, the rules are the same.

## Cards

Of course, we need those cards, presumably thirty-two of each type.  My thinking is that the monsters might be something like this, pushing for some cultural pluralism.

|Power|Monster|Description|
|-----|-------|-----------|
|1|[Squasc](https://en.wikipedia.org/wiki/Squasc)|small, hairy, tawny, similar to a squirrel without tail, but with an anthropomorphic face|
|2|[Pukwudgie](https://en.wikipedia.org/wiki/Pukwudgie)|kidnap people, push them off cliffs, attack with short knives/spears, use sand to blind|
|3|[Manaia](https://en.wikipedia.org/wiki/Manaia_(mythological_creature))|head of a bird and the tail of a fish and the body of a man|
|4|[Ogre](https://en.wikipedia.org/wiki/Ogre)|large, hideous, man-like being that eats ordinary human beings|
|5|[Yeti](https://en.wikipedia.org/wiki/Yeti)|ape-like creature taller than an average human|
|6|[Rompo](https://en.wikipedia.org/wiki/Rompo)|head of a hare, human ears, a skeleton body, the arms of a badger, and legs of a bear|
|7|[Mo'o](https://en.wikipedia.org/wiki/Mo%CA%BBo)|forms of monstrous reptiles, tiny geckos, and humans|
|8|[Manticore](https://en.wikipedia.org/wiki/Manticore)|the head of a human, body of a lion and a tail of venomous spines similar to porcupine quills|
|9|[Anchimallén](https://en.wikipedia.org/wiki/Anchimayen)|undead children, can transform into flying fireballs|
|10|[Dragon](https://en.wikipedia.org/wiki/Dragon)|winged, horned, four-legged, and capable of breathing fire|
|1|Squasc| |
|2|Pukwudgie| |
|3|Manaia| |
|4|Ogre| |
|5|Yeti| |
|6|Rompo| |
|7|Mo'o| |
|8|Manticore| |
|9|Anchimallén| |
|10|Dragon| |
|1|Squasc| |
|2|Pukwudgie| |
|3|Manaia| |
|4|Ogre| |
|5|Yeti| |
|6|Rompo| |
|7|Mo'o| |
|8|Manticore| |
|9|Anchimallén| |
|10|Dragon| |
|3|Manaia| |
|7|Mo'o| |

And the treasures.

|#|Value(g)|Description|Utility|
|-|--------|-----------|-------|
|1|200|Pottery Shards|--|
|2|300|Knife|+1 to Attacks|
|3|300|Pottery|--|
|4|400|Opal Ring|--|
|5|400|Leather Armor|+1 to Defense|
|6|400|Ruby Ring|--|
|7|500|Diamond Ring|--|
|8|500|Dagger|+2 to Attacks|
|9|500|Accounting Records|--|
|10|600|Maps|--|
|11|600|Ring Mail Armor|+2 to Defense|
|12|600|Poetry|--|
|13|600|Flute|--|
|14|700|Club|+3 to Attacks|
|15|700|Opal Bracelet|--|
|16|700|Ruby Bracelet|--|
|17|700|Chain Mail Armor|+3 to Defense|
|18|700|Diamond Bracelet|--|
|19|800|Animal Figurines|--|
|20|800|Mace|+4 to Attacks|
|21|800|Human Figurines|--|
|22|800|Harp|--|
|23|900|Splint Mail Armor|+4 to Defense|
|24|900|Opal Necklace|--|
|25|900|Ruby Necklace|--|
|26|900|Flail|+5 to Attacks|
|27|1000|Diamond Necklace|--|
|28|1000|Banded Mail Armor|+5 to Defense|
|29|1000|Tiara|--|
|30|1100|Glowing Sword|+6 to Attacks|
|31|1100|Crown|--|
|32|1200|Plate Mail Armor|+6 to Defense|

And the events.

|#|Title|Description|
|-|-----|-----------|
|1|Secret|Roll one die. If the result is 5 or higher, collect three (3) Treasure cards.|
|2|Secret|Roll one die. If the result is 4 or higher, collect two (2) Treasure cards.|
|3|Shortcut|This card may be kept until needed. Return to the Exit square immediately.|
|4|Shortcut|This card may be kept until needed. Return to the Exit square immediately.|
|5|Tunnel|Move four (4) squares ahead.|
|6|Tunnel|Move four (4) squares back.|
|7|Spelunk|Roll again!|
|8|Spelunk|Roll again!|
|9|Spelunk|Roll again!|
|10|Spelunk|Roll again!|
|11|Cave-In|Lose a turn.|
|12|Cave-In|Lose a turn.|
|13|Trap|Roll one die. If the result is 2 or less, lose a turn and this square's Treasure card.|
|14|Healing Waters|This card may be kept until needed. Return the most severe _Wound_ card without returning to the Exit square.|
|15|Healing Waters|This card may be kept until needed. Return the most severe _Wound_ card without returning to the Exit square.|
|16|Healing Waters|This card may be kept until needed. Return the two most severe _Wound_ cards without returning to the Exit square.|
|17|Dragon Hoard|Fight a dragon. If successful, roll one die and take three (3) more than the number rolled Treasure cards.|
|18|Skeleton|Take three Treasure cards from this unfortunate explorer.|
|19|Pin Cushion|Take three Treasure cards from this unfortunate explorer.|
|20|Ambush|Roll both dice. If the result is greater than your defense score, an unknown explorer has taken three (3) Treasure cards from you.|
|21|Quest|If you defeat a Manticore before returning to the Exit square or have defeated one since leaving the Exit square, receive three (3) Treasure cards on arriving at the Exit square.|
|22|Quest|If you defeat a Rompo before returning to the Exit square or have defeated one since leaving the Exit square, receive two (2) Treasure cards on arriving at the Exit square.|
|23|Quest|If you defeat an Ogre before returning to the Exit square or have defeated one since leaving the Exit square, receive one (1) Treasure card on arriving at the Exit square.|
|24|Rage|This card may be kept until needed. In a fight, add four (4) to an attack against a monster.|
|25|Level Up|Until leaving the Oubliette, all monsters have +1 power. On leaving, all Treasure cards are worth +100 gold|
|26|Level Up|Until leaving the Oubliette, all monsters have +1 power. On leaving, all Treasure cards are worth +100 gold|
|27|Level Up|Until leaving the Oubliette, all monsters have +1 power. On leaving, all Treasure cards are worth +100 gold|
|28|Recovery!|This card may be kept until needed. Reroll a failed attack or force a monster to reroll.|
|29|Recovery!|This card may be kept until needed. Reroll a failed attack or force a monster to reroll.|
|30|Dodge|This card may be kept until needed. Add three (3) to your defense value.|
|31|Revenge|This card may be kept until needed. If a monster wounds you, you may attack it again.|
|32|Revenge|This card may be kept until needed. If a monster wounds you, you may attack it again.|

And the wounds.

|#|Title|Modifier|
|-|-----|--------|
|1|Merely a Scratch|0|
|2|Close Call|0|
|3|Ugly Bruise|0|
|4|Cramp!|0|
|5|Close Shave|0|
|6|That Hurt!|0|
|7|Only a Flesh Wound|1|
|8|Bleeding|1|
|9|Soft Tissue Injury|1|
|10|Crushed|1|
|11|Broken Leg|2|
|12|Broken Arm|2|
|13|Concussion|2|
|14|Stabbed|3|
|15|Avulsion|3|
|16|Critical!|4|
|17|Merely a Scratch|0|
|18|Close Call|0|
|19|Ugly Bruise|0|
|20|Cramp!|0|
|21|Close Shave|0|
|22|That Hurt!|0|
|23|Only a Flesh Wound|1|
|24|Bleeding|1|
|25|Soft Tissue Injury|1|
|26|Crushed|1|
|27|Broken Leg|2|
|28|Broken Arm|2|
|29|Concussion|2|
|30|Stabbed|3|
|31|Avulsion|3|
|32|Critical!|4|

## Play!

If you'd like to give **Open Oubliette** a try, you'll need to supply your own dice (or random-number generator) and playing tokens, but I'd love to hear how it went!  My own tests seemed reasonable, but I also don't play a lot of games, so it might be terrible.

It's certainly not *perfect*, by any means---I'd especially like additional monsters to replace the duplicates without digging into the same sources of folklore, so feel free to make recommendations with links---but like I said, it seems to play reasonably well and improvement is why it's Free Culture!  Share your experiences and/or issue pull requests at the game repository, which will be at <https://github.com/jcolag/BoardGames> by...let's say Wednesday morning.

#### <i class="fas fa-dice"></i>

* * *

**Credits**:  The header image is [untitled](https://pxhere.com/en/photo/730015) by an anonymous [PxHere](https://pxhere.com/) photographer and is made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
