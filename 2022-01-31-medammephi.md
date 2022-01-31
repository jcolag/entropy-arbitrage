---
layout: post
title: Developer Journal, Me-Dam-Me-Phi
date: 2022-01-31 06:59:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Mae-Dam-Mae-Phi.png
proofed: true
---

Among the [Ahom](https://en.wikipedia.org/wiki/Ahom_people), today is [Me-Dam-Me-Phi](https://en.wikipedia.org/wiki/Me-Dam-Me-Phi).  Like many winter holidays, it's easy to spot two roles, here.  On the surface, the holiday is literally about gifting to the family ancestors and sacrificing to the gods.  However, the deeper reality is that it brings the community together to create bonds between generations and promote a feeling of brotherhood.  It's obviously not widespread, but I think that we can all recognize something like Me-Dam-Me-Phi.

![A Me-Dam-Me-Phi service](/blog/assets/Mae-Dam-Mae-Phi.png "I know that it's unlikely, but I'm weirdly paranoid that the signs are either ethnic slurs and/or brand names...")

While we're still using holidays to fend off the winter, let's look at some projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

I spent a few days refining the GitHub plugin.  The big changes are:

 * The preview and title now have a tooltip (title text), for better readability and accessibility.
 * The test scaffolding now has an option---described in my post about [testing Jekyll plugins]({% post_url 2022-01-26-test-jekyll %})---to print a full execution trace of the test, to help ensure that the right paths through the plugin code get executed.

On the administrative side, the cache now gets deleted when rebuilding the blog, and git ignores the cache, in case there's something left over from the previous build.  The trace isn't as readable as I would like, but it provides any information that might be needed.

## Morning Dashboard

{% github jcolag/dash %}

I have improved the representation of sunrise and sunset on the dashboard---including adding dawn/dusk times to the sunrise/sunset times, to have a better sense of natural light---formatting the times in the date information, and adding "transitional" coloration for the sunrise and sunset hours.

Maybe more interesting to some people, as heavy snows hammered my area---if you're reading this, then I *probably* survived with power and Internet intact, thanks---I started looking at the bits of data that I wasn't using in the National Weather Service data.  One hourly field that I didn't bother to examine previously is the [quantitative precipitation forecast (QPF)](https://en.wikipedia.org/wiki/Quantitative_precipitation_forecast) number, a forecast of the depth of the precipitation *if* it melted.

The QPF doesn't directly give a snowfall total---the difference between snow depth and rain depth varies with how wet and densely packed the snow is---but it *does* give a good idea of how hard it's going to be to shovel.  It also provides an upper and lower bound to the depth, generally somewhere between five and fifteen times the QPF depth.

The documentation has also gotten an update.

## Next

I'm honestly not sure.  I'll probably continue tweaking things and get to those library updates, but that's an easy answer, so maybe I'll change direction.

* * *

**Credits**:  The header image is [Mae Dam Mae Phi](https://commons.wikimedia.org/wiki/File:Mae_Dam_Mae_Phi.jpg) by [Sairg](https://commons.wikimedia.org/wiki/User:Sairg), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/) license.
