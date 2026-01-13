---
layout: post
title: Developer Diary, International Animation Day
date: 2024-10-28 07:43:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, codeberg-profile, cohost, lights-edge, newsletter]
summary: Progress on assorted projects
thumbnail: /blog/assets/Animexample3.png
offset: -8%
description: This week's projects include the blog's newsletter, archiving my Cohost posts (code and results), the blog's code, The Light's Edge, and my Codeberg profile.
spell: Monkaa Viaje Tierra del Quebracho Boing rsquo fictures
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate [International Animation Day](https://en.wikipedia.org/wiki/International_Animation_Day), celebrating the art of animation.  If you go in for the Free Culture side of things, this might make a good day to finally check out [**Monkaa**]({% post_url 2020-12-12-monkaa %}), [**Your Face Is a Saxophone**]({% post_url 2022-02-19-saxophone %}), or [**Viaje a la Tierra del Quebracho**]({% post_url 2024-08-10-quebracho %}).

![Six frames that (could) loop to show a bouncing ball](/blog/assets/Animexample3.png "Boing")

And on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the second.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the fifth of November.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For October, I wrote a piece on **Star Trek:  Prodigy**'s second season and another on giving up an increasing number of streaming services, discussed media consumption skewed slightly towards celebrating Hispanic Heritage Month and Filipino American History Month, and provided more background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Cohost Archive

{% github jcolag/cohost %}

I believe that I've done everything with [my Cohost posts](https://jcolag.github.io/cohost/) that I wanted.  On a single page with a Cohost-inspired style, you can read everything that I posted over the two years.  I have found ways around the small amounts of proprietary media that I originally posted.  And I cleaned up a couple of typos that you probably wouldn't care about in reading but bothered me.  Oh, and the repository complies with REUSE, so that anybody who wants to recycle the uploaded media can quickly find the terms.

I may add an explicit license statement at the bottom of the page, along with a link to the repository, but this should do it for this little project...unless you want to see the code that I used.

## Cohost Export

{% github jcolag/cohost-export %}

Did somebody say code?  This new repository contains the Ruby code that I used to parse my archive and create the exported archive, along with any support files that I needed.  Presumably, Cohost itself will publish a tool that does a more thorough job, but this script works for me.

If you try this tool out, then you'll want to edit `head.html` to display your name and contact point, rather than mine.  And if it overlooks something that you cared about in your archive, get in touch, and we can try to figure out how to generalize it.  As a rule, I post fairly conservatively, and try to make every post stand alone, so the code has no concept of threaded messages or "CSS Crimes," and only *barely* acknowledges media.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage %}

After the work done on archiving my Cohost posts, this seems sort of anti-climactic, but I did some mild clean-up on the index pages.  It takes the non-JavaScript link to Matomo---the self-hosted analytics system that I use for the blog, so that I have some sense of what people read---that used to live in the HTML header for some reason, where it never belonged, and puts it on the actual page.

Along the way, the post image previews also get `alt` text, recycling the post's title.  I don't like describing images that way, but this feels like a special case, since (a) it would take a ton of work for me to extract the descriptions that I use in the posts, and (b) I don't see the images as having any value beyond breaking up the format of the index and occasionally drawing attention.

## The Light's Edge --- Episodes

{% codeberg jcolag/lights-edge-episodes %}

While still no episodes, at this time---it increasingly looks like I'll need to aim for a November release for the first part, since it doesn't make much sense to fight with Halloween---I improved the README, so that it now has a full section on contributing.  It also goes into some detail about *why* contributors need to comply with the project's license to participate, pointing out that the project doesn't really happen without everybody following the license.

## Codeberg Profile

{% codeberg jcolag/pages %}

I have (finally) updated the index to include the aforementioned episodes for **The Light's Edge**, so that people can find it when they land on the page.

Along the way, I also fixed maybe the goofiest typo that I've (publicly) made in my career, referring to "action **fictures**," whatever that would mean.

Oh, and I cleaned up the problematic apostrophes.  [Pandoc](https://pandoc.org/) converting the ASCII apostrophe `'` to a Unicode right single quotation mark `’` (U+2019), which I'd call *technically* accurate, but prone to somebody's browser interpreting as something else.  As such, I replaced the Unicode character with the more appropriate and portable `&rsquo;` HTML entity.

## Next

Now that I've preserved my Cohost posts, I'd most like to go back to cleaning errors out of the blog's HTML, so I guess we'll see how that goes...

* * *

**Credits**:  The header image is [Third in a series of three example images about animation](https://commons.wikimedia.org/wiki/File:Animexample3.png) by [Branko](https://en.wikipedia.org/wiki/User:Branko), released into the public domain by the artist.
