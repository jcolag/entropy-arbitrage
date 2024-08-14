---
layout: post
title: Yet Another Dark Mode Post
date: 2024-08-14 07:44:05-0400
categories:
tags: [programming, techtips]
summary: Revisiting dark modes again
thumbnail: /blog/assets/6028828966_0046918665_o.png
offset: -38%
update: [
  2021-03-24-darkmode.md,
]
teaser: A discovery that, if you wait long enough, CSS comes to you.
spell: Rubensson
proofed: true
---

* Ignore for ToC
{:toc}

Early in the life of the blog, I wrote about [assembling a dark mode]({% post_url 2021-03-24-darkmode %}) for a web page.  I showed a couple of possibilities, after deciding on the complementary color schemes.  The other day, I discovered that the state of affairs had advanced.

![A tropical green area at night](/blog/assets/6028828966_0046918665_o.png "Admittedly, nicer darkness than I pulled together...")

Honestly, feel free to skip to the bottom of the post, because the actual new development requires little explanation.  For the rest of you, let's take a quick look at the prior possibilities and why my knowledge of them didn't lead to the blog instantly getting its own dark mode, even though it would make my own editing after dark less bothersome.

## Quick CSS History Lesson

At that point, the traditional approach generally involved some sort of button or other triggering mechanism for the user to choose between color schemes.

```JavaScript
document.body.classList.add('dark-mode');
// ...and...
document.body.classList.remove('dark-mode');
```

You'd combine that with something like the following styles to swap the colors around.

```CSS
#dark-mode:checked ~ #main-container {
  background-color: black;
  color: white;
}
```

Around that time---support depending on your browser and update cycle---we also started to see a media query that can clean this problem up by asking the web browser itself which color scheme to choose.

```CSS
@media (prefers-color-scheme: light) {
  body {
    background-color: white;
    text-color: black;
  }
}
@media (prefers-color-scheme: dark) {
  body {
    background-color: black;
    text-color: white;
  }
}
```

Many variations on this exist, from assuming light mode as a default to using CSS variables to select the colors that everything else uses.

## Except...

These schemes have two major problems, I would argue, at least for me.

First, they require a lot of reorganization and what looks like duplication.  Unless you distill your colors to semantically relevant variable names---which I recommend, where possible---you end up replicating large swaths of styles for the different media queries or containers.  For something like this blog, I have something like two thousand lines of CSS (well, see below) that I adapted from the default blog theme, and would need to manually go through and pull out every reference to a color.  And that feels like a complete waste of my time.

Second, I lied about lines of CSS, because Jekyll technically uses [SASS](https://sass-lang.com/), which compiles to CSS.  And I need to point this out, because the compilation step doesn't play well with these dynamic ways of changing colors.  If I did the smart thing and refactored my colors into variables hidden behind media queries, then the SASS compiler would pick a color scheme at compile-time and stick with that.

I *could* refactor the colors entirely into variables, but then I'd need to dig through and change every reference for a color into a variable, and then do something clever in the cases where I modify a color using SASS's `lighten()` and `darken()` functions.

## Enter CSS Color Module Level 5

Floating around for most of this year, the CSS working groups have pushed (among other things) the [Color Level 5] module.

OK, let me take a step back, here.  CSS no longer increases version numbers, and so we expect that people will use CSS 3 for many years to come, even though their CSS 3 will look almost nothing like the CSS 3 release in 1999.  Instead, the "modules" increase their versions.  Presumably, at some point, the committee will realize that almost nobody understands this, and the majority of people who do understand it find it incredibly goofy, and will throw down an official CSS 4 milestone, but until then, we deal with this.

I bring this all up to make the point that CSS always moves forward, even though the version hasn't changed in decades.  And to make the point that, if you procrastinate long enough on restyling something, CSS will probably catch up to your needs and give you a quicker way through your work, a lot like the old science fiction stories about Earth sending colony ships to distant worlds, only for those colonists to find massive human cities at the destination, because we invented faster-than-light travel while they ambled along.

In our case, we want the [`light-dark()` function](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/light-dark)[^1].  This function---used in place of any color---takes two colors as arguments, and uses the first color if the user-preferences say to use light mode, and the other for dark mode.

[^1]:  Ironically, I discovered `light-dark()` accidentally, looking for something *else* in the current/future CSS color module.  I could swear that I saw a reference to functions that pull out the components of colors, at some point, and wanted to use them to eliminate the aforementioned `lighten()`/`darken()` functions, but I found this instead, which proved more productive in the short term...

```CSS
:root {
  color-scheme: light dark;
}
body {
  background-color: light-dark(white, black);
  color: light-dark(black, white);
}
```

Even better, for my case, this propagates along through the SASS compiler, so that I can do things like this.

```SASS
$background-color: light-dark(white, black) !default;
.random-class {
  background-color: $background-color;
}
```

And while the media queries would fail, here, this carries through to the page.  I *do* lose the `lighten()`/`darken()` color modifiers, but that seems reasonable for two reasons.

* The color modifiers should have opposite meanings in dark mode, making them mostly useless.
* I converted all my colors a long time ago to the [HSL color space]({% post_url 2020-03-11-colors %}), meaning that I can apply my percent lighter or darker to the literal luminosity percentage.

On top of that, the [feature has wide availability](https://caniuse.com/mdn-css_types_color_light-dark) already, only leaving out the Samsung and Opera mobile browsers, plus Internet Explorer.  I can only hope that the single person who visits my site using the Samsung thing---no, seriously, the analytics tell me that only one of you does that---won't hate me for whatever the browser will do with this function.  I'll see if I can find a fallback for you, but bear with the less interesting colors.

## The Upshot

The blog now---finally, after years of my claiming that I'd do it soon---has a dark mode.  In my case, I changed the lightness of each color *and* rotated the hues to what I think looks nicer than the initial attempt of light blue text against a muddy brown background.

Also, as mentioned, procrastination works quite well for solving programming problems.  If you don't have a deadline, *eventually* somebody will solve your problem at a lower level...

* * *

**Credits**:  The header image is [night](https://www.flickr.com/photos/36307913@N00/6028828966) by [Fredrik Rubensson](https://www.flickr.com/photos/froderik/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/) license.
