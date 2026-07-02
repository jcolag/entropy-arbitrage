---
layout: post
title: Developer Diary, Globe Fire
date: 2026-06-29 07:54:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, mini-server, newsletter, scrawls]
summary: Progress on assorted projects
thumbnail: /blog/assets/008139-globe.png
offset: -53%
description: This week's projects include the blog's newsletter, maybe-useful results from mini-server testing, the blog's code, a return to the Scrawls editor, and some library updates.
spell: parasocial Mem Pinebook Scuttlers Nonogram popover
proofed: true
---

* Ignore for ToC
{:toc}

Again lacking a real holiday, today marks the 413<sup>rd</sup> anniversary of the fire that destroyed the original [Globe Theatre](https://en.wikipedia.org/wiki/Globe_Theatre).  About a year later, the replacement on the same site opened its doors, which the [1997 reconstruction](https://en.wikipedia.org/wiki/Shakespeare%27s_Globe) down the road mimics.

![An approximation of the original Globe's interior, looking down on the stage](/blog/assets/008139-globe.png "Pursuing Bear not included")

And with that, on to the week's projects.

{% include newsletter.md
  media='🏳️‍🌈 LGBT Pride Month'
  preview='an upcoming (short) series of posts on escaping big companies'
  topics='parasocial weirdness|prom-ness predicate|a year of PBS Passport'
%}

## Mini-Server, Part 26

While I don't have anything useful to report, here, I finally took the time to run [Mem Test 86+](https://www.memtest.org/)---which many of you probably want to know about, since the closed-source fork gets more publicity---on that server that kept shutting down under load.  And...it shuts down about a sixth of the way into the test, so I officially have no idea what else might cause this problem.

Well, I have *one* more idea.  Because the machine refuses to start back up for a few minutes after knocking off, that might suggest overheating.  But I don't see where to access the fan or CPU, so that might take even longer to test.

In all fairness, I don't necessarily have a plan for yet another mini-PC, but it doesn't sit at all well with me to have a box around that can *pretend* to work before its...let's call it an inevitable betrayal.  And honestly, a computer with a decent amount of memory won't go to waste, even if it becomes the computer-of-last-resort in the house, somewhere that I can most quickly move everything that I have going.

Oh, another non-report, I finally looked up [Briar Mailbox](https://code.briarproject.org/briar/briar-mailbox), and realized that it *really* wants to run on a mobile device, intending to use a low-power system to constantly monitor for incoming messages.  I actually do have a tablet that I "took out of service" because I woke up to find the battery swollen to the degree that it started pushing the screen out of the shell.  However, it doesn't work without a battery, and you can probably guess that I disposed of the bloated battery, so I'll need to hunt down a replacement.

Between that and the Pinebook, it occurs to me that power seems to represent the biggest vulnerability on these systems.  Thinking about it, since the last time that I had an arbitrarily desktop computer---which I probably should never have abandoned, I'll grant you---I believe that power connectors and/or overheating accounts for at least a significant chunk of my abandoned computers.  On the blog alone, [last year's dead laptop]({% post_url 2025-06-23-midsummer %}) seemed to involve some combination of overheating and some aspect of the power system that prevented it from recovering, and the time that [one laptop's power connector needed restructuring]({% post_url 2021-12-06-nicholas %}) (which didn't survive long) and my backup computer also died.  And the latter post *also* makes reference to a machine before that when another power connector had gotten so bad that I needed to solder patches to keep it going for a while.

It makes some sense, I guess, considering that, especially for the parts of the year when I feel compelled to work outside if possible, those connectors see a lot of action, and so have a physical failure mode that the CPU or the like wouldn't.  But it still annoys me to have these computers "fail" in that way that I end up stacking them up in a cabinet for some hypothetical day when I'll fix them...

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Work continues on cleaning up the blog, mostly, but not entirely, around the styles.

With the variable form of the text font that I mentioned last time, with (I think) better-chosen weights for the normal and bold type.

The styles also take a more rigorous approach to browsers requesting reduced motion.  The blog probably doesn't use *much* motion, but it still makes sense to cut it down as much as possible for people who'd rather not deal with it.

Similarly, the pull-out trays should come off as significantly more readable, and the text alignment in the footer tries to provide a bit more balance.  And you'll see the Amazon annotation icon for any links---such as featured in [Saturday's post]({% post_url 2026-06-27-neon-northern-3 %})---to the Italian storefront.

On the beefier side, the Friday posts will, starting this Friday, have improved accessibility, with ARIA labels (or actual text, depending on which link) describing the link as going to the article or quote for that day of the week.

And biggest of all, you already saw the results in---*as*, really, since it takes care of everything, from the heading down---the section about the newsletter, above.  I fed it the relevant heritage/history/pride month that guided my book and film choices, the project that I want to talk about, and a list of the writing pieces, and it filled in the rest with the overall structure and correct dates.  And importantly, going forward, if I need to change the text, such as where to sign up, then those changes will automatically populate retroactively (to this month), so that I don't have people signing up on sites where nobody'll find me anymore.

I only regret that the rainbow flag emoji (in this post) doesn't have the usual mark-up and styling that indicates the emoji and enlarges it on hovering, but the effort involved in making that works seems like it'd outweigh the utility.

## Scrawls

{% codeberg jcolag/scrawls %}

I'd consider the software in "wet paint" mode for a bit, but it should have the pieces in place---other than [Code Mirror v5](https://codemirror.net/5/doc/manual.html#addons), which won't go into the repository---to show the editor, at least the does-not-save, not-at-all-fancy version.

## Library Updates

I needed to bump library versions for [Ham Newsletter](https://github.com/jcolag/ham-newsletter), [Little Scuttlers](https://github.com/jcolag/LittleScuttlers), and [Picture to Nonogram](https://github.com/jcolag/picture-nonogram).

## Next

For the moment, the blog has most of the usability and accessibility changes that I have had in mind.  Eventually, I'll want to use the [Popover API](https://developer.mozilla.org/en-US/docs/Web/API/Popover_API) (no relation to breakfast pastries) for the pull-out trays and maybe even the "menu" at the top of each page, but I want to wait until support ends for [Firefox 115 ESR](https://endoflife.date/firefox), which came out before they added the feature.  At the moment, Mozilla has support slated to end in August, but may decide to extend support again, if Windows 7--8.1 and macOS 10.12--10.14 users still exist in large numbers and haven't found a suitable replacement.

Actually, it only has half-implementations, and treating the mouse-over event like a click probably goes too far.  But if you can get a quick preview of my [prototyping the popover idea](/blog/popover), if that strikes you as interesting.  The tab on the left should mimic the "recommended posts" tab on the index pages.  And the "hamburger button" where you'd normally find the main text opens a menu in the same position, because I didn't want to write a new set of styles for the test.  Like I said, half-implemented with some over-ambitious ideas, but it uses less code and should look and work more consistently across platforms than the current system.

Otherwise, expect Scrawls to get most of the attention.

* * *

**Credits**:  The header image is the [Shakespeare's Globe Theater reconstruction](https://digitalcollections.folger.edu/img8139) by Joseph Q. Adams, long in the public domain due to expired copyright.
