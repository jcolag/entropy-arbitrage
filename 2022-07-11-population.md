---
layout: post
title: Developer Journal, World Population Day
date: 2022-07-11 06:47:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/music-black-and-white-people-crowd-concert-audience-874486-pxhere.com.png
proofed: true
---

* Ignore for ToC
{:toc}

Today marks [World Population Day](https://en.wikipedia.org/wiki/World_Population_Day).  I've already written about how concerns about overpopulation invariably tie to bigotry, though this day traffics more in the concerns about the concrete problems causing and resulting from a growing population, such as family planning and human rights.

![A large crowd seated at a theater, photographed from behind](/blog/assets/music-black-and-white-people-crowd-concert-audience-874486-pxhere.com.png "Notice how nobody complains when the population density comes from people paying top-dollar for cramped seats.")

In a lot of ways, though not in the important way of making it explicit, the day stands *against* the eugenics-based worries about (frankly) brown people overwhelming the part of the world that likes to think of itself as "civilized" despite enslaving the parts of the world where the brown people live.

On to the code.

## Mystic T-Square

{% github jcolag/mystic-t-square %}

By now, if you follow along with this project---not that I'd expect anybody to do so---you have probably pieced together at least two of the clues from last week.  In reverse order, we have the following.

 * The HTML currently has a familiar-looking layout, also potentially relating to the **T** in the name.
   * ✔ **The game uses tic-tac-toe as its base model.**
 * The JavaScript code does something specific on loading the page, which seems unrelated to the other items, but might explain the **T**.
   * ✔ **Rather than alternating players, the game decides how to mark a square based on a trivia question.**
 * You might recognize the name mystic square, in relation to puzzles and games.
   * ❓ Not yet implemented/revealed.

At this point, then, you can play a solitaire version of [Hollywood Squares](https://en.wikipedia.org/wiki/Hollywood_Squares), essentially, though I don't particularly love that game.  Choose a square by clicking on it.  Answer a random trivia question.  Get an **O** (or 🙆) if you guess correctly or an **X** (or 🙅) if you guess incorrectly.  Continue until either **X** or **O** wins the game.

![A Mystic T-Square game with no winner](/blog/assets/mystic-t-square-demo.png "The only way to win is not to play?  No, wait, that makes a decent tagline for a movie, but a TERRIBLE tagline for a game.")

The game even---maybe primitively, but I couldn't think of a simpler process than checking for the eight target states---checks to see if one side has won the game.

Why does **O** represent a correct answer?  The gesture emoji include 🙆 "OK" and 🙅 "No," which happen to resemble the letters from Tic-Tac-Toe.  And I prefer the emoji, because I can randomly change the race and gender of the character, to give the game a more complex appearance with only a couple of lines of code.  For consistency, then, "No" represents a wrong answer, even though most Tic-Tac-Toe players might assume that, visually, it should mark a correct answer.

### A Note on *Trivial* Matters

Building this game has made me realize something that I probably should have understood at an early age:  Answering trivia questions carries no enjoyment, because---excepting cases where you can narrow down the range of answers based on other information---you either already know an answer or you don't.  And you might know an answer based on prior education or exposure...or you might have merely seen the question before.

The exposure aspect brings me to my central point:  Trivia relies on and revolves around exclusion, something that I should have learned a long time ago.

Allow me to explain using myself as an example.  While I don't know the actual metrics, the video game category appears to make up a large fraction of the [Open Trivia Database](https://opentdb.com/)'s questions.  Almost every question requires the answerer to have played the game---invariably a title from one of the major game studios---or to follow video game industry news for the questions to have meaning.  Since I do neither, they may as well have written the questions in code.  I don't know if **Splatter McGinty-Alvarez XIV, Pugilist for Hire:  The Quest for the Anointed Ointment Appointments** exists (well, OK, in this case, I can guess, because I made it up for this example), let alone the name of the love interest, the development project's code name at the studio, or how many units it sold on its first day of release.

The "fun" of trivia games, if we can call it that, seems to come more from seeing an opponent as "worse," than it does from the game bringing any satisfaction.  This makes it an interesting outlier, because other games frequently make entertaining solo activities.  That doesn't work for trivia, though.

In any case, I'll continue to *use* the trivia conceit, because I only want to provide a way that players can win or lose a single-player Tic-Tac-Toe game, without resorting to sabotage or making random choices on the player's behalf.  In other words, something impartial---the database API---chooses the questions and their ordering, and that order *might* spoil an easy win, but it also might not, depending on the player.

## Next

As you might guess, **Mystic T-Square** needs its final big feature developed.  Primarily, this means adding the final feature that turns this into the game that I imagined.

And because the game starts with a web request to retrieve the trivia questions, it probably needs a "loading" modal panel to make clear that the player needs to wait for that request to complete.  More than once, I've loaded the game to test and wondered what prevented the page from responding to my clicks.  Time permitting, the game may begin storing information on the browser, such as OTDb's session token, which would reduce the chances of repeated questions. 

Oh, and speaking of time, it might make sense to limit how long a player has to answer the trivia questions.  Researching the answers would obviously make the game much easier to win.

Of course, I also need to get back to **Salavi**, and I have notifications of libraries to update piling up, too.

* * *

**Credits**:  The header image is [untitled](https://pxhere.com/en/photo/874486) by an uncredited PxHere photographer, released under the terms of the [Creative Commons CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
