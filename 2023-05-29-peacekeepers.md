---
layout: post
title: Developer Diary, Day of UN Peacekeepers
date: 2023-05-29 07:08:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Blue-helmet.png
teaser: This week's projects include a collection of useful (to me) scripts, my Mastodon Trunk Rummager, and Boring CSS, plus a reminder of my upcoming newsletter issue.
proofed: true
---

Today celebrates the [International Day of United Nations Peacekeepers](https://en.wikipedia.org/wiki/International_Day_of_United_Nations_Peacekeepers), paying tribute to those who have served in peacekeeping operations.

If you wonder why you can't contact your American colleagues, we also celebrate [Memorial Day](https://en.wikipedia.org/wiki/Memorial_Day) on the last Monday of May, honoring military personnel who died while serving the country.  The media prefers to explain it as "the unofficial start of summer," because they'd just as soon not remind us that the wars that invariably benefit their parent corporations have a human cost to them, but *do* want to remind us to start shopping for barbecues and trips to the beach.

![The UN Peacekeepers force´s helmet](/blog/assets/Blue-helmet.png "Do they pad them on the outside?  That seems irresponsible")

Since I can't think of much to say about that, I'll move on to programming.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the third.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/)---though I don't quite trust the company---you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee (the link in the previous paragraph, the *Follow* button to the upper-right of the page), you'll get it on Tuesday morning, the sixth of June, because I never publish blog posts on Tuesdays, making that a nicer match than Saturdays.

What will you find inside?  For May, I wrote a piece on the visual design of alternate universes, talked a bit about the current state of job-hunting, a maybe-final update on a side-project, and media consumption skewed toward honoring [Asian American and Pacific Islander Heritage Month](https://en.wikipedia.org/wiki/Asian_American_and_Pacific_Islander_Heritage_Month).  If you have joined as a member on Buy Me a Coffee, then you can already see previews for some of that.

## Periodic Scripts

{% github jcolag/periodic-scripts %}

I've finished my first pass of archiving at least the most modular scripts that I have, adding an empty configuration file, and providing some bare-bones documentation.  Currently, the repository contains three scripts.

You've seen `diary.sh` previously.  It generates the "record file" for my nightly journal, which forces me to recall my day.  The files increasingly also serve as data for my [**Morning Dashboard**](https://github.com/jcolag/dash).

You have probably *not* seen `editor.sh`, however, a script that takes a few steps to determine the system's default handler for a text MIME type, and opens that editor.  I won't get into the details---partly because I don't understand them---but for a while, the text editor installed on my system stopped working, so I began using an alternative.  I have scripts that open certain files on startup and every morning, and it grew tiring to update the scripts to choose the correct editor, so I created something to do it for me.

Finally, you have also not seen `night.sh`...or actually, you *have* seen the code, in my post on [changing day/night mode at sundown]({% post_url 2022-11-09-night %}).  This takes that code and builds it into a standalone script.  If you supply it with an optional parameter, it switches everything (that I could find) to night mode; without the parameter, it switches everything to day mode.

## Mastodon Tool Trunk

{% github jcolag/tool-trunk %}

Work on the *Rummager* continues as usual, though not much that I would call exciting.

Earlier in the week, a lot of the styling and layout settled down, including making the buttons more compact by preventing the contents to a separate line (`white-space: nowrap;`), giving the "preview card" of links a distinct style, and preventing header information from wrapping to another line.

The [HTMX](https://htmx.org/) now sits in the project, as well, so that I can begin experimenting with it.  As I've mentioned, if it can reduce the work involved with getting the buttons and other features working, I'll gladly take it over building everything from scratch or adding a compilation step to this code.

## Boring CSS

{% github jcolag/boring-css %}

As befits the name of the project, I only had one small change.

Somewhere along the way, the default text color for a `textarea` element became a light color and, because I don't often use many multi-line edit elements, I didn't notice that it had no contrast for many cases.

As a result, I changed the text to the neutral color used by other text, so it should look fine against most backgrounds.

## Next

Because I may become busier than usual over the next couple of weeks---you might detect my letting the reason slip earlier in this post---I may put a lot of projects on a brief hiatus and spend most of my discretionary GitHub time clearing out the backlog of library updates.

* * *

**Credits**:  The header image is [Blue helmet](https://commons.wikimedia.org/wiki/File:Blue_helmet.JPG) by [Daniel Košinár](https://commons.wikimedia.org/w/index.php?title=Gravedigger88&action=edit&redlink=1), released into the public domain.
