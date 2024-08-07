---
layout: post
title: Developer Journal, Mendeleev's Birthday
date: 2021-02-08 07:24:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Medeleeff_by_repin.png
offset: -28%
---

* Ignore for ToC
{:toc}

![Dmitri Mendeleev](/blog/assets/Medeleeff_by_repin.png "Dmitri Mendeleev")

We're light on holidays, this week, so it's the 187<sup>th</sup> birthday of [Dmitri Mendeleev](https://en.wikipedia.org/wiki/Dmitri_Mendeleev), the Russian chemist who (among other things) worked out the form of the [periodic table of elements](https://en.wikipedia.org/wiki/Periodic_table) that we're still familiar with.

It's also the 170<sup>th</sup> birthday of early feminist author [Kate Chopin](https://en.wikipedia.org/wiki/Kate_Chopin).

## Picture to Nonogram

The **Picture to Nonogram** puzzle generator is nearing completion.  This week has included adding a slider (after solving the puzzle) to change the opacity of the image to help see where the pixels should line up, with the image---except for extreme situations---aligned on the grid.

I have also started the process of adding an undo feature, currently just tracking the user's actions.  There were other small changes, like actually exporting the generated HTML and cleaning up the CSS, but the slider is probably the headline.

## Next

As mentioned, **Picture to Nonogram** is probably near the end of development.  I definitely need to clean up the finish the undo feature.  I also want to fiddle with the resizing code, since I still get the occasional puzzle that's around five times the size of the typical puzzle; it probably needs to iterate until the size is within the desired boundaries.

Otherwise, it might be worth adding a timer for entertainment purposes.  It could clean things up to extract a lot of the static HTML into an external file, too.

To be used for competitive purposes, the page would also need to be secured against someone opening the developer tools and dumping out the grid and/or making the image visible, but I don't know that I'm *that* ambitious.

* * *

**Credits**:  The header image is [Medeleeff](https://commons.wikimedia.org/wiki/File:Medeleeff_by_repin.jpg) painted by Ilya Repin in 1885, and so long in the public domain.
