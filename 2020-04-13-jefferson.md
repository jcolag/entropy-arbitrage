---
layout: post
title: Developer Journal, Jefferson's Birthday
date: 2020-04-13 07:21:12-0400
categories:
tags: [programming, project, devjournal, bicker, uxuyu, font]
summary: Progress on assorted projects
thumbnail: /blog/assets/Thomas_Jeffersons_Monticello.png
---

![Monticello](/blog/assets/Thomas_Jeffersons_Monticello.png "Monticello")

I've been *sort of* getting back into the swing of things after a couple of chaotic weeks.  This week still wasn't as productive as I would have liked, but it's still more than the "corrected a typo and updated some libraries" updates I've been making, and there are fewer things broken down around the house, so that's a victory, for now.

Now, about the actual progress for the week!

## Miniboost

I have continued tweaking [**Miniboost**](https://github.com/jcolag/Miniboost).

One change has been to hide any controls that aren't currently in use, such as collapsing the window to just the list of categories on startup.  It's a little bit ugly, but much less likely to cause grief.  Ideally, I should be able to disable the controls, as well, but I don't see that implemented in the [Proton Native](https://proton-native.js.org/#/) source code, yet.

Another change is an option to disable the file monitor.  I'm not completely sure that `setInterval()`/`clearInterval()` was causing me actual trouble, but it was a factor I wanted to easily introduce and exclude.  So, if the interval is configured as less than zero, the timer cancels itself.

I also noticed that I had over-engineered the actual note display, storing the note *plus* the note text, which was causing confusion and fouling up the exports.  That's now fixed with a clearer delineation between the data source for the editor and its destination.

## Uxuyu

Taking what I've been learning from working on **Miniboost**, I'm trying out Proton Native for another project, a desktop client for [twtxt]({% post_url 2020-03-21-twtxt %}).  Since Node.js finally has stable [worker threads](https://nodejs.org/docs/latest-v12.x/api/worker_threads.html), it seems reasonable to check for updates on feeds that aren't being officially "followed."

I call it [**Uxuyu**](https://github.com/jcolag/Uxuyu), taking each letter in "twtxt" and bumping it up by one.  Mentally, I hear the name as "Ooh Who You," or sort of the opposite of "ooh, yoo-hoo."  Those are all meaningless, but it's a name I don't see in use elsewhere, so that's what I'm rolling with.

I'm not convinced that Proton Native is up to the task, yet, but we'll have to feel that out as we go, I guess, because I have at least *started* the project...not that there's much, yet.

And if this works out, I'll probably revisit the mostly abandoned [**Zoea**](https://github.com/jcolag/zoea) project for [Scuttlebutt]({% post_url 2020-01-25-scuttlebutt %}), since what I needed there was quite similar to what I need here.

## Bicker

It is definitely not ready for use, but I took the first steps towards automatically adding previews for any URLs entered into a paragraph in [**Bicker**](https://github.com/jcolag/Bicker).

Discourse's [Onebox](https://github.com/discourse/onebox) gem does a surprisingly nice job of retrieving the summary content for a page and [Kramdown](https://kramdown.gettalong.org/) handles (most of) the conversion from HTML to Markdown.  It needs a lot more work to make this feature useful, but I think it's a good start that will pay off down the line.

## Seeking Refuge

Something that has bugging me since I released [**Seeking Refuge**]({% post_url 2019-12-14-seeking-refuge %}) has been my inability to get the couple of emoji I used to show up in the PDF and ePub files.  About a quarter of the way in, one of the story's characters sends a message that the narrator describes as representative of the following snippet.

 > أنا
 > 📥 # 单据, 👀 💴 fraud w00t

That intentionally messy bit of text is:

 * Arabic for "I am,"
 * A download icon,
 * A pound/number sign,
 * The Chinese word for "document,"
 * A comma,
 * Eyes,
 * Money (yen, in this case),
 * The English word "fraud," and
 * ...well, [w00t](https://en.wikipedia.org/wiki/W00t),

...in case there's some part of it you can't see on your system.  I think it's a nice character moment that contrasts with how the character actually speaks, but maybe was a step too far.

In any case, the quote shows up fine in every format *except* for the PDF and ePub files, as far as I can tell.  And in those case, they show up as blank spaces, but if you copy the line and paste it into another document, it's fine there, so the emoji are present, just invisible.  It was frustrating, but I couldn't find a solution and didn't want to sit on the book like I have other projects.

Going back to research this after a couple of months giving it a break, though, I discovered that this is a small, known bug in [LibreOffice](https://www.libreoffice.org/) regarding fonts that include *color*, so this probably won't be a permanent problem.  However, it's been almost four months of having a technically sub-standard product (the artistic merits are obviously open for debate...) floating out there and I don't like that at all.

The solution?  I just needed a black-and-white font that contains emoji.  I chose [Noto Emoji](https://github.com/googlefonts/noto-emoji/tree/master/fonts), the "Regular" version, released under the OFL.  It's definitely not as pleasant to look at...

![The emoji](/blog/assets/seeking-refuge-emoji-example-1-01.png "the emoji")

...but it survives into the PDF without compromising on only using free-licensed tools or spending days trying to figure out how to make something better, so the beady eyes will keep until the LibreOffice team can get around to fixing their problem.

Note that there's a much more pleasant font named "Symbola," but while several download sites describe it as being released to the public domain, not only could I not track down an official statement to that effect, but the original location is extremely clear that it's only licensed for personal use, making it effectively proprietary freeware and ruling it out of consideration.  Just be warned, if you run across it on your own.

## Next

Well, I'll continue on with **Uxuyu**, at least.

I would also like to minimally assign **Bicker**'s URL previews to a default user (which requires a default user...) and, time permitting, clean up the presentation so that nobody can reply to them.  Since some of the previews (like Twitter) have special formatting, it might be best to store them as HTML and insert them as-is, which will probably require modifying the schema.

I'd *like* to put **Miniboost** aside for a while, but because I actively use it, I assume that the clock is ticking until I add more features, like a status bar or an interface to create categories of notes or whatnot.  I'm happy with it as-is, but can always be happier with it.

* * *

**Credits**:  The header image is [Thomas Jefferson's Monticello](https://commons.wikimedia.org/wiki/File:Thomas_Jefferson%27s_Monticello.JPG) by [Martin Falbisoner](https://commons.wikimedia.org/wiki/User:Martin_Falbisoner), made available under the terms of the [Creative Commons Attribution-Share Alike 3.0 Unported license](https://creativecommons.org/licenses/by-sa/3.0/deed.en).  And yes, Jefferson *was* a huge hypocrite who preached equality out of one side of his mouth while protecting slavery (an institution some of his own children were born into) out of the other **and** he abandoned all of his alleged principles of governance the second he was elected President.  But naming the post "Tax Hangover" sounded like it was going to make the search for a header image much more difficult, so here we are...
