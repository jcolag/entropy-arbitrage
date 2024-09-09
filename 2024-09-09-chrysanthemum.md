---
layout: post
title: Developer Diary, Chrysanthemum Day
date: 2024-09-09 07:15:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Chrysanthemum.show.png
offset: -8%
teaser: This week's projects include social media updates, clean-up on the blog's code, fixing old blog posts, Notoboto, my Codeberg Pages profile thing, and the long-promised vehicle toy for The Light's Edge.
spell: Notoboto Codeberg LLL Nuno Mums Pinkary socialshowdown Tcl Tk es Jugni Unported
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate---or at least we might in Japan---[Chrysanthemum Day](https://en.wikipedia.org/wiki/Chrysanthemum_Day), one of their oldest festivals, surviving for over a thousand years.

![A display of chrysanthemums in Lahore, Pakistan](/blog/assets/Chrysanthemum.show.png "In the United States, our system of units and measurements would clock this as Way Too Many Mums")

Off we go to the updates without more fanfare than that, I guess.

## Social Media

While I hadn't heard of them before their announcement that they [released their source code](https://github.com/pinkary-project/pinkary.com) under the AGPL, I took that announcement as a good time to sign up to a relatively new social media site.  As a result, you can now [follow me on Pinkary](https://pinkary.com/@jcolag).

![A QR code pointing people to my Pinkary account](/blog/assets/pinkary_jcolag.png "It took me multiple tries to find software that would decode this, even after changing the pink to white and adding different borders, so beware.  It does, at least, only carry the link to my profile, as far as I can tell.")

It seems to want to stand in a niche that combines that [Link Tree](https://linktr.ee/) site that became briefly popular a while back, a question-and-answer format most recently seen at [Cohost](https://cohost.org/jcolag), and the overall microblog aesthetic of {% x %}.  Project leader [Nuno Maduro](https://nunomaduro.com/) also does a lot of work on [Laravel](https://laravel.com/), the PHP web application framework, so this might stick around for a while.

Whether *I* stick around beyond posting blog updates depends on the usual factors, as you can guess.

Oh, and maybe I'll resurrect the [Free Software Social Networking Showdown](/blog/tag/socialshowdown) after more than four years...but probably not.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

This week has continued the cleanup from the overhauls of past weeks.

In the styles, links to tag pages now get a little tag hint, so that you know what'll happen when I point you at [developer diary](/blog/tag/dev-journal) posts, for example.  And I made sure that a lot of the changes made to posts also show up on the [tag list](/blog/tags/), assuming that anybody ever visits there.  And more URLs get the little link-hints.

Speaking of the tag list, it now makes sure to count the tagged pages correctly, regardless of hyphenation.  And since it links to that page, I updated the page-not-found error page.

## Entropy Arbitrage, the Posts Again

{% github jcolag/entropy-arbitrage %}

Since the CSS hints for links will probably stick around, I took a couple of hours to remove the old "Font Awesome character stuffed into the link name" of old posts, other than [Social Media Roundup](/blog/tag/link-dump) posts.

After scanning around, it only came to around a hundred files.  As a result, unless I missed something, you should no longer see the "old crusty link to Amazon with the Amazon logo in the title and then also hovering at the end of the title" and similar problems.  Similarly, I dropped the "hot beverage" {% emoji hot beverage %} emoji from Buy Me a Coffee links.

## Notoboto

{% github jcolag/Notoboto %}

As hinted last week, my lightweight note-editor now complies with [REUSE](https://reuse.software/).  If you wanted to see how it looks, this project should give you some better insight.  First, you have the two licenses in the [`LICENSES`](https://github.com/jcolag/Notoboto/tree/main/LICENSES) folder replacing the single AGPL license.  Then, the main script has the following in its header comments, indicating me as the owner and the license for the file.

```Tcl
# SPDX-FileCopyrightText: 2024 John Colagioia <jcolag@colagioia.net>
#
# SPDX-License-Identifier: AGPL-3.0-or-later
```

Then, in the [`img`](https://github.com/jcolag/Notoboto/tree/main/img) folder, each `whatever-material.png` image file has a companion `whatever-material.png.license` file that looks like this.

```text
© Google LLC

SPDX-License-Identifier: Apache-2.0
```

They both convey the relevant information in the context of the file, and allows more nuance between files.

However, I also did some more immediately productive work, here.  It turns out that embedding images as I did doesn't account for the images that already existed.  As a result, the more that I typed, the more that the application would insert copies of images into the text, which doesn't *hurt* anything, but also doesn't help.  To solve that, I needed to delete the images first, apparently one-by-one, since I can't find a comparable process for the entire set.

```Tcl
set images [$widget image names]
foreach name $images {
  $widget delete $name
}
```

Tk assigns the images boring names like "`image1`," which `delete` can use to make changes.

## Codeberg Pages for Me

{% codeberg jcolag/pages %}

While certainly not the most critical detail, here, my [Codeberg Pages profile](https://jcolag.codeberg.page/) now complies with the aforementioned REUSE standard.

Much like pushing the initiative on the toys for **The Light's Edge**---coming up shortly...---I don't see how this makes a *huge* difference in how people interact with the repository, assuming that anybody ever interacts with it at all.  But for a new, small project, it seemed worth taking the step of making this a normal practice for me.

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

For lack of a better name, I present to you...the *Rail Runner*, the long-promised vehicle that will probably make appearances in **The Light's Edge**.  Pardon the exposure to somebody's brand[^1], but the box sat on top of the pile and had good dimensions for everything.

[^1]:  Also pardon the crass commercialism and digression, but since I do actually like them enough to have those boxes everywhere, and they have an affiliate-like program for all customers, I suppose that I should mention on the chance that you need something like [Thrive Market](http://thrv.me/QT5wJT), the link will give you a forty percent (40%) discount on your first order and I get credit towards my next, if you stick around.  Or ask some other member for their link, if you'd rather help them out with their grocery bills.  When I dropped Amazon Prime, Thrive replaced a lot of the dry goods that I bought there regularly.

![LLL-1 in es Rail Runner prototype](/blog/assets/lights-edge-rail-runner-1.png "I decided not to go for subtlety in taping it, but the toothpick faux-harness, you might not spot.")

I think of it as somewhere between a template (our world) and work-horse (theirs), in that this core design should work in almost any material, and people can quickly adapt it.  Change the lengths of the folded panels to change the shape of the cockpit.  Change the shape of the cut-out to accommodate different passengers or even additional passengers, given the width.  Cut it out of (multiple pieces of) wood, print it in (panels of) plastic, or stamp them out of sheet metal.  Modify the ends of the rails to resemble claws, weapons, or whatever, or cut a triangle out of the rails to help enclose the cockpit.  Even bending the rails down instead of up changes the look.

A canopy would improve the appearance, but it didn't seem worth complicating things at this stage.  Even without it, the design cuts the right outline for something like a one- or two-person shuttle, scout, or fighter craft.

For those of you living in a world of ISO paper sizes, the model has enough flexibility that you can probably get away with scaling the SVG file to A4 dimensions *or* centering the pages on top of each other, accepting narrower rails and extending the vertical lines to the top and bottom edges.

## Next

Now that I've settled the embedded images in **Notoboto**, part of me wants to also embed check-boxes.  In some versions of Markdown, you can create a checklist by creating a bulleted list and starting each entry with empty or filled square-brackets, such as a line like `* [ ]`.  I have a few notes with checklists---I use them to keep track of what we've talked about in the [Free Culture Book Club](/blog/tag/book-club) and what projects I still have available, for example---and would love to click in the note and have it automatically fill the empty check-box (`[ ]`) with a filled box (`[x]`).

Oh, and if you noticed in the [Social Media](#social-media) section, I need to commit my standardized approach to referring to {% x %} as a quick plugin.

Otherwise, I see library updates building up again, so I might also or instead slog through those.

Will anything more happen with **The Light's Edge**?  I actually have no idea...

* * *

**Credits**:  The header image is [Chrysanthemum show](https://commons.wikimedia.org/wiki/File:Chrysanthemum.show.jpg) by [Jugni](https://commons.wikimedia.org/wiki/User:Jugni), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license.
