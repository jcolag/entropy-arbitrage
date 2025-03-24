---
layout: post
title: Developer Diary, World Tuberculosis Day
date: 2025-03-24 08:43:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/TB-poster.png
offset: -30%
description: This week's projects include the blog's code.
spell: sed RCTA
proofed: true
---

* Ignore for ToC
{:toc}

Today, we recognize [World Tuberculosis Day](https://en.wikipedia.org/wiki/World_Tuberculosis_Day), raising awareness of the global epidemic and the efforts to end it.  Despite it sounding like a problem out of **La Bohème** and the associated bizarre attempts to characterize it as some sort of Victorian-era superpower, about a quarter of the population probably has a latent infection and kills over a million people per year, bumped down to the second-most deadly disease only with COVID-19 tearing through the population.

![A poster asking to prevent disease, warning that careless spitting, coughing, and sneezing spread influenza and tuberculosis, showing a person covering their mouth with a handkerchief](/blog/assets/TB-poster.png "Disappointingly still relevant...")

With that, on to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

The script to use icon fonts for annotation icons should now do everything that it'll likely do for the duration, though I see some likely bugs.  Provided that the specified stylesheet has the right format---more on that later---the mapping file has what it needs, and you specify the right class-name prefix, it'll output the CSS that covers the links and languages.  Oh, and even if the stylesheet doesn't support colors, this will still pick up the icons, rather than earlier versions of the code insisting on having both icon and code before proceeding.

```console
ruby link_annotation_update.rb \
   --mapping _plugins/simpleicons.yml \
   --prefix si \
   --stylesheet assets/simpleicons/simple-icons.css
```

The above command takes care of my current example of working with the [Simple Icons](https://simpleicons.org/) font.

Earlier, I mentioned that I had something to say about formatting.  To keep this short, Simple Icons formats its styles like so.

```CSS
.si-creativecommons::before { content: "\ec94"; }
.si-creativecommons.si--color::before { color: #ED592F; }
```

The code assumes a format like this, where it searches for the prefix---`.si-`, in this case---and picks out the `content` and `color` styles when the remainder of the name matches an icon that the mapping file wants.  Keeping the classes on one line helps enormously with that.  However, the next likely target for the script, [Font Awesome](https://fontawesome.com/), has class-based styles that have a slightly different format.

```CSS
.fa-creative-commons {
  --fa: "\f25e"; }
```

You will, I imagine, see the big difference(s), beyond the lack of colors.  First, and of most relevance, the Font Awesome people inexplicably split their classes over two lines.  Second, it sets a variable for use in another style, rather than setting the `content` directly.  Oh, finally, and maybe most important, because of the variable shenanigans, the styles no longer use the `::before` pseudo-element.

We can resolve these irritations with something like this, at least on Linux.

```console
sed -Ez \
  's/\{[[:space:]]+/{ /g;s/ \{ --fa:/::before { content:/g' \
  path/to/fa/css/all.css > temporary.css
```

The first half of the replacement (`s/\{[[:space:]]+/{ /g`) joins the two lines above to one.  GNU `sed`'s `E` parameter says to use extended syntax, allowing us to mess around with character classes like `[:space:]`, and `z` tells it to use a null-character as the ending, instead of a new line, so that we can replace across lines.  The second half (`s/ \{ --fa:/::before { content:/g`) inserts the `::before` pseudo-element and changes the variable to the attribute that we want.

While messing around with icons anyway, the blog now shows an appropriate icon for [Bandcamp](https://bandcamp.com) links, and the blog now has a mapping file for the remaining icons only found in Font Awesome, for when I start overhauling that.

In addition, it looks like I *finally* resolved the issues with the author-annotation thing on Mastodon toot, so [an example](https://mastodon.social/@jcolag/114206097879441237) now looks like this.

![A screenshot of Saturday's blog announcement toot, showing the More from John Colagioia banner underneath the link](/blog/assets/mastodon-2025-03-22-author.png "With a clear issue to resolve later")

The automated toots no longer include the image, since that (among other things) blocks the link previews.  The image displayed in the preview still needs work.  I updated the Open Graph image link to include the full domain rather than a relative path, but I suppose that Mastodon doesn't yet support AVIF files, there.

Finally, the script that I use to put together the text for non-automated social media announcements no longer copies out the image for upload on Fridays.  Since I always use the same image for the [social media roundup](/blog/tag/link-dump) posts, and it more identifies the broad concept of a "week" than anything else, it feels like a waste to attach it to the announcements.

## Next

I need to clean up the final issues with the annotation-icon script, and then (I hope) finally get back to the Open Badges work.

* * *

**Credits**:  The header image is [TB Poster](https://commons.wikimedia.org/wiki/File:TB_poster.jpg) by the  Rensselaer County Tuberculosis Association, in the public domain due to an expired copyright.  The page noted a possible copyright entanglement in 2008, but seventeen years later, the public domain has expanded to include the range when RCTA might have published it.
