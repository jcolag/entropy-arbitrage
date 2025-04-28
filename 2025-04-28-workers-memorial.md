---
layout: post
title: Developer Diary, Workers' Memorial Day
date: 2025-04-28 07:28:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/WMD-ribbon.png
offset: -38%
description: This week's projects include the blog's newsletter, Mystic T-Square (finally), and some library updates.
spell: Dia visibilidad Scuttlers Zoea RolandR
proofed: true
---

* Ignore for ToC
{:toc}

Today marks [Workers' Memorial Day](https://en.wikipedia.org/wiki/Workers%27_Memorial_Day), an international day of remembrance and action for workers killed, disabled, injured, or otherwise made unwell by their work.  Our Canadian friends call it their National Day of Mourning.  Either way, it often serves as a vehicle to spotlight the fight for workplace safety.

> Remember the dead – Fight for the living

While this doesn't generally happen, we should probably also use the opportunity to consider that we have serious disparities in *who* often gets harmed by their work, and the biases and harassment that lead to those disparities by driving those other people out of the workplace.

![A purple  Workers' Memorial Day ribbon](/blog/assets/WMD-ribbon.png "I'd love to stop needing these sorts of events...")

And with that, on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the third.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the sixth of May.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For April, I wrote a piece on the continued degradation of customer service in multiple senses of the word, discussed my media consumption slanted a bit towards Arab-American Heritage Month, and provided some plans for **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Mystic T-Square

{% github jcolag/mystic-t-square %}

Shockingly, most of this week went to finally updating everybody's least-remembered Tic-Tac-Toe-with-Trivia variant.  It hasn't finished, yet, but a realization on why the AI[^1] never seemed to work.

As of this writing, it still doesn't work, but the refactoring has begun to minimize the paths that need testing as everything else changes.  You'll also see a handful of new variables that might give small hints as to how the upcoming changes will work.

[^1]:  I mean artificial intelligence in the traditional sense of code that tries to make useful decisions based on an algorithm, not the modern smoke-and-mirrors game of generative language models that cost a fortune to run.  In this case, the code aims to replace the tile-sliding player by gaming out how each move affects the chances of winning, so that it can make an informed decision, like a stripped-down chess AI.

## Library Updates

I needed to bump library versions for the [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Little Scuttlers**](https://github.com/jcolag/LittleScuttlers), and [**Zoea**](https://github.com/jcolag/zoea), though I suppose that I'd consider those mostly abandoned projects.

## Next

I'll need finish getting the **Mystic T-Square**'s AI running---early tests look viable if not particularly "intelligent"---and then it'll probably need configuration options to turn the AI on and off (making it a one- or two-player game) and eventually tuning the AI to favor different outcomes.  I may also have worked out how to refactor the blog's SASS code.

* * *

**Credits**:  The header image is [WMD Ribbon](https://commons.wikimedia.org/wiki/File:WMD_ribbon.jpg) by [RolandR](https://commons.wikimedia.org/wiki/User:RolandR), made available to the public domain by the photographer.
