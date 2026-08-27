---
layout: post
title: Developer Diary, Esmet-Akhom Graffito
date: 2026-08-24 08:03:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, recipe, scrawls]
summary: Progress on assorted projects
thumbnail: /blog/assets/Esmet-Akhom.png
offset: -26%
description: This week's projects include a Wikipedia update, my mini-server, a recipe, my Scrawls editor, the blog's code, and some library updates.
spell: graffito Esmet Akhom Achom Mandulis Pinebook Roku tsp endcook tsp miso Bridgy Twitterbot Scuttlers Miniboost Uxuyu Agilkia Tausch Unported
proofed: true
---

* Ignore for ToC
{:toc}

August's most important anniversary, as everyone definitely already knows and has out their party hats, celebrates the carving of the {% wiki Graffito of Esmet-Akhom %} 2,419 years ago, seemingly the final native writing in Egyptian hieroglyphics.  The ragamuffin priest apparently wanted {% wiki Mandulis %} to protect his inscription---apparently not the temple, the culture, his favorite restaurant, or whatever---for all eternity.  No, really.  Go read.  I'll wait here...

![The graffito in question](/blog/assets/Esmet-Akhom.png "Does Mandulis have a city on his hat?  Carmen Miranda would seethe in jealousy...")

And with that, on to the week's projects.

## Wikipedia

