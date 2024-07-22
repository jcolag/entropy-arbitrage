---
layout: post
title: Developer Diary, Ratcatcher's Day
date: 2024-07-22 08:03:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/ma-131907.png
offset: -15%
teaser: This week's projects include fiddling with a 3D printer, the blog's code, blog posts, and the Fictopedia archive.
spell: LaTeX MathML fictopedia frac lim sqrt overset underset mathrm Ratcatcher Anycubic Kobra Prusa GreenBit Mathjax Hôpital bâtiment avec les mais ce maintenant LaTeX
proofed: true
---

* Ignore for ToC
{:toc}

{% include mathjax.html %}

Depending on where you are, today *might* celebrate the oh-so-appealing-sounding [Ratcatcher's Day](https://en.wikipedia.org/wiki/Ratcatcher%27s_Day), commemorating one of two dates that medieval traditions used for the story of [*The Pied Piper*](https://en.wikipedia.org/wiki/The_Pied_Piper_of_Hamelin), but also honoring literal rat-catchers and presumably most modern exterminators.

![A Japanese statue of a rat-catcher upset at the rodent crawling over his neck instead of into his trap](/blog/assets/ma-131907.png "I've had programming projects that worked like this...")

And on we go to the projects.

## New Hardware

I couldn't find an Open Source Hardware solution in the (extremely low) price range that I wanted to consider, but I have purchased a cheap 3D printer...which I don't really have the space for, but I'll worry about that some other time.  I have had some ideas for [**The Light's Edge**](https://www.thelightsedge.com/)'s pseudo-merchandise, for one major expected use, and many of those ideas require the physical artifact to work with.  Somebody asked me about prices last week, and quickly discovered that they come fairly cheap, these days.

If you want the specific and boring details, I ordered the [Anycubic Kobra 2](https://store.anycubic.com/products/kobra-2) on sale, and it arrived far sooner than I expected.  It then took an obscene couple of hours to assemble, because their instructions don't really bother with things like "clarity in which direction the observer faces" in their sketches, but between the instructions and the shipped video, I finally got it to auto-level correctly.

Grabbing [Prusa Slicer](https://www.prusa3d.com/page/prusaslicer_424/) and adding [GreenBit's profile for the printer](https://www.printables.com/model/710525-my-prusa-slicer-profile-for-anycubic-kobra-2-pro/files)---Click *Menu*, *File*, *Import*, *Import Config...* to add it---got it running, at least, and the example boat that everybody uses for calibration looks fine.

I don't know how much use it'll get overall, but I'll want to start prototyping toys for [**The Light's Edge**](https://www.thelightsedge.com/) soon.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

This week's work mostly cleaned up last week's work, honestly.

For example, I added and updated styles for the heading anchors---the link emoji to the right of each heading---the transitions for the table of contents, and the general look of embedded posts, including a bogus "verified" icon.  Similarly, I added a unique name for the "sleeping" {% emoji sleeping %} emoji.

Maybe more interestingly to some, because I started rambling about [Planck units](https://en.wikipedia.org/wiki/Planck_units) and [gravitational binding energy](https://en.wikipedia.org/wiki/Gravitational_binding_energy) in the [**ST:TNG** *New Ground*]({% post_url 2024-07-18-new-ground %}) post, I assembled ideas from a bunch of pages and put together an I-hope-working-for-everybody way of adding [Mathjax](https://www.mathjax.org/).  This means that I can now insert arbitrary mathematical expressions in a post, such as $$\frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$ the [quadratic formula](https://simple.wikipedia.org/wiki/Quadratic_equation) for one that most readers will probably at least recognize.  But we could also do something fussier, like $$\lim_{x\to 0}{\frac{e^x-1}{2x}} \overset{\left[\frac{0}{0}\right]}{\underset{\mathrm{H}}{=}} \lim_{x\to 0}{\frac{e^x}{2}}={\frac{1}{2}}$$, an application of [L'Hôpital's rule](https://en.wikipedia.org/wiki/L%27H%C3%B4pital%27s_rule)[^1].

[^1]:  Despite no connection to Free Culture, I have a contractual and moral obligation to explain that "it’s a big building with patients, but that’s not important right now[^2]," or rather "*c’est un grand bâtiment avec les patients, mais ce n’est pas important maintenant*."

[^2]:  The rest of you can ask your nearest middle-aged person [or Wikipedia](https://en.wikipedia.org/wiki/Airplane!), I guess, though the former will enjoy the conversation more.  Also, I now find myself trying to calculate the probability that somebody will figure out where I went to school based solely on that one joke...

Most usefully for some applications, you can click on the math to get a zoomed-in version in a pop-up, or right-click for a context menu that'll give you the [$$\LaTeX$$](https://en.wikipedia.org/wiki/LaTeX) or [MathML](https://en.wikipedia.org/wiki/MathML) equivalent, in case you need to reproduce something that I did elsewhere.  I [played with MathML]({% post_url 2023-09-11-nayrouz %}) with similar intentions almost a year ago, but that went nowhere, and this makes a tidier solution, I think.

If I ever get around to talking actual computer science in a post---I'd like to find *something* to do with my [old lecture notes]({% post_url 2020-01-19-teaching %}), after all---this should come in handy.

## Entropy Arbitrage...but the Posts, Now

{% github jcolag/entropy-arbitrage %}

I continued the process of propagating the "What do we mean by *less well*?" blurbs to older [Free Culture Book Club](/blog/tag/bookclub) posts, to probably nobody's surprise.  I got another two batches out, each covering six months apiece.

Honestly, it seems worth confessing that this minor task has entertained me, somewhat, because it reminds me of a lot of really solid projects---and projects that somebody could *make* solid---that we've discussed over the last few years.  Otherwise, it still looks like drudgery, grabbing a batch of old book club posts and pasting in the line.

## Fictopedia Archive

{% codeberg jcolag/fictopedia %}

Likewise, the process continues of cleaning up the links, page-by-page, to make sure that links with destinations will actually point *to* those pages, instead of some alias.  And as with last week, I've added a license statement to every page that I touch.

This entertains me, too, though less than reviewing the old book club posts, since I need to look at every link on every page, and figure out how it broke or why it looks broken.  My favorite breakage, I think, looks like the conversion-from-wiki algorithm taking a wiki reference with an offset---it looks something like `The_Page#The_Heading`---and turning that to HTML by slapping an extension on the overall string, so `The_Page#The_Heading.html`, where the page name might also serve as an alias to the real page and the heading ID will probably have the wrong casing.

In any case, I've finished pages starting with the letter *K*, if you want to explore...

## Next

Like last week, for the upcoming week, I would expect me to continue cleaning up blog posts---adding the "Less Well" explanation and then adding tables of contents---and continuing to clean up the Fictopedia posts.  I might change my mind in a couple of days, but this seems like the most likely path until I finish off those tasks.

* * *

**Credits**:  The header image is [Frustrated Rat Catcher / 鼠捕り](https://collections.lacma.org/node/188349) by an unknown artist, long in the public domain due to either an expired copyright or no original copyright.
