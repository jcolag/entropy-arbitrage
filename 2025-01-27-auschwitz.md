---
layout: post
title: Developer Diary, Liberation of Auschwitz
date: 2025-01-27 07:55:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, dashboard, javascript, newsletter, open-badges]
summary: Progress on assorted projects
thumbnail: /blog/assets/Auschwitz-Liberation-1945.png
offset: -38%
description: This week's projects include the blog's newsletter, the blog's code, my morning dashboard, and Open Badges.
spell: OpenSCAD const
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the eightieth anniversary of the [Liberation of Auschwitz concentration camp](https://en.wikipedia.org/wiki/Liberation_of_Auschwitz_concentration_camp) by the Soviet [Red Army](https://en.wikipedia.org/wiki/Red_Army), rescuing the seven thousand or so prisoners not killed or brutally transferred.  As a result, [International Holocaust Remembrance Day](https://en.wikipedia.org/wiki/International_Holocaust_Remembrance_Day) commemorates the event and mourns the losses at the camps.

It shouldn't feel relevant eighty years later, but in the past week, the United States has seen the start of mass deportations---a "Final Solution" had *prior* attempted solutions, remember---and a recommendation of literal ethnic cleansing in Palestine, so...

![Prisoners of the Auschwitz Concentration Camp after their release](/blog/assets/Auschwitz-Liberation-1945.png "I can't help liking the fellow in front, the only person who seems to realize that somebody set up a camera because of the symbolic importance of the event")

And on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the first.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the fourth of February.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For October, I wrote a piece on XYZ, something of an ode to PBS, discussed my media consumption, and provided some background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage %}

A kind reader pointed out that I managed to get the [Project Gutenberg](https://www.gutenberg.org/) annotation icon wrong, showing up as some squiggly blob.  Looking the correct Unicode value up, it became clear that, yes, I apparently misread a six as an eight.  That, therefore, now should show correctly.

While I had to dig in there anyway, I also added icons for [FreeCAD](https://www.freecad.org/), [OpenSCAD](https://openscad.org/), [Laravel](https://laravel.com/), and [Mercurial](https://www.mercurial-scm.org/), since I saw them seeing use in recent or upcoming posts.  And I added a second [SourceForge](https://sourceforge.net) domain that an upcoming post will need.

## Morning Dashboard

{% github jcolag/dash %}

This will take some explanation, despite the minimal code.

As I've mentioned before, I increasingly rely on the library-sponsored streaming services for my (non-Free Culture) entertainment needs.  Recently, I discovered that [Hoopla](https://www.hoopladigital.com/) periodically makes "bonus borrows" available, works from across the site that members can borrow without it counting against their credit balance.

Investigating, it turns out that they always do this for the last seven days of the month.  Therefore, I wanted to add a fake calendar event to my **Morning Dashboard** for those seven days, to remind me to take advantage of what they have on offer, if it interests me...and if I have the time.

```JavaScript
const now = new Date();
const events = [];
if (now.getDate() >= new Date(now.getFullYear(), now.getMonth() + 1, -7).getDate()) {
  events.push({
    name: 'Check for Hoopla Bonus borrows'
  });
}
```

In short, the above code creates a date for the negative-seventh day of the next month, to give us the last seven days of this month, for example, this gives us the 25<sup>th</sup> for January.  If today's date (the 27<sup>th</sup>) lands at or after that day, then it pushes the bogus event onto the list.

Personally, it would've pleased me more to put this on my calendar, so that the existing code would automatically pick up the information.  Thunderbird's calendar, however, doesn't have the idea of "the last *N* days of the month," so this works around that lack.

## Badging

{% github jcolag/badging %}

A recent conversation reminded me that [Open Badges](https://openbadges.org/)---formerly a Mozilla project, which they have since left for community development---exists as a standardized concept.  Because [I taught for many years]({% post_url 2020-01-19-teaching %}), I previously thought about this in the context that Mozilla and 1 EdTech intend it, as a micro-credentialing standard for continuing education.

In short, skipping a bunch of steps, a badge consists of an image with metadata that verifiably asserts the awarding institution, the recipient, and the reason(s) for the badge.  The institution can store them.  Students can store them in "backpack" applications.  Or, if the institution goes with this "fully baked" badge scheme that embeds all the metadata into the image file, the students could *also* make any webpage as a low-rent version of the backpack thing, where anybody can see what they've accomplished and validate the claims.

Despite the grounding in education, though, that conversation sparked the idea that many communities---Free Culture came immediately to mind---could use the same or a similar scheme to reward collaborators or (eventually) maybe even hand out awards for exceptional work.  For a tacky but few-moving-parts example, I---or, more specifically, the blog---could release a "Featured in the [Free Culture Book Club](/blog/tag/book-club)" badge for each author whose work gets covered, so that interested authors have the option of using that on the project page.

With all that explained, this new repository will house my attempt to create a minimal script that'll create those "fully baked" badges.  At this time, the code will (I hope correctly) insert metadata into a PNG-format image file, which should do the job, **if** you have the proper metadata.

I don't know if anybody---including myself---will actually find a use for it, but the idea caught my interest enough that it seemed worth minimizing the burden of creating the badges to see how it shakes out.

## Next

Expect me to work more on **Badging**, as I dig through the specification and work out how to get the metadata right, validate it, and otherwise make sure that somebody can't counterfeit it.

* * *

**Credits**:  The header image is [Auschwitz Liberation 1945](https://en.wikipedia.org/wiki/File:Auschwitz_Liberation_1945.jpg) by an unknown photographer, in the public domain due to an expired Russian copyright.