I don't know how much time that I'll have for it, but I signed up to participate in the [Organized Labor Month Online Campaign](https://meta.wikimedia.org/wiki/Event:WikiProject_Organized_Labour_Month_Online_Campaign) at Wikipedia.  In solidarity with [Wiki Workers United](https://wikiworkersunited.org/), they want to create, translate, or update a thousand pages related to the labor movement during September.

## Mini-Server, part 30

Technically more about hardware in general, but to bring some old hardware back into service, I finally broke down and ordered from Amazon for the first time in a long time.

- Power adapter intended for my old Pinebook, which would make a fantastic "spare" laptop or "client" to the other machines.
- Battery for an old Android tablet, which could at least run [Briar Mailbox](https://code.briarproject.org/briar/briar-mailbox), and also potentially let me experiment with the non-Google Android systems, to see if they'll run the apps that I need to replace Roku.
- Thermal paste to get that old mini-PC running, since it actually has some heft to it.

Unfortunately, I haven't had much luck, so far.  The power adapter plugs in and *starts* charging, but then stops; the base plug also gets dangerously hot, even with nothing plugged into the other end.  They also sent me the wrong battery; I tried plugging it in anyway, but only got a red light for my troubles.

The opportunity hasn't arisen to try reseating the heat sinks on the mini-PC, but I can only assume that they shipped me a tube of bird guano instead.  And I suppose that it all serves me right for assuming that I could trust Amazon...

Also, it doesn't seem to work for me, but I installed and hope for improvements to [FFmpeg web CLI](https://tejaswigowda.com/ffmpeg-webCLI/), an in-browser video editor...at least hypothetically.  The `docs` folder has a full static application that *seems* capable of running anywhere with [`ffmpeg`](https://www.ffmpeg.org/) installed.  In practice, though, other than the *Media Info* function, everything else errors out, whether I get the page from a Raspberry Pi (with FFmpeg built for the ARM architecture), the mini-PC (an Intel-based architecture), running locally as found near the end of the documentation (also Intel), and the site that I linked to.  I suppose that, since it runs in the browser, maybe my system doesn't have enough memory for it.

It seems pretty nice, though, so I do *hope* that it has some small bug that someone will correct.  And I suspect that others will appreciate it, so I wanted to share the thing in case it only fails because of my machine's limited memory.

## Recipe

I planned for at least one more interesting idea to drop in here, but (I'll describe below) it went awry, sending me scavenging for equipment that might solve the problem(s) that I ran into.

### Bread Again

It took me a few tries over the past month, but I think that I finally have the approach to making sourdough bread in the air fryer, using the [minimal sourdough starter]({% post_url 2026-07-20-seneca-falls-2 %}#recipe) that I worked out last month, based on the [air fryer bread]({% post_url 2026-05-25-missing %}#recipe) from three months ago.  I seem to have good luck with bread at the end of the month...

{% cook 2|Air Fryer Sourdough Bread %}
Combine @flour{¾%cup}, @sourdough starter{¼%cup} (fed and active), @salt{¼%tsp}, and @sugar{1%Tbsp} in a bowl.

Stir in up to @water{1%Tbsp} (probably less than 1 tsp at a time) and @olive%oil{1%Tbsp} to get a shaggy dough.  If it sticks, add a teaspoon or so of flour.  If it seems too dry, add half a teaspoon or so of water.

Knead the dough for ~{5%min} until elastic and smooth.  Form it into a ball and let it rise in the mixing bowl, covered with a towel until it doubles in size, at least ~{5%hr}.

Move dough to the air fryer basket on a sheet of parchment paper.

Set the air fryer for 380°F (195 C) and bake for ~{5%min}, then lower the temperature to 330°F (165 C) for at least ~{10%min}, until golden brown on top and a hollow sound when tapped.  Check later in the bake and cover the top with foil if it browns too fast.

Flip the loaf and bake for another ~{5%min} or until the underside no longer looks and feels raw.

Let rest for ~{10%min}.
{% endcook %}

My air fryer operates on a kind of slide-out bucket with a grate supporting the food (and the heating element above), so I also poured some water down there before adding the bread, but didn't put that in the recipe as air fryers evolve back into convection ovens with doors in front and heating elements in other spots.  But if you bake, you can probably see where this goes.  The sugar fuels the yeast's reproduction, letting the dough rise better.  Then, the steam from that added water combines with the initial blast of heat for the bread itself to rise more evenly, instead of the crust solidifying quickly and constraining the baking dough.

I almost forgot:  The dough itself also gets little-to-no new water, because the starter uses a one-to-one ratio of flour and water, so a quarter-cup of starter[^2MZcsV] carries about a quarter-cup of water in the starches.  It took me far too long to work that out.  My first little sourdough loaves ended up needing up to half a cup more flour to soak up the water that I assumed that the dough needed, leading to more mass, which wouldn't cook evenly.

[^2MZcsV]:  The recipes that I've seen suggest using enough starter to make up about fifteen-to-twenty percent of the total flour in the non-sourdough recipe.  For a cup of flour, which would come to a bit more than three tablespoons, not the four tablespoons in a quarter-cup.  However, a full quarter-cup increases the gas production a bit more if the bread could use it, *and* means that I don't need to tell you to add three-and-a-seventh tablespoons of starter to four-fifths of a cup of flour.  And nobody has any need to conserve starter, because you only need to give it flour and water to get as much as you might want in a few hours...

As a result, the crust browned more---probably leftover sugar---but came out soft and sliceable, more like what you'd expect by "bread" than the sort of biscuit-like hard crust that I usually get.  On top of that, everything inside rose and baked evenly, with nicely distributed bubbles.  Oh, and it tasted pretty good, too.  It actually came out well enough that I sliced up the leftovers and froze them, rather than finding uses for increasingly stale bread.

The flaws?  This now takes planning.  I already needed to take the starter out of the refrigerator and feed it the night before, but this also adds mixing and kneading the dough in the morning.  But it only spreads the work apart, rather than adding to it.  And this should work nicely when the cooler weather returns and I go back to no-knead half-loaves.  Since I let the dough sit to develop its gluten for almost a full day in those cases, it should work well to pull out the starter and feed it in the morning, mix the dough around dinner time, and have it ready to bake the following night, which doesn't add anything to the process other than feeding the starter instead of using yeast.

### Other

Since I teased it last week and don't have it for this time around, I should mention that I also *tried* to make my own {% wiki tempeh %}.  I found a "recipe" for making it with sunflower seeds, and gave it a try with some my fancy new starter.  After almost two days, though, I didn't see any growth, so I tossed it, in case it went bad.

Most likely, I didn't start it off with enough heat.  It needs to stay at around 90° F (32 C) to grow and ferment, and even on a couple of hot days, I couldn't reliably keep its shelf that warm.  I have already started over...

Oh, and someone might also find it interesting that I made a celery and almond salad, with chopped dates and miso.  It felt like a complete meal to me, but your stomach might differ.

## Scrawls

{% codeberg jcolag/scrawls %}

I didn't make as much solid progress as I wanted to on the editor, but the editor objects now carry more metadata for future use.

The editor also uses the browser's local storage to track open files.  It displays those files as an approximation of tabs for a multi-document interface.  The tabs don't *do* anything, but they look like tabs and list "open" files, which provides plenty of room for expansion.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Mostly, the coloration of last week's content boxes should have improved readability in both light and dark modes.

However, I noticed that the [web mentions]({% post_url 2024-03-13-indieweb-1 %}) work that I did a couple of years ago stopped working.  Part of this, I needed to re-authenticate to [Bridgy](https://brid.gy/)...I think.  But I also discovered that the plugin that I use to insert the mentions into the posts had fallen pretty far out of date.  Trying to upgrade it in isolation wouldn't work because of a conflict, so I upgraded everything.  And rejoice, because it didn't break anything.  And after a couple of tries---more rigorous testing this week, before I announce anything---web mentions have started trickling back in.

Also, in trying to debug that issue, I noticed that I still preloaded an old version of the main body font, rather than the variable font that I started using a few weeks ago.  That should no longer waste time loading something no longer used.

## Library Updates

Apart from the blog's libraries, I also needed to bump library versions for my old [generic board game](https://github.com/jcolag/generic-board-game) nonsense, my obsolete [library Twitterbot](https://github.com/jcolag/library-twtterbot), [Little Scuttlers](https://github.com/jcolag/LittleScuttlers), my [Mastodon Tool Trunk](https://codeberg.org/jcolag/tool-trunk), [Miniboost](https://github.com/jcolag/Miniboost), and [Uxuyu](https://github.com/jcolag/Uxuyu).

## Next

Code-wise, I'd expect more of the same.  The blog has some changes in store.  Scrawls verges on usefulness.  Library updates continue to pile up.

Beyond that, I have the start of an idea for a small new project, and would like to find a process for making tempeh that works, especially with cooler weather setting in.

* * *

**Credits**:  The header image is [Agilkia Esmet-Achom](https://commons.wikimedia.org/wiki/File:Agilkia_Esmet-Achom_02.jpg) by [Olaf Tausch](https://commons.wikimedia.org/wiki/User:Oltau), made available under the terms of the [Creative Commons Attribution 3.0 Unported](https://creativecommons.org/licenses/by/3.0/deed.en) license.  The photograph, not the carving itself, which probably never had a copyright at all.
