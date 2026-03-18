---
layout: post
title: Colors Revisited
date: 2026-03-18 07:27:05-0400
categories:
tags: [tech-tips, programming, design, color]
labels: [css, format, math]
summary: Digging back into (CSS) colors
thumbnail: /blog/assets/3624468931_872fccafc3_o.png
description: Looking back at an early post with an eye on modern web technologies.
spell: oklch ncnExi nm UgrQlR bI hsl okLCH calc rgb Palsson
proofed: true
---

* Ignore for ToC
{:toc}

Early on writing for the blog, I put together a post on [what I knew about color]({% post_url 2020-03-11-colors %}) from a programming standpoint.

To summarize that post, if you use the HSL color-space, then you can pick almost any color, the same colors with thirty degrees higher and lower hue, plus the color one hundred eighty degrees from the original---or in other words, a hue, hue+30, hue-30, and hue+180[^ncnExi]---use a range of saturations and lightnesses, and almost always have a workable color scheme.  And if you know to find red at 0°, green at 120°, and blue at 240°, then you can mostly feel your way through most designs *almost* automatically with a handful of rules.

[^ncnExi]:  Well, the remainder after dividing by 360, but most implementations do that silently for you.

![Colorful houses in a Lisbon neighborhood](/blog/assets/3624468931_872fccafc3_o.png "Sorry, I can't think of anything clever to say about literal houses...")

In the six years since that post, though, we have gotten some improved web technology that lets us play around with colors in even more interesting ways, and so it seemed like a good time to revisit the idea, and maybe hope that desktop will catch up.

## Agenda

Regular readers here probably already have this impression, but for clarity, I do believe that you should generally have professionals do work that you care about.  I'd call design something important, and having somebody who actually knows their stuff will almost always give you better results than waltzing in with educated guesses.  That way lies the [Dracula theme](https://draculatheme.com/spec)...

That said, we (in developing software) don't always have access to a professional beyond our own expertise.  I've had more than one occasion when I asked management when we'd send our ugly system off to the graphic design people, getting "oh, we don't have the budget for that sort of thing" in response.  And in those cases, you need to make do, and you want as good a result as you can get[^3R3s1G].

[^3R3s1G]:  You want good results *except* for the times when you want deliberately bad results.  When I hack together a prototype to demonstrate an idea, I learned quickly to make it as ugly as possible, with scribbled lines, clashing colors that violate the brand guidelines, and barely readable fonts.  When I haven't done that, people tried to put it into production...

Having some background in the space also helps you communicate with the sorts of designers that you'll want to work with.  You'll need to deal with people who work entirely on vibes and have no firm concept of how colors go together, too, but you'll also get plenty who can have a real conversation about how to add a new color or whatever.

## Color Spaces

To explain the broader background, as many of you (probably) already know to some extent, color results from the wavelength(s) of light that either reflect off or pass through an object for our eyes to detect.  Photons with a wavelength of around 380--450 nanometers look violet, lengthening to 625--750 for red.

Your brain doesn't want to deal with the existential angst of the much larger parts of the spectrum that you *can't* see, though, so it interprets 750 nm as similar to 380 nm, creating a tidy continuum of colors.  Your brain also wants to prioritize certain colors, at least partly because sunlight has a dominant color, and so do the internals of the human body, and so the appearance of those colors don't necessarily have the same urgency.  This probably doesn't matter in most cases, but it means that color has a representational problem *immediately*.  We ignore most of a half-infinite[^UgrQlR] spectrum, and pack the rest into a tiny circle, some of which we notice more than the rest, not really resembling the objective physical world.

[^UgrQlR]:  I realize that physicists probably won't appreciate my use of the term "half-infinite," which I borrowed from computer science.  In short, though, photons have energy proportional to their frequency, and you find the frequency as the speed of light divided by the wavelength.  Because you can't have a photon with negative energy, that provides the electromagnetic spectrum with a boundary on weak "long-wave" radio.  In the other direction, though, as far as we know, gamma ray photons can carry as much energy as a system can add.  Or we could flip the model around and say that an infinitely powerful gamma ray photon has a zero wavelength, and long-wave radio can (mathematically) have an infinite wavelength.  Either direction, we get an infinite range with a bounded origin point.

We get another model of color with the rise of computers, where it once cost a ton of money to emit any old frequency, so we fake most colors by combining red, green, and blue[^8PA_bI].  And most of us know the RGB color space, literally describing the intensity of the red, green, and blue for each pixel.  It works reasonably well technically, because your eyes have red, green, and blue receptors, but as mentioned, our brains don't treat those as equally intense, about two-thirds of cones responding to green and thirty percent red (plus the highly sensitive remainder responding to blue), meaning that we can't consistently intuit what a random RGB triplet will look like, or how to convey a specific color.  Like any description based more on how the machine works than how people generally think, it only works for *us* in practice.

