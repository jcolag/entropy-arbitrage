---
layout: post
title: Logos for Dystopias
date: 2026-07-29 07:52:05-0400
categories:
tags: [programming, tech-tips]
labels: [inkscape]
summary: Messing with Inkscape for no particularly good reason
thumbnail: /blog/assets/3967682030_6e9b2edecc_o.png
offset: -26%
description: Creating an ominous science fiction logo with all (well, most of) the clichés.
spell: LIBERAT Eurostile Librestile Michroma OFL monaspace pointiness
proofed: true
---

![A sketch of a hand sketching something, in this case the finished logo from the post](/blog/assets/3967682030_6e9b2edecc_o.png "Thank you, Thing...")

A couple of months ago, I put together a post---not entirely serious, but also not entirely joking---about how [corporate personhood might provide an opportunity]({% post_url 2026-05-31-free-corporation %}) to wipe out almost every exploitative organization.  I won't rehash that blog post, but at the end of the post, I joked that the idea could probably gain some traction with the cynical addition of a clichéd dystopian logo for hypothetical branded merchandise, coming up with this example.

![A goofy logo reading LIBERAT,INC but with the letter forms modified along science-fiction lines, exaggerating some pointy corners, rounding other corners, extending some legs to join letters, and so forth](/blog/assets/liberatinc.svg "It still makes me giggle...")

Maybe surprisingly, I haven't gotten any feedback on such an off-the-wall (but shockingly viable) idea, not that I get much feedback in general.  However, someone *did* contact me to ask how I put the logo together.  As a change of pace for the [tech tips posts](/blog/tag/tech-tips), then, we can talk a bit about [Inkscape](https://inkscape.org/) instead of programming and play with vector graphics.

For the possible changes to apply, I somehow mentioned in a *different* post that I looked to this post on [clichéd futuristic typography {% cc %}](https://typesetinthefuture.com/2016/02/18/futuristic/), but it gives a strong impression that artists do the work manually, which I don't do particularly well.  In other words, I needed to work out how to make all this work on my own without too much skill on my part, but the conceptual framework that I used deserves some credit.

Rather than using the imaginary organization from the other post, in this case, I'll use the blog's official name that I rarely actually use:  Entropy Arbitrage.  I probably won't use it for the website, because I find this style more kitschy than anything else, but it should make an interesting example, and I won't need to waste time on the punctuation.

## Font Selection

The conventional wisdom says that we should use Eurostile Bold Extended, but I haven't found a Free-licensed Eurostile-like font that looked decent.  For example---I point at this in case somebody who enjoys messing with fonts wants to get involved with or fork the project, not to criticize the work---I can find [Librestile](https://github.com/ocelothe/librestile), but so many of the letters give me a queasy feeling, the lowercase-*t* probably the clearest example.  [Michroma](https://gwfh.mranftl.com/fonts/michroma) doesn't seem to have its own bold, italic, or extended versions, and it similarly has a bunch of letters that don't seem to fit.  (If you don't care about Free licensing and want to go all-in on the trope, feel free to buy a real Eurostile license.)

