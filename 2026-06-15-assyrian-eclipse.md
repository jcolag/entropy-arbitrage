---
layout: post
title: Developer Diary, Assyrian Eclipse
date: 2026-06-15 07:29:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog]
summary: Progress on assorted projects
thumbnail: /blog/assets/art002e009573orig.png
offset: -26%
description: This week's projects include all blog modifications, all the time.
spell: Bur-Sagale lang tJ-MUu Didaskalia są skąpe pozostawiają wiele pola osobistej interpretacji czy inwencji Razem trzema piosenkami nam przedstawienie zajęło minut pl Homem-Grilo Dünnes Eis Quand manigancent les Redmine Gedichte Sówka świecie dnia Norte orée ville Carriotepunk Exo
proofed: true
---

* Ignore for ToC
{:toc}

Less a celebration than one of the world's shared historical anchors, today marks the anniversary of the [Bur-Sagale eclipse](https://en.wikipedia.org/wiki/Assyrian_eclipse) in 763 BCE.  Because we can calculate the precise moments of eclipses for thousands of years in any direction, and since Solar eclipses tend to leave such a deep mark on people, the wide notability allows people to connect dates on different calendars.

![A Solar eclipse as seen on the Artemis II Lunar flyby](/blog/assets/art002e009573orig.png "I profusely apologize for not tracking down a twenty-eight-hundred-year-old photograph for this...")

And with that, on to the week's projects.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

As suspected, I have continued to clean up the structure of the blog, maybe improving the readability a bit along the way.

I started with updating the "menu" of links up in the blog headings.  Instead of a couple of titles that ran together, and then icons in pretty much the order that I created the pages, the pages now all have icons, and a (somewhat) more sensible order:  About, the Code of Conduct, Tags, the Tag Search, text Search, the Calendar, the Codeberg repository, the RSS feed, and the home-page.  I also extracted that HTML into a smaller module, *in case* (small hint) I want to present it in a different format at some point.

More importantly, the links that only use icons now have ARIA labels for accessibility.  I gather that you can't rely on screen-readers reading the title text, so absent a name for the link, this indicates to use (what to most people presents as) the magnifying glass link to search.  After messing around with [Orca](https://gnome.pages.gitlab.gnome.org/orca/help/)---already installed on my desktop, probably by default or nearly so---for a while, it looks like at least some screen-readers will read *both* the title text and the ARIA label if they differ, so I set them both to the clearest version of how I would've labeled that.  Oh, the chain emoji to help people to share direct-to-section links also have the ARIA label.

Similarly, while the menu doesn't have *so* much packed into it, most normal pages and posts should start with a "skip to main content" link to the page title.

At the bottom of the page, less about accessibility, you'll see that the tags have a bit more breathing room.

The math on the first-day-of-week work should also now work right.

If you scrutinize the page code---hey, I don't want to judge people's hobbies...---you might also notice some vestigial empty/useless elements gone, and some filled in to serve more of a use, such as the Indie Web `p-category` elements that identify the tags to anybody whose browser follows those tags.

## Entropy Arbitrage, the Posts

{% codeberg jcolag/entropy-arbitrage-posts %}

Most likely, few if any readers will notice this except in extremely narrow circumstances, but it has mildly bothered me since almost the start of the blog that, on the rare occasions when a post includes non-English passages, it structurally looks like the English text surrounding it.  Over the years, HTML has added a language (`lang`) property, originally only for the whole page---Firefox now relies on that to offer to translate a page from its language to yours[^tJ-MUu], when they differ---but more recently meaningful on all elements.

[^tJ-MUu]:  The only part of Mozilla's AI push that provides any utility...

Writing in Markdown, though, it doesn't really leave convenient places to add such a property.  However, the converter that Jekyll uses *does* allow following any paragraph-level element with an awkward-looking tag specifically to add properties to the previous item.  For example, in a [Free Culture Book Club](/blog/tag/book-club) post from last year, I use the creators' description to give a broad sense of the project.

```Markdown
> ...
>
> Didaskalia są skąpe i pozostawiają wiele pola do osobistej interpretacji czy inwencji. Razem z trzema piosenkami nam przedstawienie zajęło 20 minut.
{: lang="pl" }
```

