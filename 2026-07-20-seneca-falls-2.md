---
layout: post
title: Developer Diary, Seneca Falls, Day 2
date: 2026-07-20 07:04:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, recipe, scrawls]
summary: Progress on assorted projects
thumbnail: /blog/assets/Wesleyan-Methodist-Church-Seneca-Falls-NY.png
offset: -26%
description: This week's projects include a sourdough recipe, the blog's code, the Scrawls editor, and a bunch of library updates.
spell: Tetrault endcook CPREP Fýlakas Onomáton Uxuyu Zirkel
proofed: true
---

* Ignore for ToC
{:toc}

While not nearly as important as some historians like to present it, today marks the 178<sup>th</sup> anniversary of the second/final day of the {% wiki Seneca_Falls_Convention|Seneca Falls Convention|en %}, the first *major* women's rights convention.  I emphasize "major," because too many histories ignore how many prior women's rights groups---especially *Black women*---coordinated and met with each other to share ideas.

![The remaining exterior walls of the Wesleyan Methodist Church in Seneca Falls, NY, with a blue New York landmark sign describing the convention](/blog/assets/Wesleyan-Methodist-Church-Seneca-Falls-NY.png "Susan B. Anthony not pictured here, either...")

After the Civil War, Seneca Falls became an important symbol, and so suffragists edited history a bit, including retroactively adding Susan B. Anthony to the attendees.  And they also used the convention as a gate-keeping tool, using the mythologized version to exclude people (like Lucy Stone) from the suffragist movement more broadly, as if not attending a hastily planned local meeting with no more than three hundred attendees determines commitment to the movement twenty years later.

I don't want to re-litigate the story, mind you, or undermine the value of the symbol to the women's rights movement.  Lisa Tetrault's **The Myth of Seneca Falls** actually does a fantastic job of putting the pieces together, though, for anybody interested in further reading.

If you want an even more bleak reading on a holiday than that, we also have {% wiki International_Chess_Day|International Chess Day|en %}.  I gather that celebrations have grown difficult over the past few years due to cheating scandals, Russia's political reputation in a Russian-dominated sport, and transphobic policies.

I can only really follow up on this (beyond people guessing where I land on the latter two scandals without too much trouble) that I tried *so hard* to like chess over the years, but could never take it seriously.  Eventually, I realized that I liked the idea of playing it, because I had internalized the stereotype that "smart people play chess" and either wanted to think of myself that way or thought that I should.  Once I realized that "trying to like things that smart people stereotypically like so that I can feel smart" sounded unspeakably goofy, I gave up on that, along with plenty of other things that convinced me to take myself far too seriously.

In other words, yes, I know how to play chess.  No, I don't know the notation schemes.  No, I won't play you; I don't have any urge to play a simulated war, but you should have fun if you do.

And with that, on to the week's projects.

## Recipe