Therefore, I'll need to drop the conventional wisdom.  The logo above uses OFL-licensed [League Gothic](https://www.theleagueofmoveabletype.com/league-gothic), which I admittedly chose because it shares similar features to the Eurostile concept while also looking woefully out of place.  For this example, I'll start with GitHub's recent [Mona Sans](https://github.com/mona-sans), also made available under the terms of the OFL.  For all GitHub's problems and cratering reputation, they *have* produced a bunch of fairly good fonts recently, such as the (presumably related) [monaspace](https://monaspace.githubnext.com/) set of code fonts.  It even has a specific Heavy Expanded Italic (as in extremely bolded, wide, and italicized) version.

## The Base

Now, even though Mona Sans has italicized versions---where we can generally assume that the designer took pains to preserve legibility instead of hoping that software tilting the letter forms looks nice---we'll need to make enough changes that starting with italics might confuse us as we work, so we'll italicize last, manually, even though that means somewhat worse results than we might get otherwise.

![The Entropy Arbitrage name, all-caps, in Mona Sans](/blog/assets/future-logo-entropy-arbitrage-0.svg "Step zero")

Now that we have something to work with, in Inkscape's menu, select everything with the Selector Tool.  Then, open the *Text* menu and click *Text to Glyphs*; you'll see the selection break apart from one unit to one for each letter.  Then, with everything still selected, under the *Path* menu, click *Object to Path*.  This creates one outlined shape (where we can and will modify the outline) for each letter.

## Angles and Curves

With a basis, we'll need to hit probably the most complicated part, here, or at least the part that required the most research and experimentation on my part, turning some corners into curves.  Maybe the italics thing rates as most complicated in terms of explaining it...

Before starting, because this starts to look terrible if we don't have *consistent* curves (height, angle, and curvature), I'll suggest dropping a horizontal guide along the bottom of the upper arms of the *T* and *E*.  For the last logo, I went through editing the nodes on the curvy letters so that the upper arm had the same thickness across everything, but I don't know that we need it here.

Here comes the annoying part, letter by letter.

Select the Node Tool.  When you select a letter, because you turned them into paths at the end of the last step, every corner and every important point of curvature will get a hollow diamond drag-handle that you can use to deform the object however you please, including double-clicking an edge to create a new handle.

Next, under the *Path* menu, select *Path Effects*.  It'll open a dialog, where you can select *Corners* from the drop-down menu.  If you change the radius from zero, it'll curve *every* corner, which we don't want.  Instead, each diamond handle will get a tiny hollow *circle* handle that you can drag along the path.

![The handles in Inkscape described in the previous paragraph, the curvature handle beneath the corner's handle](/blog/assets/inkscape-curvature-handle.png "I mean the little circle")

Click the circle and drag it down to the horizontal guide that I mentioned your wanting to add, and it'll curve that corner with a consistent radius.  You can actually drag it anywhere along the edge, but the guide makes sure that it all looks consistent and deliberate.

![The same logo, but the upper-left corner of every blocky letter now has a rounded corner](/blog/assets/future-logo-entropy-arbitrage-1.svg "Step one")

I feel like *something* should happen to the round letters (the *O* and *G*, here), maybe in the lower-left---conservation of pointiness, if you will---but I haven't found anything that doesn't look horribly out of place, so we'll leave them for now.  Also, don't look too close at how the *A* works, since it doesn't give us a right angle to work with...

## Stretched Arms

Next, undoing some of that previous step, we'll take the upper arm of anything that stretches right, and extend it further right into the next letter.  The *Typeset in the Future* article calls this kerning, and we could certainly mess with that, but I see it more as connecting some letters.

With the Node Tool still set, select the relevant two nodes in the upper-right of the letter, then drag them as a pair straight right.  If you hold the {% key CTRL %} key, it'll help keep you moving in the same direction without deviating from the horizontal line.

![The same logo, but now most versions of the E and T have their upper-right arms extended further right](/blog/assets/future-logo-entropy-arbitrage-2.svg "Step two")

In the original example, I did some extra work to create the "hollows" in the next letter to fit the extended arm into:  Duplicate the extended letter, scale it up a bit, and take the other letter's Path difference with it.  But this feels better served by having the letters flow into each other.

At this point, the overlaps tipped me off that I had the opacity set to 64% for some reason, so I fixed that here instead of going back and redoing the first two images.

You can definitely make the argument for some manual kerning, scrunching the EN-block or *I* so that they brush up against their TR-block, for example.  But this should do.

## The Slice

Now we need the "bullet line" that takes a chunk out of the vertical lines, but only somehow *certain* verticals, so that it doesn't split the letter in two.

For that, we need a rectangle.  No, really, nothing more exciting than that.  Actually, we need one rectangle for each letter, identical and with its top flush against the guide(s).  Actually, before doing this, it occurs to me that the partly curved letters (*B*, *P*, and *R*) should probably have their upper bars forced to the same width as before.  I mentioned ignoring it before, but now I see the reason for it.

Do it the same way as extending the arms, but perpendicularly.  Select the top nodes of the upper hole and drag them down to the guide, again holding down {% key CTRL %} to make sure that you don't drag off to the side.  No, it won't look too different, unless you compare the two versions of the *B*.

![The same logo, but now subtly different in the B, P, and R has a thicker upper bar on its curve to match the E and T](/blog/assets/future-logo-entropy-arbitrage-3.svg "Step three")

Now we can create that rectangle and copy-and-paste it everywhere.  Don't worry about the color, because we'll use some Path gimmicks that remove it entirely.  I find positioning them easier with the keyboard after the first one.  Hit {% key CTRL %}+{% key D %} to duplicate (and focus) the rectangle, then arrow right to move the copy to the next letter, eventually going back to fix the box width on anything that needs some help.  I'll leave those in place so that you can see...

![The same logo, but now with the leftmost vertical bar cut overlapped right underneath the common horizontal bar with a black bar](/blog/assets/future-logo-entropy-arbitrage-4.svg "Step four")

Now, with the Selector Tool, select---I know, big surprise, there---each letter with its horizontal bar.  Then, under the *Path* menu, click *Difference*.  Repeat that for every letter and its box.

![The same logo, but now with the leftmost vertical bar cut right underneath the common horizontal bar](/blog/assets/future-logo-entropy-arbitrage-5.svg "Step five")

If I had a certain aesthetic, I could certainly see it starting to come together, at this point.

## Texture

I lack patience for the assorted approaches to trying to create a legitimate-looking metallic texture, but you can find a few tutorials claiming it---or you could cheat, exporting the logo as a raster image, and painting it with whatever colors and textures read as metallic---so I applied a quick gradient to look vaguely gold-like, using the darkest color as an outline to make it feel more solid.

To get the gradient to work, select a row of letters, choose the Gradient tool, and drag from top to bottom of the row.  Assuming that Inkscape doesn't glitch---it did a few times as I worked, losing the user interface that I needed---then you can click the bar to add colors and fill them in.

![The same logo, but now with the metallic gold gradient](/blog/assets/future-logo-entropy-arbitrage-6.svg "Step six")

To avoid the outline between the *E*-*N* pair and the *T*-*R* pairs, I selected them and applied *Path*/*Union* to turn them into one piece, then *Path*/*Break Apart*, in case we need the pieces separate later.

If you don't like the gold, then [Scheme Color {% cc %}](https://www.schemecolor.com/search-palettes/metallic) has a couple-dozen options for you that you might prefer.  And no, they don't have a license on the site, but you really can't copyright a short list of numbers, even if people happen to interpret them as a color scheme.

## Stretch Again

We can now go for (what I associate with) the *Star Trek* movie thing, extending the upper-left and lower-right arms.  You've seen that trick before, using the Node Tool to select the relevant nodes and pull them to the side.

That requires changing the document size, so that nothing gets cut off.  And I also rebalanced the lettering horizontally to suit it.

![The same logo, but now with the upper-left of the first E stretched to the left and the lower-right of the final E stretched to the right](/blog/assets/future-logo-entropy-arbitrage-7.svg "Step seven")

We almost have it, I think.  Oh, we almost forgot the excessive points on the blunt ends.  You know the drill, more work with the Node Tool, selecting (in this case) the upper-right corner of every remaining arm and moving it a fixed amount to the left.  For this sort of work, if you click on the node in question, you can hold down {% key ALT %} and arrow around (left, in this case), which will cleanly jump a significant amount in that direction.

![The same logo, but now with the really pointy bits on the right-hand side of every E](/blog/assets/future-logo-entropy-arbitrage-8.svg "Step eight")

There we go.  And yeah, I changed my mind on the upper-right of the last *E*, to balance it out.

## Finally (Fake) Italicize

If we had italicized the right way, at the beginning, the curves and angles would've taken extra care to get the angles right, when Inkscape doesn't have angled guides.  Therefore, we need to take care of that now.  We no longer have letters, here, so we can't go back to the Text Tool and ask it to italicize, either.

If you select everything (with the Selector Tool), then left-click one of the selected items, then you'll notice that the resizing handles (up, down, left, right, and the diagonals) turn into rotation and skew handles.  In this case, I dragged the upper-middle handle a little way to the right.  You definitely don't want to go too far on this.  And again, this requires changing the document size.

![The same logo, but now skewed to imply that it stretches into the future](/blog/assets/future-logo-entropy-arbitrage-9.svg "Step nine, the probably final step")

Skewing the text doesn't look as polished as using an italicized font, but it still looks fine for casual inspection.  A smarter designer than me would probably compare this result to straight italicized text, and carefully carry over any differences.

And there we have it, a cheap logo ready for a grim but science-y background, maybe with the two lines moved closer together (or further apart, to make room for some prominent object in the background image) and give that extended lower-right arm a more extreme point, but I won't spend time on that.

Still, it almost looks plausible, right?  Here, let's try some atmosphere.

<audio
  controls
  preload="auto"
  style="width: 100%;"
  title="Industrial Cinematic by Kevin MacLeod"
>
  <source
    src="/blog/assets/industrial-cinematic.mp3"
    type="audio/mp3"
  >
  Your browser does not support the HTML audio element.
</audio>

> In a world...  
> ...where decay and collapse have become currency...  
> ...one programmer must turn to blogging to stem the tide...  
> ...moving collapse to where people need it most.  
> And this time, it's personal.  
> In theaters, this Thanksgiving...  
> Look upon his works, Ye Mighty...  
> ...and subscribe to the newsletter...  
> ...in despair:  
> ...Entropy Arbitrage.

Count yourself lucky.  I spent about half an hour trying to figure out what the poster would look like.

Again, I wouldn't call the final result "my thing," as evidenced by my idea of where I would admit to using such a thing, so it definitely won't become the site logo.  And don't have much call to create dystopian science fiction logos.  But the work all happens in Inkscape without too much tedium, so it at least felt fun to play with it.  And I actually almost hate how professional it looks---though I suppose that condemns the genres that rely on the tropes more than it reflects on me---even though I still don't *like* it...

* * *

**Credits**:  The header image adapts [drawing hand](https://www.flickr.com/photos/30485180@N06/3967682030) by [C Dalton Rowe](https://www.flickr.com/photos/30485180@N06/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license.  The music is [Industrial Cinematic](https://incompetech.com/music/royalty-free/index.html?isrc=USUAN1600047&Search=Search) by [Kevin MacLeod](https://incompetech.com/), made available under the terms of the [Creative Commons: By Attribution 4.0](http://creativecommons.org/licenses/by/4.0/) license.