That last line tells a screen reader to read those quoted paragraphs in Polish rather than English.  I might imagine that, now that Firefox's page-translation feature has settled in, they could enhance it to translate those smaller passages, too.  I suppose that anybody could probably also write a browser add-on to add a button that translates segments, too, using the same infrastructure.

For those who might want to see if they have any passages that you might care about, you can run down the list of posts.  In some cases, you'll also now see the original non-English text, where I originally only provided my translation.

- [*Fiction — Grandfathers, Butterflies, and Patient Minus-One*]({% post_url 2020-08-16-butterfly %})
- [*Free Culture Book Club — Homem-Grilo*]({% post_url 2022-02-05-grilo %})
- [*Free Culture Book Club — Dünnes Eis, part 1*]({% post_url 2022-03-12-dunneseis %})
- [*Free Culture Book Club — Dünnes Eis, part 2*]({% post_url 2022-03-19-dunneseis2 %})
- [*Free Culture Book Club — Quand manigancent les haricots*]({% post_url 2022-09-03-haricots %})
- [*Free Culture Book Club — Quand manigancent les haricots pt 2*]({% post_url 2022-09-10-haricots-2 %})
- [*Free Culture Book Club — Quand manigancent les haricots pt 3*]({% post_url 2022-09-17-haricots-3 %})
- [*Free Culture Book Club — Redmine, part 1*]({% post_url 2022-11-19-redmine-1 %})
- [*Free Culture Book Club — Redmine, part 2*]({% post_url 2022-11-26-redmine-2 %})
- [*Free Culture Book Club — Gedichte*]({% post_url 2024-01-27-gedichte %})
- [*Slipped a Mickey*]({% post_url 2024-01-28-mouse %})
- [*Free Culture Book Club — Route 66, An American (bad) Dream*]({% post_url 2024-11-09-route-66 %})
- [*Free Culture Book Club — Sówka w świecie dnia*]({% post_url 2025-05-24-owl-world %})
- [*Free Culture Book Club —  Norte, part 1*]({% post_url 2025-12-27-norte-1 %})
- [*Free Culture Book Club —  Norte, part 2*]({% post_url 2026-01-03-norte-2 %})
- [*Free Culture Book Club — Memory Heap, part 1*]({% post_url 2026-03-07-memory-heap-1 %})
- [*Free Culture Book Club — Memory Heap, part 2*]({% post_url 2026-03-14-memory-heap-2 %})
- [*Free Culture Book Club — À l’orée de la ville, pt 1*]({% post_url 2026-03-28-oree-ville-1 %})
- [*Free Culture Book Club — À l’orée de la ville, pt 2*]({% post_url 2026-04-04-oree-ville-2 %})
- [*Free Culture Book Club — À l’orée de la ville, pt 3*]({% post_url 2026-04-11-oree-ville-3 %})
- [*Free Culture Book Club — Carriotepunk, part 1*]({% post_url 2026-05-16-carriotepunk-1 %})
- [*Free Culture Book Club — Carriotepunk, part 2*]({% post_url 2026-05-23-carriotepunk-2 %})

These only account for longer stretches of non-English text, such as a paragraph.  Individual words or phrases within a paragraph will take more thinking.  It wouldn't take much to surround a phrase with `<span lang="ldn">...</span>` or create a plugin to reduce the syntax or whatever, but *finding* the occasions where I might have used a non-English phrase...I have no idea how to approach that, so far, nor can I see a way of marking it that doesn't clutter the Markdown.

## Next

Expect more of the same, this week.  I know that the non-post pages need some work to get the "skip to content" link working, for example.  Some pieces need more clarity.  I could probably stand to update fonts[^jYn3hy] to current versions.  You get the idea.  On top of that, work has progressed on [Scrawls](https://codeberg.org/jcolag/scrawls).

[^jYn3hy]:  For example, [Exo 2](https://ndiscover.com/family/exo-2/) now comes packaged as a variable font, meaning that posts could use different weights than "maybe too light to read for some people" and "the browser made it bold instead of using a bold font."  Likewise, I believe that I last upgraded the emoji font shortly before the version 17 standard got approved, whereas The People™ demand liberal use of the orca emoji.

* * *

**Credits**:  The header image is [Solar Eclipse of the Heart](https://www.nasa.gov/image-detail/amf-art002e009573/) by NASA, released into the public domain under their policy.
