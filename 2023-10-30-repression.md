---
layout: post
title: Developer Diary, ...Victims of Political Repressions
date: 2023-10-30 07:41:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Return-of-the-Names-29-10-2016-Moscow-A-01.png
teaser: This week's projects include a sneak peek at the upcoming newsletter, social media changes, the blog's code, and library updates.
spell: Hashover Fýlakas Onomáton Miniboost Slackup Uxuyu Zoea Krikheli
---

Today, the [Remembrance Day for the Victims of Political Repression](https://en.wikipedia.org/wiki/Day_of_Remembrance_of_the_Victims_of_Political_Repressions), memorializes the victims of political repression in the former Soviet Union.

![The Return of the Names ceremony in Moscow, 2016](/blog/assets/Return-of-the-Names-29-10-2016-Moscow-A-01.png "The person to the far left, with a completely different style of jacket and attention drawn out of frame, seems wildly out of place...")

And with everyone fully confused, on to the projects...

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the fourth.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, then you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the seventh of November, because I never publish blog posts on Tuesdays, making that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For October, I wrote a piece on the aftermath of my laptop-shopping process, discussed media consumption, and have some early-stage looks at two upcoming projects.  If you've become a member on Buy Me a Coffee, then you may have already seen previews for some of that.

## Social Media

It feels like only this time last month, when I updated people from my [T2 account to the newly-renamed Pebble account]({% post_url 2023-09-25-nepal %}).  Oh, right.  That definitely happened.  How time flies...

Anyway, I suppose that I can no longer point people at my ~~T2~~*Pebble* account, now because on the 24<sup>th</sup>, they announced---among other things---the following.

 > The painful truth, however, is that we were not growing quickly enough for investors to believe that we will break out. Combine that with a crowded space of alternatives --- and the uphill climb is even steeper. In order to continue to build out a complete Pebble, we would have needed more investment, and more time.

I feel like people haven't talked enough about this aspect of the announcement:  The industry doesn't see "the next Twitter" as a social space.  They see it as a money-making juggernaut that needs to constantly expand exponentially, even when we run out of humans and corporations to make accounts.  In other words, their vision of a replacement for Twitter in the public sphere *centers the worst aspects of Twitter* (and other businesses) in order to draw money out of the economy.

Also, they believed that they would have so little competition, that only the fact that many of the founders previously worked at Twitter would magically grant them market-share, even as people realized that the problems with Twitter existed long before the change in management.

Therefore, you have my assorted objections to getting attached to any service that doesn't have at *least* a non-profit organization running it, and ideally has a way for you to run your own, then it'll inevitably get worse and collapse.

Anyway, I didn't post much, there, but I do like the look of their exported archive enough that I might post it somewhere permanent.  Although the design that they put into their "gift" *does* raise the question of why they did such a lousy job of designing their actual application...

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Last week, I had the thought that readers may not (often) leave comments, here---so infrequently that I rarely even need to clean up spam comments---because they don't know if they can trust the comment system.  Sure, *I* know that I use [Hashover](https://www.barkdull.org/software/hashover) and that the comments themselves get backed up to a private GitLab repository (private, because the files expose e-mail addresses), but unless you read [a post from almost four years ago]({% post_url 2019-12-25-upgrades %}), *you* probably don't know that.

Therefore, I added a line down by the comment box that, if you'd rather discuss the post (or anything else of interest) somewhere *other* than my off-brand commenting system, I offered up [the blog's chatroom on Matrix](https://matrix.to/#/#entropy-arbitrage:matrix.org).  Or, rather, I *thought* I did that.  I actually failed to copy the final *g*, so we had a few days when I pointed people to a server that didn't exist.

Anyway, I tell you all this because...I corrected the link.  Now, you all can refuse to post comments *and* refuse to post in a chatroom.

While I already had business in the blog's code, I also updated my [social media roundup post](/blog/tag/linkdump) generation script to add a `spell` header.  As you may know from some prior post that I can't find, when I proofread, I pass the post through a spellchecker.  Because certain posts invariably get checked multiple times and contain words that you won't find in a standard dictionary and don't occur frequently enough to get their own space in a custom dictionary, I have a specific step in my post-checking script that collects words in that header and temporarily adds them to a custom dictionary.

The problem?  When I add the first unique word, I needed to add a new line to the top of the post, which made all the line references in the generated JSON file less useful.  By adding the header in when creating the post, I avoid that nuisance.

## Library Updates

I needed to bump library versions for [**Bicker**](https://github.com/jcolag/Bicker), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Miniboost**](https://github.com/jcolag/Miniboost), [**Renewal DB**](https://github.com/jcolag/RenewDB), [**Slackup**](https://github.com/jcolag/slackup), [**Uxuyu**](https://github.com/jcolag/Uxuyu), and [**Zoea**](https://github.com/jcolag/zoea).

## Next

As mentioned above, expect my Pebble archive to show up, this week, where I can immortalize my maybe-twenty posts by the end of the month.

I also still have quite a few library updates to deal with, so that may take priority for now.

* * *

**Credits**:  The header image is [Return of the Names 29.10.2016 Moscow](https://commons.wikimedia.org/wiki/File:Return_of_the_Names_29.10.2016_Moscow_(A)_01.jpg) by David Krikheli, made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
