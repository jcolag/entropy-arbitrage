---
layout: post
title: Developer Journal, First Paleontology Lecture
date: 2022-04-11 06:50:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Mammut-americanum.png
proofed: true
---

Today marks the 226<sup>th</sup> anniversary of the first lecture on paleontology, *Mémoires sur les espèces d'éléphants vivants et fossiles* (*Memoirs on Living and Fossil Elephant Species*), delivered by [Georges Cuvier](https://en.wikipedia.org/wiki/Georges_Cuvier).  He would go on to coin the term [mastodon](https://en.wikipedia.org/wiki/Mastodon) for the ancient elephant that he had studied.

![Reconstruction of an American mastodon](/blog/assets/Mammut-americanum.png "All the pit's a stage...or something like that")

Is this my snide way of implying that some programming feels like paleontology, trying to reconstruct some ancient state of affairs based on scanty, decaying evidence?  Of course not.  That would be *archaeology*, not paleontology...

## G.L.O.B.E.

{% github jcolag/g-l-o-b-e %}

As discussed [last week]({% post_url 2022-04-04-telaviv %}), I finally finished the styling for the distance "traveled" in the game, so that it displays as green for the first third, yellow for the second, red for the final third, and white after "losing the game," to the extent that someone can win or lose identifying a country.

In addition, the styling now ensures that the country names can't overflow and skew the remaining table.

## Morning Dashboard

{% github jcolag/dash %}

It isn't a big deal, but to "soften" the appearance of the dashboard, the background now boasts a transparent texture, much like I use in most projects.  Along the way, I discovered that [Subtle Patterns](https://www.toptal.com/designers/subtlepatterns/) now survives as part of freelancing site Toptal, which...apparently doesn't understand that "<q>licensed under Creative Commons</q>" isn't specific enough for anybody to use; archived versions of the site still show that they mean CC-BY-SA, though.

I also updated a library version to keep the bots happy.  And that library update brings me to the general topic...

## Library Updates

I needed to bump library versions for [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Bicker**](https://github.com/jcolag/Bicker), [**RenewDB**](https://github.com/jcolag/RenewDB), and [**Library Twitterbot**](https://github.com/jcolag/library-twtterbot).  This cleared out the majority of my backlog, at least.

## Next

I discovered a bug in the **Morning Dashboard** where some subset of Thunderbird events shows up on the dashboard for the previous day.  Most likely, the code doesn't know about a flag or a time zone or something that can skew the effective date, but it'll still require investigation.

* * *

**Credits**:  The header image is [Mammut americanum Sergiodlarosa](https://commons.wikimedia.org/wiki/File:Mammut_americanum_Sergiodlarosa.jpg) by [Sergio De La Rosa](https://www.deviantart.com/serchio25), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