In a maybe-ill-advised move (we'll see), it occurred to me that, if I seemed likely to make little loaves of bread in the air fryer on a regular basis, then I should give into the world of sourdough.  You all probably know me better than to imagine me saying something like this.

> Oh, sure, let me remember to coddle a jar every day and throw out a few cups of flour, so that I can make an appointment for sometime next week to bake bread.

After all, I don't exactly fit the fad of going from a busy social life to stuck at home during pandemic lockdowns, so maintenance to fill time doesn't appeal to me.  And yes, you can find a handful of recipes specifically for the discarded pre-stable sourdough starter, but that seems risky, and a middle-aged guy can only eat so much starch, nor do I want to adjust my diet to accommodate the starter.  Therefore, I poked around for how to make starters in general, small starters, no-waste starters, and fast starters...and then decided to wing it, based on what I saw, coming up with this.

{% cook 1|Minimal Sourdough Starter %}
Mix @rye flour{½%cup}, @water{½%cup}, and @yeast{¼%tsp} in a jar.

Let sit for ~{16%hours} in a warm location, loosely covered.

If the starter falls, mix in another tablespoon or two each of flour and water and let sit for ~{4%hours}.
{% endcook %}

No waste or much patience required.  Yes, I use volumetric measurements.  I want bread, not shaped explosive charges.  The specific brand's grind could maybe change how the flour packs, throwing off the balance on the starter slightly.  But I can probably eyeball that and fix it, which I might need to do working by mass, too.  Use fifty grams for half a cup, if you'd rather.  Oh, and more heresy, I also used an old (clean) glass peanut butter jar instead of something fancy.

### What Passes for Design Notes

Many recipes talk about rye flour as making the process as close to foolproof as possible, apparently nutritious for yeast but not welcoming to random microorganisms, and I bought some on a whim to pad out an online grocery order a while back, throwing it in the freezer in case I wanted to change things up.

A couple of recipes for faster starters talk about using commercial yeast to jump-start the process, getting it to the point of fermentation---which makes sense, since a no-knead bread takes about that long to fully rise---and then it'll pick up wild yeasts over time.  And as mentioned, I do have plenty of that Costco yeast in the freezer.

The no-waste starter recipes talk about feeding the starter small amounts every day during the week instead of another cup or so---traditionally, you deflate the in-progress starter, and move half of it starter to another container, then feeding the new container another cup of flour and another cup of water, tossing (or feeding and giving away) the rest---until it starts smelling...well, yeasty, instead of the unpleasant funk.  Since I started with functioning yeast, I only went with one small feeding the following morning, when the starter had fallen and stopped smelling.  The small extra feeding brought it back where I expected within an hour.

Anyway, given that it took combining three separate categories of recipe, that either means that I broke new ground this week *or* everybody has known about this for centuries and web searches have officially degraded past the point of utility.

### Maintenance

For minimal maintenance, the too-vaguely named "scrapings method" leaves some remnants of the starter in the jar after making bread each time, and...leaves the jar that way in the refrigerator until it needs to return for action, no feeding.  When required, give the scrapings more flour and water, and let it sit for however long to get bubbling and doubled in size again, pretty much like using the commercial yeast to kick it off.

The last part does mean *some* planning to make bread, because it needs feeding at some point before, specific duration TBD and probably dependent on temperature.  But I still have conventional yeast that I can use if I need a tighter schedule.  And if I find myself baking a *lot* of yeast-based foods, then I can always treat it like a more conventional starter, feeding it daily at room temperature or weekly in the refrigerator.

Mind you, it'll also take me a while to get "scrapings."  I ended up with about a pint of starter, which deflates back to a cup when stirred, and you generally use a tenth to a fifth of a bread recipe's flour in starter, so if the [air fryer bread]({% post_url 2026-05-25-missing %}) (all I'd likely bake until the temperatures drop) from a couple of months ago takes a cup of flour, that only calls for about three tablespoons (of eight) of starter, so I'll actually get another use out of the initial batch of starter, and will feed it a tablespoon or two with each use until the time comes for larger bakes, which'll extend it.

### Get to the Point

How did the bread turn out?  Uneven, but I don't think that I can blame the starter.

The moisture in the starter plus the humidity---I picked a terrible day to experiment, the height of the heat wave but before the wildfire smoke poured in---required more than a quarter-cup more flour to make it reasonable to knead, which probably needed a longer baking time at a slightly lower temperature.  I didn't do that, giving me a dense loaf with some undercooked spots.  I'd call it a promising sign for the next loaf, though, assuming that I add the water more carefully, next time; it did rise and brown nicely.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

I made a couple of changes that nobody will probably ever see.

The one that *I'll* encounter most often, I added a quick chime in the deployment script that alerts me that the build has completed.  At that point, the script starts moving the files to the server, so that signals to me that I need to post the announcements to any social media that I still use and haven't managed to automate.

Largely invisible even to me, I cleaned up how the site name lays out in the header source code.  I looked at it all on one line and didn't like it at all, so I broke it up as if I've actually used HTML for the past thirty years...

## Scrawls

{% codeberg jcolag/scrawls %}

Not much happened here beyond some minor maintenance.  The ignore-file no longer wastes my time with the Code Mirror library.  And speaking of the library, I added a quick shell script to find the latest version and unpack it for use.

## Library Updates

I needed to bump library versions for that the [Badging](https://codeberg.org/jcolag/badging) work that I need to get back to, the [CPREP background generator](https://codeberg.org/jcolag/cprep-background-generator), [Fýlakas Onomáton](https://codeberg.org/jcolag/fylakas-onomaton) [generic board game](https://github.com/jcolag/generic-board-game) that never became anything, my [morning dashboard](https://codeberg.org/jcolag/dash) that I haven't really used in well over a year and have designs on replacing, [Uxuyu](https://github.com/jcolag/Uxuyu)

## Next

I have a maybe-bad idea for the blog that could make for an interesting post regardless, work to do on Scrawls, and probably more library updates, as I get my act together after a week of the aforementioned heat and wildfire smoke.

* * *

**Credits**:  The header image is [Wesleyan Methodist Church Seneca Falls NY](https://commons.wikimedia.org/wiki/File:Wesleyan_Methodist_Church_Seneca_Falls_NY.jpg) by [Kenneth C. Zirkel](https://commons.wikimedia.org/wiki/User:Kzirkel), made available under the terms of the [Creative Commons Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
