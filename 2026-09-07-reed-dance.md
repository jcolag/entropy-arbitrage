---
layout: post
title: Developer Diary, Umhlanga
date: 2026-09-07 07:54:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, mini-server]
summary: Progress on assorted projects
thumbnail: /blog/assets/Reed-Dance-Festival-2006.png
offset: -26%
description: This week's projects include my mini-servers (including looking for Linux replacements), the blog's posts and code, and some library updates.
spell: Umhlanga hnEziY Pinebook Gentoo Guix Behlendorf CPREP Nonogram Amada
proofed: true
---

* Ignore for ToC
{:toc}

Most of the United States celebrates its fake Labor Day, the one that quietly ignores the labor movement, but the Swazi people (I believe) celebrate their {% wiki Umhlanga %} "reed dance" festival today.  It has some unfortunate patriarchal origins, but it sounds like at least Eswatini seems to have dismissed the obsession with trying to manifest virginity[^hnEziY] as a physical attribute.

[^hnEziY]:  For those not familiar, virginity has no objective operational definition.  Anything that one might "inspect" could exist or not on any given body, based on a wide variety of factors, only loosely correlating to sexual activity.

At least it looks better than a random family grilling, right?

![A crowd of Swazi women in different kinds of traditional garb in the background, with a woman in a green uniform in the foreground, looking to the left](/blog/assets/Reed-Dance-Festival-2006.png "It looks more like a listless flash mob at the moment, but presumably things pick up from here")

And with that, on to the week's projects.

## Mini-Server, Part 32

