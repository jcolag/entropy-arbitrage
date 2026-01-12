---
layout: post
title: Developer Diary, Anti-Corruption Day
date: 2024-12-09 07:54:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, html, library-update]
summary: Progress on assorted projects
thumbnail: /blog/assets/student-in-Uvira-spreads-anti-corruption-message.png
offset: -30%
description: This week's projects include the blog's code and a lonely library update.
spell: noscript Fýlakas Onomáton Uvira Bitamala
proofed: true
---

* Ignore for ToC
{:toc}

Today, we observe [International Anti-Corruption Day](https://en.wikipedia.org/wiki/International_Anti-Corruption_Day), intended to raise awareness of corruption and ways to fight it.  It also seeks to draw attention to how corruption undermines the rule of law, human rights, markets, quality of life, and so forth.  I can't imagine why that might all become more relevant as we inch towards 2025...

![A student carrying a protest sign defining corruption as an unworthy practice in democracies](/blog/assets/student-in-Uvira-spreads-anti-corruption-message.png "I can't disagree with the assertion")

On that downer of a note, on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

As far as *visible* changes go, you might notice that the entries on index pages now show the tags.  In an ideal world where I pay more attention to the tags, that should give a better indication of what you'll find inside.

![A screenshot of a recent Social Media Roundup post title on the index page, with tag bubbles centered beneath it](/blog/assets/ea-title-with-tags.png "Not exactly stunning, but functional...")

You won't see it in action for a while, but the blog now also has a style available to hide an element if the browser doesn't support or allow JavaScript.  I have a couple of possible features in mind where, if the user can't or won't use JavaScript, it doesn't make much sense to show the controls.  Apparently for exactly this situation, the HTML specification now allows the `noscript` element to appear inside the `head` element, allowing me to do something like this.

```HTML
<noscript>
  <style>
  .js-required {
    display: none;
  }
  </style>
</noscript>
```

When I have the features ready, that'll let me release it without irritating the non-JavaScript readers, by wrapping the controls in a container with the `js-required` class.  Previously, browsers wouldn't recognize the `noscript` element anywhere but the document body, meaning that you could only solve something like this by setting the wrappers to not display, then use JavaScript if you wanted them to appear, which feels uglier.

More invisibly, though, I've spent most of this week squeezing out now-deprecated SASS code in the stylesheets.  I recently upgraded Jekyll versions, which upgraded the SASS-to-CSS compiler in turn, and that compiler had *opinions* on the code.  I won't get into the details, because I don't think that I wrote any of the original code, only inherited it by building the blog's styles off the version of [Minima](https://github.com/jekyll/minima) available at the time.

Inexplicably, the Minima maintainers know about this problem on the horizon, and [their solution to eventually using obsolete features](https://github.com/jekyll/minima/issues/815) seems to begin and end with refusing to upgrade the SASS compiler, though I also see signs in that thread that they *might* change their minds.

## Library Updates

I needed to bump another library version for [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton).

## Next

I need to continue running down the last issues with the blog's SASS code, which might take a while.  It looks like the migration tool---which seems to only issue similar warnings to what I already get, rather than actually helping with any of the work---exits on the first significant problem, meaning that I don't know how deep the pit goes...

* * *

**Credits**:  The header image is [A student in Uvira spreads anti-corruption message](https://commons.wikimedia.org/wiki/File:A_student_in_Uvira_spreads_anti-corruption_message.jpg) by [Bitamala](https://commons.wikimedia.org/w/index.php?title=User:Bitamala&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
