---
layout: post
title: Developer Diary, Battle of Cap-Français
date: 2026-06-22 07:58:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog]
summary: Progress on assorted projects
thumbnail: /blog/assets/cap-francais.png
offset: -26%
description: This week's projects focus on continuing to update the blog's code.
spell: rel sasquatch Exo incendie ville du Boquet Chapuy
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the anniversary of the end of the [Battle of Cap-Français](https://en.wikipedia.org/wiki/Battle_of_Cap-Fran%C3%A7ais_%281793%29), where (oversimplifying) the French occupiers, trying to stop the Haitian Revolution, made the mistake of fighting each other and recruiting slaves for the front lines with the predictable results of giving everybody the opportunity to rise up against the government.

![The city of Cap-Français in flames during the battle](/blog/assets/cap-francais.png "Only you can prevent the need to burn fascists out of the city...")

Over in Europe, Croatia celebrates [Anti-Fascist Day](https://en.wikipedia.org/wiki/Anti-Fascist_Struggle_Day), celebrating their World War II uprising against the Axis occupiers.

And with that, on to the week's projects.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Work has continued on overhauling---I hope *improving*---bits of the blog.

Completely behind the scenes, the "menu" across the top of the page (as in the nine icons in the upper right that take you around) now lives in its own file.  This gets ahead of what I'd prefer to talk about here, but it now feels like too many links to splatter across the top of the page like that, and I still have at least one more feature to add there someday, so it should probably turn into a proper drop-down menu, which would also provide the space to give each icon some readable-at-a-glance text (instead of the title-text tool tips) to ease figuring out which icon goes where.

More visible, the little pull-out panel describing the newsletter (at the bottom of the post on mobile) should now have a clearer and *shorter* explanation of [the newsletter](https://buymeacoffee.com/jcolag/posts/71215) and how to get it.  I'd like to include a sign-up form right there, but Buy Me a Coffee doesn't seem to support anything along those lines.

In addition, all the links that identify my pages to various services (the `rel="me"` hyperlinks) now get hidden, so I no longer need to worry about them randomly appearing when I change verbiage somewhere.  Every page should also have a "Skip to Content" link that jumps to the first heading; last week added the link, but not every page had somewhere for it to go.

My fix to the calculation for newsletter-day needed fixing, confusing integers with dates.

Fonts also got a refresh.  The emoji font now supports Unicode 17.0, so if I want to include a Sasquatch {% emoji sasquatch %}, an orca {% emoji orca %}, a trombone {% emoji trombone %}, or the other handful of new symbols, everybody should see the same thing on the website.  Likewise, I mentioned that the [Exo 2](https://ndiscover.com/family/exo-2/) font used everywhere now has (or always had, and I only now noticed/cared) a variable font version, which collapses all the weights into one font.  Or more importantly, this means that I can "dial in" the weights that look the best instead of the older situation of a probably too-light main body and an awkwardly dark bold, and if occasionally useful, a one-off phrase can show up <span style="font-weight: 1">as light</span> or <span style="font-weight: 1000">as heavy</span> as the range goes, or anywhere in between.  As either a bonus or nuisance depending on your preferences, using the bespoke *italicized* font uses slightly different letter-forms more readable in italics, such as the "single-story" *a*, *f*, and *g*.

And you might also catch some minor cleanup along the way, but nothing else of consequence.

Maybe usefully, in addition to things (literally) sounding good in my spot-checking with [Orca](https://gnome.pages.gitlab.gnome.org/orca/help/), the [Web Accessibility Evaluation Tool](https://wave.webaim.org/) gives most pages a 9.6--9.9 out of ten for accessibility impact, where a five represents an average page on the Internet, and they take fractions of a point off for things like a no-script element, under the pretext that most users with disabilities have JavaScript turned on.  I still have a long way to go on especially the [social media roundup](/blog/tag/link-dump) posts, which only hit around eight out of ten, and those results make me more comfortable even if that still technically rates as better than average on the Internet.

## Next

As mentioned, I'll probably start messing with the script that generates the Friday posts to improve their accessibility---I honestly forgot about them during all this---and I still have Scrawls to get back to, with actual progress that I haven't had time to commit.

* * *

**Credits**:  The header image is [Vue de l’incendie de la ville du Cap Français](https://commons.wikimedia.org/wiki/File:Vue_de_l%27incendie_de_la_ville_du_cap_fran%C3%A7ais_f1.highres.jpg) by J.-L. Boquet and J.-B. Chapuy (painter and engraver), in the public domain due to expired copyright.
