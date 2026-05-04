---
layout: post
title: Developer Diary, Anti-Bullying Day
date: 2026-05-04 07:43:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update]
summary: Progress on assorted projects
thumbnail: /blog/assets/Sikana.png
offset: -19%
description: This week's projects include the blog's code and library updates.
spell: MMJBac Notoboto Šikana olej na plátně Klára Sedlo
proofed: true
---

* Ignore for ToC
{:toc}

Today, we observe [United Nations Anti-Bullying Day](https://2009-2017.state.gov/j/drl/rls/rm/2012/189663.htm), which seems largely abandoned.  But given that something like a quarter of adolescents face bullying, to say nothing of adults and having bullying as a government policy in a lot of the world[^MMJBac], maybe we should get that going again.

[^MMJBac]:  I suppose that, technically, opposition to cyber-bullying has a different day...

![A pumpkin-headed clown with a malicious grin brandishes a whip over a distressed, wilted pumpkin on the ground](/blog/assets/Sikana.png "I admittedly didn't even consider that a bullying option, but yeah, don't do that either, I guess...")

Unrelated, when it occurred to me that we have a corporate-sponsored holiday today as well---"Star Wars Day" {% emoji yawning face %}---I had a fairly terrifying realization:  I used holidays from the beginning to identify the developer diary posts *sometimes*, but also frequently resorted to little more than identifying when in the month the post landed, such as [End of April]({% post_url 2020-04-27-april %}).  I didn't plan to keep going with the diary posts for *other* projects, you see, and so didn't expect to have another end-of-April developer diary post, for example.  Regardless, it didn't really matter, because I never used the holiday for anything more than the title.

Well, six years ago, that changed with [If You Give a Mouse a Sci-Fi Franchise...]({% post_url 2020-05-04-mouse %}), also (I believe) the only one of these posts to try for a clever title, since I considered it a gesture at using the holiday under mild duress[^5pNpNw].  And at that point, it finally dawned on me that I have written these posts long enough to start needing to worry about *duplicating holidays*.  Two weeks ago, I used Chinese Language Day, for example, exactly as I did (though without any explanation) in 2020 as well.  In other words, I'll need to start checking the blog's own history to avoid reusing events.  (And sure, I already have a tendency to keep coming back to the same always-on-a-Monday holidays...)

[^5pNpNw]:  For example, I wouldn't want a funny title for an anti-bullying day such as today's post, because that feels inappropriate.  I'll dump on Corporate America tirelessly, though...

And with that, on to the week's projects.

## Newsletter Reminder

I won't belabor the point this time through, but for those of you interested in receiving this month's newsletter, it goes out tomorrow morning.  You can make sure that it shows up in your inbox by heading to [Buy Me a Coffee](https://buymeacoffee.com/jcolag), clicking **...** in the upper-right (to the left of **Login**), selecting **Follow**, and providing your e-mail address.

Or if you'd rather read them after-the-fact and keep me far away from your inbox, I believe that I have tagged them all properly as posts, so that you can [visit the list](https://buymeacoffee.com/jcolag/posts/71215) as far back as May 2022 when I started using the service.

## Entropy Arbitrage, the Code

{% codeberg jcolag/entropy-arbitrage-code %}

In time for [yesterday's AI-related post]({% post_url 2026-05-03-good-ai-2 %}) that included a sample user interface, I added styles to make those mock-ups legible in dark mode.  Since it generates the SVG inline, CSS can style the elements, the `line`, `polygon`, `rect`, and `text` elements each have a `fill` and `stroke` property.  The `text` elements use `fill` for their coloration, everything else uses `stroke` for its outlines.

## Library Updates

Mostly, [Notoboto](https://codeberg.org/jcolag/Notoboto)'s semantic search work---all written in Python---needed a *bunch* of library versions bumped.

## Next

Same deal as the past few weeks, I'll try to finish clearing out the backlog of library updates and tweaking details on the blog---it looks like the embedded UI mock-ups don't show up in the RSS feed, and I'd like to figure out why, since I believe that every other plugin works right---but mostly to buy time while I keep reading up on something else.

* * *

**Credits**:  The header image is [Šikana, olej na plátně](https://commons.wikimedia.org/wiki/File:%C5%A0ikana,_olej_na_pl%C3%A1tn%C4%9B,_180_%C3%97_180_cm,_2020.jpg) (*Bully*, oil on canvas) by [Klára Sedlo](https://klarasedlo.com), made available under the terms of the [Creative Commons Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
