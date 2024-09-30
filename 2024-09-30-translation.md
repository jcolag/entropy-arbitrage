---
layout: post
title: Developer Diary, International Translation Day
date: 2024-09-30 07:47:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Rosetta-Stone-front-face.png
offset: -15%
teaser: This week's projects include the blog's newsletter, the blog's newsletter, The Light's Edge, and a bunch of library updates.
spell: LicenseRef CPREP Fýlakas Onomáton Miniboost Uxuyu FSFE Hillewaert
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate [International Translation Day](https://en.wikipedia.org/wiki/International_Translation_Day), celebrating translation professionals.  You know that I like a language day.  This one coincides with the Christian feast of Jerome, patron saint of translators.  As someone who has spent a lot of time translating things---with and without computer assistance---and working with people to get software interfaces translated, I definitely want to applaud the people who do this for a living, even if I don't often have the opportunity to pay for the service.

![The Rosetta Stone](/blog/assets/Rosetta-Stone-front-face.png "It belongs in a museum...but not that one")

If you'd rather something trendier, we also have [Blasphemy Day](https://en.wikipedia.org/wiki/Blasphemy_Day), bringing attention to freedom of expression, especially in the form of criticism of religion.  We still have a couple of countries that apply the death penalty to blasphemy, so we don't want to forget about the issue.

And on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the thirty-first, one of the occasions when the Saturday of the last week of the month falls in the actual month.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the third of September.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For September, I wrote a piece on Cohost's untimely demise, discussed media consumption skewed slightly towards celebrating Hispanic Heritage Month, and provided some background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## The Light's Edge --- Website

{% codeberg jcolag/thelightsedge %}

In preparation for the first parts of the first story, I spent the week pulling the website together, making it compliant with [REUSE](https://reuse.software/).

Frustratingly, REUSE doesn't seem to have an official method for including proprietary assets with permission.  I can understand this, on one hand, because the FSFE presumably doesn't want to encourage it, and [SPDX doesn't include](https://spdx.org/licenses/) anything that qualifies.

After more searching than I care to admit and finding plenty of people with similar problems...never ignored, because they did get responses, even though none of those responses included a viable answer, I settled on a half-measure of a "license" file called `LicenseRef-Proprietary.txt`.  SPDX has at least occasionally recommended that prefix for any license that they don't talk about, and I needed to give it some name.  For the content, I went with something minimal, to cover what I hope would include any other one-off items that I could potentially need.

 > All rights reserved under relevant copyright statutes.  Used with permission.  

Now, `reuse lint` tells me that I have properly complied with REUSE, because it apparently doesn't inspect the license names.  Regardless, I'd call that close enough.

## Library Updates

I needed to bump library versions for [**CPREP**](https://github.com/jcolag/background-generator), the [blog's code](https://github.com/jcolag/entropy-arbitrage-code), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Miniboost**](https://github.com/jcolag/Miniboost), [**Slack-up**](https://github.com/jcolag/slackup), and [**Uxuyu**](https://github.com/jcolag/Uxuyu).

## Next

Expect another week of library updates, since I still have plenty, though I'll also probably need to spend some time uploading whatever Cohost exports for me.

I may also start publishing **The Light's Edge** within the next few weeks, and so will start making preparations for it.

* * *

**Credits**:  The header image is [Rosetta Stone](https://commons.wikimedia.org/wiki/File:Rosetta_Stone.JPG) by [Hans Hillewaert](https://www.flickr.com/photos/81858878@N00/), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/) license.