[^8PA_bI]:  Unless you work in printing, in which case you make colors out of cyan, yellow, magenta, and black.

The big advancement over the decades, which I focused on in my original post on color, involved creating *cylindrical* color spaces, mapping colors' hues to angles between 0° and 360°.  If we combine them with a saturation (how vivid the color looks) and a luminescence (the lightness of the color), we get the HSL color space.  That feels more intuitive than RGB, because we can reason about those three values better than we can when combining color intensities.  As I mentioned before, you need to remember to find red at 0°, green at 120°, and blue at 240°, but once you have that down, you guess that `hsl 27°, 61%, 20%` (to generate some random numbers) gives you an orange-tinted red---assume that orange and yellow space out equally between red and green---somewhat faded, and dark, probably a red-brown.

However, HSL has its flaws, too, most notably that people still see different hues as more and less vivid or bright, meaning that two "identical" colors except for the hue look significantly different.  In particular, yellow, cyan, violet, and magenta appear discontinuous, with a narrow band of hues standing out dramatically.  Likewise, as I have noted before, the colors that you probably have the least need for in normal work---cyan and magenta---take up enormous slices of the color wheel's pie.  It makes more sense than trying to visualize blends of red, green, and blue light, but it still requires a lot of visual inspection at every step to get colors that match each other.

We can skip a bunch of other color spaces, defined both before and after HSL, and get to the point.

## OK I Guess

