---
layout: post
title: Developer Diary, Evolution Day
date: 2025-11-24 07:15:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [newsletter, codeberg-profile, salavi, mastodon-tool-trunk, library-updates]
summary: Progress on assorted projects
thumbnail: /blog/assets/Darwin-s-finches-Gould.png
offset: -38%
description: This week's projects include the blog's newsletter, my Codeberg profile, Salavi, my Mastodon Tool Trunk, and a library update.
spell: salavi jq
proofed: true
---

* Ignore for ToC
{:toc}

Today marks [Evolution Day](https://en.wikipedia.org/wiki/Evolution_Day), celebrating the anniversary of the publication of [**On the Origin of Species**](https://en.wikipedia.org/wiki/On_the_Origin_of_Species) in 1859.

![Darwin's finches, suggestive of branching lineages](/blog/assets/Darwin-s-finches-Gould.png "If I still cared about Twitter and if it still existed, this would've felt like a great excuse for a send-tweet joke...")

By the way, not really related to anything that I have done, exactly, but I discovered this week that, arguably, I have violated Codeberg's terms of service by using it to store non-software.  No, nobody complained.  Rather, [Codeberg clarified its terms of service](https://blog.codeberg.org/letter-from-codeberg-onwards-and-upwards.html#:~:text=blogs%20and%20personal%20websites) to explicitly include software released under Free Culture licenses.

Why mention it all, if I now fully comply with their terms?  Partly, I want to apologize to anybody who saw my use of Codeberg and wondered why I would throw my support behind an organization that seemed to only allow software[^oSFO7c], but also, congratulations to them for catching that their phrasing made people uncomfortable[^cxigP8].

[^oSFO7c]:  If you actually want an answer to that, I assumed that they meant "free and open source" in the broad sense that would include Free Culture works, especially since their new-repository page allows using broader Free Culture licenses than software.

[^cxigP8]:  And now, as you can see in the comments on the issue, that people have chosen to wildly misinterpret the decision to start asking when they can start using the exclusionary licenses that I talked a lot about in [yesterday's post on licensing]({% post_url 2025-11-23-free-culture-licensing-2 %})...

And with that, on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the sixth.

**Programming Note**:  I will sunset the Mailchimp version of the newsletter near the end of the year, as they have announced moving "custom coded e-mails"---exactly how the newsletter works---behind their paywall.  I won't use their terrible UI, so I'll try to find an alternative that can import the Mailchimp list, but if you want the newsletter or want to keep receiving it after the new year, follow me on Buy Me a Coffee.

If you have signed up on Mailchimp, at least one more time, you'll get the e-mail on Saturday the sixth, which I realize feels like a long lead.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the ninth of December.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For November, I wrote a piece on (no surprise there) moving away from Mailchimp after five-plus years, discussed my media consumption slanted a bit towards Hispanic American Heritage Month and Filipino American History Month, and provided some background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Codeberg Profile

{% codeberg jcolag/.profile %}

I adjusted and updated some of the verbiage on [my profile](https://codeberg.org/jcolag/), and added an ignore file so that I can start setting up the structure to add (and then update) the list of recent blog posts to keep the profile up to date.

## Salavi

{% codeberg jcolag/salavi %}

Now that the generated boards work correctly, I have created a blank board (`index.html`) that (baby steps) uses JavaScript to build the board, so that it doesn't need the separate generation step.  Right now, I don't have snakes or ladders in place, but you can pretend to go head-to-head with the Owl on the [deployed Salavi page](https://jcolag.codeberg.page/salavi/).

## Mastodon Tool Trunk

{% codeberg jcolag/tool-trunk %}

The week before Daylight Saving ended, my script scheduled the week's toots an hour late.  As it turns out, when I wrote the script, it incorrectly grabs the time zone for a week later, instead of something more reasonable---given that the scheduling happens over the weekend---such as a day or two later.

I also added a quick script to confirm the scheduling, since I can never remember `jq .[].scheduled_at` for whatever reason.

## Library Updates

I also needed to bump library versions for the [Generic Board Game](https://github.com/jcolag/generic-board-game) repository that never really went anywhere.

## Next

I'll try to wrap up Salavi, this week, then have some work to do on the blog, and maybe a couple of other things.  And I'll continue to clear out the backlog of library updates on GitHub.

* * *

**Credits**:  The header image is a scan from (what we now call) [**Voyage of the Beagle**](https://www.biodiversitylibrary.org/page/2010582#page/393/mode/1up) (1839), page 379, by John Gould, long in the public domain due to an expired copyright.
