---
layout: post
title: Developer Diary, World Standards Day
date: 2024-10-14 07:45:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Memory-plaque-of-founding-ISA-in-Prague.png
offset: -30%
teaser: This week's projects include the blog's code, preparation for The Light's Edge episodes, and another toy for The Light's Edge.
spell: LLL GFCI Luděk Kovář Unported
proofed: true
---

* Ignore for ToC
{:toc}

Today marks [World Standards Day](https://en.wikipedia.org/wiki/World_Standards_Day), which honors the experts and organizations in many fields who draft and develop voluntary technical standards.  Hug your local GFCI outlet and Unicode chart, in other words.

Oh, in the United States, we also have [Indigenous Peoples Day](https://en.wikipedia.org/wiki/Indigenous_Peoples%27_Day_%28United_States%29) and the thing about the weirdo who even the Spanish Empire said that his shenanigans seemed criminal in a land that he lied about until his death, but we politely pretend that he did something useful.

![ISA founding plaque in Prague](/blog/assets/Memory-plaque-of-founding-ISA-in-Prague.png "Oddly, not manufactured to any standard...")

Anyway, on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

I have started cleaning up the generated HTML for the blog.  A few weeks ago, an article about how the number of top-hundred or so websites that serve no errors has increased dramatically to...one.  I laughed at that, then realized that I had no idea what this blog looks like, in that respect.  After running the [Nu HTML Checker](https://validator.github.io/validator/) (v.Nu), oh, it looks like we have many, many errors on most pages.

Maybe we shouldn't laugh so hard at big businesses getting this wrong, then, right...?

Some errors seem unavoidable.  For example, Matrix room links---such as you find at the bottom of every page encouraging you to discuss whatever feels related to posts---have number-signs where the URL definition doesn't allow them.  Others come from sloppy coding on my part, so you'll start seeing minor corrections to get at those.  And a final set come from plugins, so I'll probably need to send them bug reports.

Alongside these changes, I have similarly continued trying to make small speed optimizations, based on feedback from [Page Speed Insights](https://pagespeed.web.dev/), apparently a Google thing.

Between the two, I hope that people see a better experience as they read.

## Cohost Archive

{% github jcolag/cohost %}

I now have my export, and have begun the work of creating a static archive of my posts to Cohost.

While I haven't uploaded any of the content, yet, I did push out the stylesheets that I intend to use, in case somebody wants to borrow them.  I used [**Boring CSS**](https://jcolag.github.io/boring-css/) as a basis, added a color scheme based on Cohost's---extending their four brand colors to the standard set of eight---and building some smaller styles for aspects of the generated code.

## The Light's Edge (Episodes)

{% codeberg jcolag/lights-edge-toys %}

It almost seems disappointing to bring this up, since I haven't yet posted any actual episodes, but the README documentation now feels more comprehensive.  The page now goes into detail on the requirements for contributors.

Oh, and it also points readers to relevant pages that they probably want to see, including adding the overall project blurb to the top.

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

As I started writing **The Light's Edge**, I realized that our initial protagonist---that space will eventually open up---should probably have spent a lot of his time on Earth getting around by skateboard.  It has the virtue of portability, doesn't require much explanation, and has potential down the line to stand out against the space opera as he becomes embroiled in the story.

![LLL-1 on his new skateboard, against a heavily edited domestic background](/blog/assets/lll-1-skateboard.png "I spent far too much time concealing that he rides on a wood floor past a cardboard wall, but I do like the results...")

Like the 3D Rail Runner model, this should scale fairly well to whatever size that you might need.  Past a certain size, though, you'll probably feel disappointed that the wheels don't work.  And no, I have no intentions of fixing that.  At that point, *build* a small skateboard and use actual toy wheels...

## Next

I should have my Cohost archive ready to post, soon.  You should probably expect me to replace any non-Free-licensed media with pointers to it elsewhere, but also expect a single page with all posts, where anybody so-inclined can link to an individual post within the page.

Also, you can probably bet on more work on **The Light's Edge**, and maybe another project.

* * *

**Credits**:  The header image is [Memory plaque of founding ISA in Prague cropped](https://commons.wikimedia.org/wiki/File:Memory_plaque_of_founding_ISA_in_Prague_cropped.jpg) by [Luděk Kovář](https://cs.wikipedia.org/wiki/Wikipedista:Gumruch), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