Over the last few years, we have introduced the [okLCH](https://en.wikipedia.org/wiki/Oklab_color_space) color space, which has a similar cylindrical shape to HSL, but aims for perceptual uniformity, so that every hue should "feel" the same for the same lightness and chroma (boldness, analogous to saturation).  It has its own flaws, such as "gaps" in the cylinder where it can't guarantee that perceptual uniformity, but it now works widely in CSS with that caveat.

The hues lay out differently, for whatever reason.  Here, red lands at slightly less than 30°, green a bit over 142°, and blue at 264°, probably to reclaim some space from cyan and magenta.  Again, though, once you have those numbers in mind, you get a similar intuition for what color an arbitrary set of three values mean.  If you see `oklch 0.47 0.71 332°`[^bv-8pm], you can probably already guess that you have a purple (near the point between red and blue), bold but dark enough to match a medium gray.

[^bv-8pm]:  If you need transparency, append a slash and decimal value, for example `oklch(0.47 0.71 332 / 0.25)`, to expand the example above.

However, this random example brings us to those aforementioned gaps.  This hue can't manage a chroma value higher than 0.27 on any real hardware.  You generally can't get a chroma value higher than 0.2, so you probably want to consider that the "real" maximum value, decreasing that some for the orange-to-green range.  Likewise, light (l > 0.9) or dark (l < 0.3) colors support significantly less chroma.

The model includes these gaps to preserve that perceptual uniformity on the hardware and your eyes:  You can't have that bold a medium purple, because no hue "works" at those levels.  At other levels, you'll get patchy coverage of hue.  You can play with this on an [okLCH explorer](https://oklch.com/) tool.  Remember that I "wasted time" talking about how different colors have different levels of relevance to us, hence seeing them as more or less bold?  This also affects those choices, with a light yellow-green---like sunlight, but you'll recognize the highlighter marker color---taking higher chroma values than the rest of the spectrum.

If a color doesn't make sense for the monitor (or at all), the implementation (browser) picks the closest legitimate match.  On my monitor, that generally seems to mean starting with another hue, then stepping down the other values if necessary.

What do we mean by colors that "make sense for the monitor"?  Some of you might have some familiarity with [DCI-P3](https://en.wikipedia.org/wiki/DCI-P3) displays, which allow for a wider range of colors.  Somebody with a fancy Apple monitor, then, can see a wider range of colors on their screen than I can on my refurbished, discount laptop screen manufactured a few years ago.  On such more-modern screens, you can generally bump the chroma to 0.25.  You'll probably want to wrap those colors in a media query for `color-gamut: p3`, with duller colors that work everywhere as the default.

Because the implementation will try to find the closest match for "missing" colors, it still needs visual inspection to make sure that the colors show up as intended and working out combinations that do fit.  However, it takes significantly less inspection than HSL and RGB, because *if* you have real colors---which you could calculate, maybe pulling the code right out of the tool linked a couple of paragraphs back---then you have a good sense of aspects such as the contrast between two colors and whether they feel equally vibrant and/or light.

## Relative Colors

Now, though, we can do even better than all this, beyond only picking the better color space.  CSS now has *relative* colors.

When I started putting the blog together, I noticed that Jekyll uses [SASS](https://sass-lang.com/), which extended CSS with various utility features.  Two features struck me as invaluable, the `lighten()` and `darken()` functions, which returned a color modifying the input.  You can set something to display as "the background color, but twenty percent darker," for example.  I didn't find much else to care about in SASS, but early versions of the blog used those functions everywhere.

Well, CSS has caught up to that and arguably surpassed it.  [Relative color syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Colors/Using_relative_colors) allows you to alter a color by any channel in any color space.  As such, you can do something like this.

```CSS
color: oklch(from orange calc(l * 0.8) c h);
```

That takes the default HTML orange (`#ffa500`) and makes it twenty percent darker.  You could also replace an HTML name with anything else, most usefully a CSS custom property ("variable"), so replacing `orange` above with something more like `var(--background)` gives us exactly the SASS example of a darker version of the background color, assuming that you created it.

You can see how this might fit well with okLCH colors already.  Because we know that some color relationships work better than others, and because we know that the same lightness/chroma pairs will look similar across all hues if the display can show them at all, then we can start building color schemes through arithmetic.  Consider the following idea.

```CSS
:root {
  --main-hue:  158;
  --primary: oklch(0.7 0.15 var(--main-hue));
  --secondary: oklch(from var(--primary) l c calc(h - 150));
  --tertiary: oklch(from var(--primary) l c calc(h + 150));
  /* And then create darker, lighter, and more faded
   * versions of those three colors using the same process.
   */
}
```

We now have the start of a "split complementary" color harmony, a primary color---a slightly bluish green---and thirty degrees to either side of the complementary color opposite it on the color wheel.  If you'll pardon the intrusion of an HTML blob in the middle of the post, that gives us something like[^pi-SCO] the following boxes.

[^pi-SCO]:  I didn't bother to set up all the CSS.  I only want to illustrate the point, here.

<div style="background-color: oklch(0.7 0.15 158); height: 5em; margin-left: 25%; width: 50%;">
  <div style="background-color: oklch(0.7 0.15 8); display: inline-block; height: 3em; margin: 2.5%; width: 44%;"></div>
  <div style="background-color: oklch(0.7 0.15 308); display: inline-block; height: 3em; margin: 2.5%; width: 44%;"></div>
</div>

See?  Even using them in the worst possible way---on a page or screen, we'd probably use all three colors against a common bland background, not stack them on top of each other---they don't really clash, definitely not bad for a random "root" color.  And if you don't like that harmony, then you can try others.

|Name|Colors|Explanation|
|----|------|-----------|
|Monochrome|1|One main color, only changing lightness and chroma|
|Complementary|2|A main color and the color with a hue 180° away|
|Analogous|3|A main color and colors at +30° and -30° hue|
|Tetradic|4|A main color, one analogous color, and their complements|
|Analogous Complementary|6|The analogous colors and their complements|
|Split Complementary|3|My example, a main color and ±30° hue from the complement|
|Triadic|3|A main color, and the colors at ±120° hue|
|Square|4|A main color, the complement, and the colors at ±90° hue|

You probably have some direct experience with analogous colors, by the way.  Think about how you'd represent a fire.  Chances are, you'd display something as red, orange, and yellow.  And if you zoom in, the hottest part of the color has traces of blue, the complement of orange.  See?  You already know this stuff.  Oh, also, many designers consider analogous harmonies to have an open-ended set of colors, with each pair---±30°, ±60°, ±90°, and so forth---used progressively less frequently.

And while I didn't do it here (it'd take too much work for the sake of an example), if we chose their colors as the previously defined `var(--primary)`, `var(--secondary)`, and `var(--tertiary)`, then you can change `var(--main-hue)` and see that follow down the entire set of colors.

And yes, you can do this with any color space.  If you really want `rgb(from var(--whatever) calc(r + 10) calc(g - 20) calc((b + g) / 2))`, then go for it.  But you can see that it works *better* when you have a more predictable color space, such as okLCH.

## Light and Dark

To wrap this up, don't forget about the `light-dark()` CSS function, which I discussed in a post about [dark mode]({% post_url 2024-08-14-dark-mode-again %}) about a year and a half ago.  This allows you to set different colors based on whether the user's browser expresses a preference for lighter or darker color schemes.

For example, you can show a lighter background by default, but a darker background for browsers requesting it.

```CSS
:root {
  color-scheme: light dark;
  --main-hue:  158;
  --primary: oklch(0.7 0.15 var(--main-hue));
  --bg-light: oklch(from var(--primary) calc(l * 1.2) calc(c / 3) h);
  --bg-dark: oklch(from var(--primary) calc(l * 0.3) calc(c / 3) h);
}
body {
  background-color: light-dark(var(--bg-light), var(--bg-dark));
}
```

And then choose text and other colors in similar ways.

## Putting It Together

Combined, this all now gets us far closer to the ideal, where---in the absence of a branding guide, which should override everything else---we can get a color scheme with a couple of quick choices that *probably* satisfies a handful of conditions.

First, it should look nice, or at least decent.  The color harmonies broadly get us most of the way here.

Second, we should have the capacity to spot when colors, pair-wise, have a high enough contrast that low-vision users don't have a problem.  Because okLCH prioritizes perceptual uniformity, we can actually get an approximation fairly quickly.  A more thorough test requires converting colors to RGB and using the [Web Content Accessibility Guidelines](https://w3c.github.io/wcag/guidelines/22/#dfn-relative-luminance) formulas, but for a quick-and-dirty contrast ratio, take the luminance of each color, cube it, and take the ratios of those numbers.  With some critical exceptions, that should usually come close enough to compare to the [AA and AAA accessibility ratios](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast).

As I said, though, and as you can confirm with some arithmetic, this doesn't quite work for gray and saturated yellows-to-greens.  By this math, grays act darker than expected.  For the green problem, we could *probably* devise some clever adjustment where we take the cosine of the hue-minus-140° or so and the chroma value times some fudge factor---the WCAG formula for RGB values has coefficients for the red, green, and blue channels that hint at a trigonometric relationship, after all---but at that point, you probably won't do the work in your head and might as well convert to RGB to use the aforementioned formulas.  Notice, though, that this connects with the prior comments about that same color range reading as excessively bold because it comes close to matching the dominant hues in sunlight.

Likewise, the `light-dark()` function helps package good contrast in a way that different people might find more palatable.

Finally, the colors should work for color-blind users.  That, other than ensuring that everything has a high contrast, I don't know how to estimate, *other* than converting the colors to RGB, going through the matrix math to simulate different kinds of color-blindness, and re-checking the contrasts.  This, unfortunately, makes sense, because the condition in humans results from failure of a class of cones in the retina, and so knocking out the red, green, or blue channel[^4Qov6i].  And really, that always requires testing by humans who have the various conditions, since the math doesn't provide precise results.

[^4Qov6i]:  For manual checking, the *Accessibility* tab in the browser tools have a drop-down to simulate different low-vision conditions, but don't rely on them completely.

Oh, and speaking of which, you generally want to avoid bolder (high saturation/chroma) reds when you can, because the brain processes that range of hues slightly differently, and so we have a physiological response to it.  That response can lead to epileptic fits in susceptible readers, independent of trauma and culture.

## One More

In reading up to put this post together, making sure that I had details correct, I stumbled across an important newer---not yet available in the Chrome family, as I write this---feature, [`contrast-color()`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/color_value/contrast-color).

Given an input color, `contrast-color()` returns `white` or `black`, depending on which has the higher contrast to the input.  Once this becomes widespread, this should (except for some color ranges where neither really works) permanently solve the choice of colors on controls/widgets such as buttons.  And I have to imagine that, eventually, browsers will expand the return values to whatever color has the greatest contrast ratio against its input.

## The Blog

Full disclosure, I haven't taken advantage of all this, yet, but I'd like to.

A couple of years ago, I converted all the blog's colors to HSL to maintain a better intuition when changing things.  I also added the `light-dark()` nonsense, primarily because I prefer to read dark-mode at night and light-mode during the day.

Then, a couple of weeks ago, I converted the colors to okLCH.  The next steps?

It does make sense to use relative colors to only define a single hue.  Aside from making the color scheme clearer, it would also allow me to occasionally have a blog post that "rotates" the color scheme to a new set of hues.  I wouldn't expect to do that often if at all, but I like the premise.

For example, if the site defines all colors based on the yellow, something like `calc(var(--yellow)+150)`, and if a post includes a `style` element distinct from the main site style which says `--base: 142`, then the light-mode background color becomes a green *equivalent to* the yellow in boldness and lightness, plus an associated purple-red and blue, and the contrasts should mostly hold up.  At least in theory, you could imagine using this sort of thing to "theme" a post for a holiday[^BJCQ7m], or to separate a certain kind of post visually from the rest of the blog.

[^BJCQ7m]:  If you want an even wilder possibility that I would definitely never use on the blog, if you set up all the colors like this, then you could also run JavaScript like `document.documentElement.style.setProperty('--base', '294');`, which changes the *entire* color scheme at once.  For the right project, you could call `setInterval()` and have the color scheme slowly "rotate" through every hue variation.

Then, and probably a higher priority, I do want to double-check the contrast across the blog.  Readers who need higher contrast than I provide do already have a few options, such as turning off the stylesheets, using Firefox's reader mode, or using RSS, *but* if I can make reading a cleaner experience while maintaining the general aesthetic, then I should do that, and I should also check under color-impaired conditions.

* * *

**Credits**:  The header image derives from [Colorful hillside neighborhood in Lisbon, Portugal in the morning sun](https://www.flickr.com/photos/45713725@N00/3624468931) by [O Palsson](https://www.flickr.com/photos/opalsson/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license.
