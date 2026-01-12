---
layout: post
title: Developer Diary, International Sex Workers' Day
date: 2025-06-02 06:42:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [boring-css, library-update, open-badges, ruby, small-things, stenotype]
summary: Progress on assorted projects
thumbnail: /blog/assets/Sex-worker-statue-Oudekerksplein-Amsterdam.png
offset: -6%
description: This week's projects include stenotype corner, Boring CSS, Open Badges, my Small Things experiment collection, and a smattering of library updates.
update: [
  2025-06-01-one-fight.md
]
spell: stenotype Typey HRUF STKPWHRAO EUFRPBLGTSDZ ter modally Chording fas boring-css SmallThings Uxuyu Nokogiri Oudekerksplein
proofed: true
---

* Ignore for ToC
{:toc}

Today, we observe [International Sex Workers' Day](https://en.wikipedia.org/wiki/International_Whores%27_Day)---often under a rather outmoded and unfortunate term that I'd as soon not propagate---recognizing their often exploitative working conditions and, yes, honoring sex workers.  The date commemorates the brutal end of a strike by French sex workers that we credit with starting the modern international movement to treat sex workers like, y'know, *people* with civil rights and occupational protections[^1].

[^1]:  As regular readers know, I originally had an expanding couple of comments, back in the main post, which evolved into [yesterday's post]({% post_url 2025-06-01-one-fight %}), discussing why we should care about the treatment of sex workers.  Since I removed the serious stuff to a standalone post where it belongs, so that you can release some of yesterday's tension at my expense, I'll instead mention here that---having grown up watching far too many sitcoms, I suppose---I spent an embarrassingly large part of my life thinking that the phrase "dressed like a [pejorative term for a] sex worker" referred to the specific style of dress often found in 1980s media, with the weird, boxy wool-or-sometimes-faux-fur mid-length skirts, fishnet stockings, and a halterneck top (usually fake leather), maybe with a hat, all often in gaudy solid colors and extremely unflattering.  It took me longer than I ever plan to admit to realize that everybody else understood it as a wordy and offensive synonym for "sexualized" or even "sexy."  I probably *should* have known better, because I often remember the Dolly Parton interview where she describes her persona as derived from a sex worker she knew growing up, the "most glamorous and respectable person" in her town, and Parton doesn't dress like that...

![The Belle statue in Amsterdam, in front of the red-light district, inscribed Respect sex workers all over the world](/blog/assets/Sex-worker-statue-Oudekerksplein-Amsterdam.png "What the metal chick said...")

Stand up for sex workers, even if you despise their work, and you stand up for all of us.  Lecture over, I suppose.  Let's check out the week's projects.

## Stenotype Corner

My fifth week of this experience, sticking with the second lesson, *One-syllable words with simple keys*, but with the words randomized.  My speed has gone in interesting directions.  For most of the week, it dropped slightly and didn't budge---again, many of these words take more effort---but after a few days, my accuracy has climbed back to slightly over ninety percent after the usual hit that comes with a change.  Then, I started working more deliberately, prioritizing accuracy over speed...and my speed went up along with it.  {% emoji person shrugging %}  I probably should've expected that[^2], really, but it surprised me to see speeds of twenty words per minute even while trying to push through, but then twenty-two to twenty-five words per minute while "slowing down"...

[^2]:  Especially at such slow speeds, figure that the various fragments a second to confirm that I have the correct fingering in mind almost certainly comes to significantly less than making a mistake, undoing it, and then recovering.  The recovery might even take a couple of iterations, too, considering that a repeated or avoidable problem could fluster me, causing new issues.  I've probably mentioned that "traditional" typing generally takes the position that you *never* correct your mistakes in speed-testing, specifically to get you past this problem of getting wrapped up in rushing the fix and compounding the problem.

In any case, I'll likely move to the next lesson today or tomorrow, now that I can fairly consistently type in the mid-twenties words per minute with a mid-to-high-nineties accuracy for these words.

### Getting to Carnegie Hall but with Huge Transit Gaps

I'd like to raise another trouble that struck me during the week, and wish that I had a clearer way around:  The *modality* of stenography cuts against practice.

To explain, when learning traditional typing on something like a QWERTY keyboard, any time in front of a keyboard becomes an opportunity to practice.  Rest your thumbs on the space bar, left fingers on {% key A %} {% key S %} {% key D %} {% key F %}, and right fingers on {% key J %} {% key K %} {% key L %} {% key ; %}, and go.  If you know how to type the next letter/word, you do so.  If you don't remember where to find {% key B %} or the like, though, then you glance down to hunt-and-peck before returning your fingers to the home row.  Similarly, if I wanted to learn *written* stenography, then I could practice in normal writing by using shorthand for the words that I can figure out.  Neither of these has much cost of switching.

By contrast, because a stenography keyboard has an entirely different layout and requires more sophisticated circuitry---specifically, you need the ability to hit a bunch of keys at once and have them all register as a set ("n-key roll-over"), whereas most keyboards use a (physical) matrix to reduce the number of lines by having the keys share---you can't readily mix traditional typing with stenography.  Switching either requires physically changing position to change keyboards or (as my SOFT/HRUF does support) changing the keyboard's mode for one word.  Well, either that or "finger-spelling," where you use the stenography keyboard to modally type a single letter, but that doesn't count because that introduces a *third* mode, rather than bridging the two.  In any of the cases, it adds work.

This becomes an obstacle, because it means that a person---like myself---needs to learn a substantial number of words/syllables to type more than drills, which puts off building speed.  I'll get there eventually, but if you wonder why five weeks has only gotten me to about a third of my traditional typing speed, that disconnect between practice and utility probably has a lot to do with it.

When I have enough knowledge that I can write these posts with the SOFT/HRUF, you'll probably see the speed jump dramatically, with orders of magnitude more practice.  No, really.  Each drill picks forty-five words and presents them in three cycles, and I've gone with two drills per day, which comes to less than two thousand words (45 x 3 x 2 x 7) per week, which looks like a post where I don't actually have much to say...

### Back to the Books

Other than the drills, over the weekend, I also started re-reading [**Art of Chording**](https://www.artofchording.com/) to see if it has insights beyond drilling, or maybe different drills.  It feels extremely scattered, almost seeming like they meant it as a retrospective that talks about everything at once, not really interested in building skills so much as making sure that it doesn't overlook something.

Once it gets to more formal lessons, though---nearly halfway through the book, mind you---it does introduce the single-key abbreviations ("briefs") that I alluded to missing a while back, as well as identifying the "hidden sounds," as the chapter puts it, the sounds not directly included in `STKPWHRAO*EUFRPBLGTSDZ`.  It looks like it might provide enough information that I can now start sounding out most short words arbitrarily, rather than wait for the daily time that I've allocated to drills over the past few weeks, which should mostly solve my practice issue.

> If I can sound out the words as I go, then that should make my typing far faster and better over time.

That sentence sounds a bit stilted because I needed to choose shorter words without too much complexity, while coming up with something coherent and relevant on the fly, but I did get the entire thing out on the stenography keyboard in (almost) one shot, which I'd call a bigger success than general metrics.  I especially appreciate that the software/dictionary/whatever figured out what I wanted to do when I typed "bet" and "fas" followed by "ter."

## Boring CSS

{% github jcolag/boring-css %}

While I haven't done much for my CSS non-framework in a while, as a convenience to at least myself, the main page now displays a table showing the full set of colors at a glance.  Think of it in terms of checking every color against the default background at once, rather than literally only looking at the color palette.

## Open Badges

{% github jcolag/badging %}

While I don't have anything *useful* to report, here, it occurred to me that the penultimate step---why not pull out the big words on rare occasions, right?---didn't really feel right stylistically.  In Ruby, when you have an `if` or `unless` condition that only has one line...

```ruby
unless options.profile
  create_org_profile options.organization
end
```

The community generally prefers to use the single-line form.

```ruby
create_org_profile options.organization unless options.profile
```

Both versions execute identically, but the second reads more like English, do the thing unless this condition holds.

## Small Things

{% github jcolag/SmallThings %}

Not much to report, here.  I found an older experiment of mine to try out [Shoelace](https://shoelace.style/) and its web components, so decided to archive it here.

## Library Updates

I finally got around to clearing out the backlog, and needed to bump libraries for my [**Morning Dashboard**](https://github.com/jcolag/dash), [the blog's code](https://github.com/jcolag/entropy-arbitrage-code), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Ham Newsletter**](https://github.com/jcolag/ham-newsletter), and [**Uxuyu**](https://github.com/jcolag/Uxuyu).  The blog change may need to get backed out, though.  Whatever security problems [Nokogiri](https://nokogiri.org/) has, it looks like the old version has tendrils throughout Jekyll with parts pinned to specific versions, meaning that nothing builds with the library at the current version.  Maybe a solution exists, but for the moment and until I figure out a usable solution, I still run the prior commit.

## Next

I need to resolve the conflict with the blog's code, and I should probably get back to trying to figure out if my Open Badges implementation actually does things right.  Other than those, I've teased new projects for a while, now, so maybe you'll see the start of one or two of those.

* * *

**Credits**:  The header image is [Sex worker statue Oudekerksplein Amsterdam](https://www.flickr.com/photos/23941584@N00/885953123/) by [Romeo Design](https://www.flickr.com/photos/reidlromeo/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) license.
