---
layout: post
title: Developer Journal, Independence Day
date: 2022-07-04 07:32:05-0400
categories:
tags: [programming, project, devjournal]
labels: [library-update, mystic-t-square]
summary: Progress on assorted projects
thumbnail: /blog/assets/American-1902-Fourth-of-July-fireworks.png
proofed: true
---

* Ignore for ToC
{:toc}

Today celebrates [Independence Day](https://en.wikipedia.org/wiki/Independence_Day_%28United_States%29) in the United States, maybe explaining why much of the business world goes dark.  Coincidentally [Abkhazia](https://en.wikipedia.org/wiki/Abkhazia), the [Northern Mariana Islands](https://en.wikipedia.org/wiki/Northern_Mariana_Islands), [Rwanda](https://en.wikipedia.org/wiki/Rwanda), and the [Philippines](https://en.wikipedia.org/wiki/Philippines) all celebrate similar holidays.  You find a variety of national celebrations, this time of year; I have no proof, but I *suspect* that they might all trace to some ancient solstice celebration involving color and fire---translating to fireworks---plus parades.

![Children of various ethnicities from around the United States and then-territories celebrate Independence Day outside the Capitol, next to Uncle Sam and Columbia](/blog/assets/American-1902-Fourth-of-July-fireworks.png "I don't know if the Filipino kid mortifies me or impresses me.")

It seems unlikely, after all, that so many countries (and would-be countries) celebrate their identity so near to the start of summer.

That said, given the Supreme Court's absolute rampage over the last couple of weeks, I imagine that many American readers might feel somewhat less than fully patriotic.  For those of us in that state, while I mentioned it last year around this time, I encourage you listen to a reading of [What to the Slave Is the Fourth of July?](https://en.wikipedia.org/wiki/What_to_the_Slave_Is_the_Fourth_of_July%3F) by Frederick Douglass.

<iframe
  allowfullscreen
  frameborder="0"
  height="36"
  mozallowfullscreen="true"
  src="https://archive.org/embed/nonfiction037_1503_librivox/snf037_whattotheslavejulyfourth_douglass_pga_128kb.mp3"
  webkitallowfullscreen="true"
  width="740"
>
</iframe>

It makes some insensitive comments, but take an hour out of your holiday to come to terms with the fact that this country once stripped millions of people of all rights, yet expected them to celebrate that country's founding.  Celebrate the ideals---which we *will* bring back, just as they did---not the current state of affairs.  Try one sample:

 > Standing with God and the crushed and bleeding slave on this occasion, I will, in the name of humanity which is outraged, in the name of liberty which is fettered, in the name of the Constitution and the Bible, which are disregarded and trampled upon, dare to call in question and to denounce, with all the emphasis I can command, everything that serves to perpetuate slavery---the great sin and shame of America! "I will not equivocate; I will not excuse;" I will use the severest language I can command; and yet not one word shall escape me that any man, whose judgement is not blinded by prejudice, or who is not at heart a slaveholder, shall not confess to be right and just.

Or try this:

 > The existence of slavery in this country brands your republicanism as a sham, your humanity as a base pretence, and your Christianity as a lie. It destroys your moral power abroad; it corrupts your politicians at home. It saps the foundation of religion; it makes your name a hissing, and a by word to a mocking earth. It is the antagonistic force in your government, the only thing that seriously disturbs and endangers your Union. It fetters your progress; it is the enemy of improvement, the deadly foe of education; it fosters pride; it breeds insolence; it promotes vice; it shelters crime; it is a curse to the earth that supports it; and yet, you cling to it, as if it were the sheet anchor of all your hopes.

I can't top that---words that, but for gender, have the same power today as they did a hundred seventy years ago---so...code?

## Mystic T-Square

{% github jcolag/mystic-t-square %}

To break myself out of a rut, I started work on a new---and simple...at least, in all probability---game.  I don't want to give away *too* much, but you might have enough information to guess how the game will eventually look, based on what I have already committed.

 * You might recognize the name mystic square, in relation to puzzles and games.
 * The JavaScript code does something specific on loading the page, which seems unrelated to the other items, but might explain the **T**.
 * The HTML currently has a familiar-looking layout, also potentially relating to the **T** in the name.
 * It probably doesn't qualify as a clue, but so that nobody stresses over fitting in the reference, we use [T-squares](https://en.wikipedia.org/wiki/T-square) for drawing horizontal lines on a drafting table.

Each of those three pieces will feed into what I envision as a two-player game, probably mostly against a bare-bones artificial opponent, but maybe eventually online.

## Library Updates

I needed to bump library versions for [**Slack Backup**](https://github.com/jcolag/SlackBackup) and [**Git-Graft**](https://github.com/jcolag/git-graft).

## Next

With any luck, I'll split my time between **Mystic T-Square** and **Salavi**, this week, though I can't make any promises.

* * *

**Credits**:  The header image is [A False Alarm on the Fourth](https://www.loc.gov/item/2010652033/) by Udo J. Keppler, long in the public domain.