I mentioned this in passing in [yesterday's post]({% post_url 2026-09-06-shop-small-3 %}), but I had two semi-related developments.  First, I finally got a viable power adapter for my (original, non-Pro) Pinebook.  The battery now charges, and the thing starts up, though I don't recall what password I set however many years ago when I bought the thing.  Rather than try to guess, I plan to install...*something*.

Again, this came up in yesterday's post, so I apologize for the redundancy.  I would normally pick a lightweight Linux distribution and use it as the "spare" and possibly remote laptop, something quick to pull into service when I need it.  However, we have had some frustrating developments, over the past couple of months.

- Linus Torvalds made it abundantly clear that the [Linux kernel happily accepts LLM contributions](https://lore.kernel.org/linux-media/CAHk-=wi4zC+Ze8e+p3tMv8TtG_80KzsZ1syL9anBtmEh5Z40vg@mail.gmail.com/) and opposes progressive politics, which...yuck.
- The Debian community [voted to allow "responsible" LLM use](https://www.debian.org/vote/2026/vote_002), which can't really coexist with [Debian's long-held position](https://www.debian.org/intro/why_debian) as the "stable and secure" choice that "provides smooth Upgrades."
- Fedora has an [almost identical LLM policy](https://docs.fedoraproject.org/en-US/council/policy/ai-contribution-policy/).

Now, you know that I have a relatively nuanced approach to LLMs.  I don't believe that you can get them to write good code, and you certainly pollute the copyrights, even if it does a fantastic job.  But I don't pore over lists of [software with LLM-assisted contributions](https://codeberg.org/ethical-foss/open-slopware) to rail against and abandon those projects.  However, the operating system raises the stakes for both quality and copyright, so I'd rather not rely on the thing that connects all the other code to hardware *and* makes sure that resources get allocated fairly.

The overwhelming majority of Linux distributions build on either Debian or Fedora, which would limit my options, in that case.  But even if I moved to something independent with a no-LLM policy, such as [Gentoo](https://www.gentoo.org), [Elementary](https://elementary.io), or [Guix](https://guix.gnu.org/), all Linux distributions (tautologically) include the Linux kernel.

Beyond Linux, [Net BSD](https://www.netbsd.org) has a ban on LLM-based contributions, on the basis that the license can't protect code of uncertain copyright (good), but I believe that the lack of a copyleft license makes it a riskier platform to trust in the long-term[^Xl4kUz], as evidenced by BSD not growing as robust a community as Linux.  We also have other UNIX-like kernels, such as [GNU Hurd](https://www.gnu.org/software/hurd/advantages.html) and [Redox](https://redox-os.org/), which have potential.

[^Xl4kUz]:  Maybe that doesn't matter for the Pinebook, though.

It looks like Redox actually works on their entire operating system (also called Redox) of unclear completeness.  And Guix appears to have the most complete Hurd integration, offering it as an option from the installer.  More on this as I research, I guess.  I *know* that I don't have the energy to assemble my own system---kernel, management software, utilities, and user interface---to even try to consider that a real option.

Anyway, I said that story had two pieces, here.  I put off going to Pine64 for the power adapter, because they charge quite a bit for shipping, something that didn't matter when I bought a laptop, but makes less sense for commodity hardware like a power adapter.  But since (apparently) nobody else has anything comparable, I needed to compromise.  As such, I decided to spring for a Pine Time (their smart-watch) and a couple of accessories to feel less awful about the shipping costs.

And I have actually wanted a pedometer, since my little tablet stopped counting steps for whatever reason, and this does the job quite well.  I'll need to work out how to get the data from the watch into files that I can analyze like I did the old tablet app, but so far, I like the thing...other than not liking wearing a watch.

## Entropy Arbitrage, the Posts

{% codeberg jcolag/entropy-arbitrage-posts %}

Complaining about the [Open MDW license]({% post_url 2026-08-30-open-mdw %}) over last weekend reminded me that I still had old blog posts referring to a [certain software foundation insistent on retaining its offensive name](https://apache.org/) while also claiming to do better by creating a "placebo brand" (The ASF) that *you and I* can totally use to refer to them[^n3o7IK], while they continue to use the name that Native American developers have begged them to stop using for decades.

[^n3o7IK]:  The more that I read about the issue, the more I consider using *other* names to refer to them...

Finally, I went through the old posts and put an end to that.  Except for two posts quoting other sources and one more referring specifically to the [SPDX identifier](https://spdx.org/licenses/) (last Sunday's post does both), which I can't reasonably alter, *Apache* now refers only to the Native American identity, when I use it on the blog.  I refer to the license as the ASF License 2.0.  For a while, I put off the change in case a consensus emerged on what to call the license, but bashing the Linux Foundation made it pretty clear that it should get fixed sooner than later.  Previously, I took care of references to the organization or its projects.

For people who don't know/remember the back-story, here, foundation founder Brian Behlendorf wanted a name that evoked the romanticism of Geronimo and "the last days of a Native American tribe called the Apaches," despite the *hundreds of thousands* of Apaches around today.  The same quote goes on to describe making a web server as pretty much the same thing, symbolically, as fighting for one's homeland[^4jL9Iq].  Only later did someone surprise Behlendorf by complimenting him on the "a patchy web server" pun...that he didn't notice.

[^4jL9Iq]:  I can't help but marvel at how well this models Julia Serrano's model of harmful cultural misappropriation, which she identified as anything involving at least one of erasure, exploitation, or denigration, often abbreviated as EED.  You have exploitation right off the top, with taking a tribal name to represent a business entity that has no connection to the people.  You have erasure, by declaring them to have had their "last days" more than a century ago.  And you have denigration by trivializing the ethnic cleansing that they endured as somehow analogous to writing an HTTP server.

Anyway, Native Americans have tried to convince the foundation to change its name for decades---I didn't notice, to my chagrin---and they declared the problem resolved a couple of years back by turning their feather logo into a leaf, and suggesting that people uncomfortable with the cultural misappropriation use the organization's initials.  I called that a "placebo brand," since they have no intention of changing their official name or project branding, but using the initials does serve the purpose of not letting *me* make the situation worse by perpetuating the offending name.

Yeah, I know, a lot of verbiage to explain "I changed one, sometimes two, words in about a dozen posts."

Likewise, I went through all [Free Culture Book Club](/blog/tag/book-club) posts and added a quick explanation that I hope will cut down on the people trying to identify the posts as "reviews" and agonizing over whether I gave a "good" one to a project that they care about.  They look like this, for now.

{% include fc-review.md %}

It seems silly to need such an announcement every week, but I do have a collection of about twenty messages over the years across various channels---creators taking issue with my assessment of the work in one way or another---which informs me that I should've done something like this all along.  And it also makes use of the new flexibility in the content warning boxes, from a few weeks back.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Probably to nobody's surprise after the long story in the previous section, I created that "stop calling this a review" disclaimer as a partial file for Markdown to include in posts, so the repository now includes that, too.

In addition, the first-weekday-of-month code needed an adjustment again.  Somehow, it slipped by without bounding the date to the first through the seventh.

Likewise, the [About page](/blog/about) now has a new section admitting to the couple of AI-generated images a couple of years back that I'll eventually replace, but otherwise don't use LLMs for any content on the blog.

## Library Updates

I needed to bump library versions for my character background generator [CPREP](https://codeberg.org/jcolag/cprep-background-generator), my [morning dashboard](https://codeberg.org/jcolag/dash), and the [Picture-to-Nonogram](https://codeberg.org/jcolag/picture-nonogram/commits/branch/main) code.

## Next

For this week, I'll probably continue slogging through the library updates, at least on mornings when I don't have something else that takes priority.  I did find two programming languages that have me somewhat excited, so either might trigger an idea as I get acquainted with them...but also, maybe not.

I'd also *really* like to finally square away my makeshift incubator, but that requires other people (and companies) providing things.

* * *

**Credits**:  The header image is [Reed Dance Festival 2006-018](https://commons.wikimedia.org/wiki/File:Reed_Dance_Festival_2006-018.jpg) by [Amada 44](https://commons.wikimedia.org/wiki/User:Amada44), released into the public domain by the photographer.
