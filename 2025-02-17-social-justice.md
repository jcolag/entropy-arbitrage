---
layout: post
title: Developer Diary, World Eve of Social Justice
date: 2025-02-17 07:52:05-0500
categories:
tags: [programming, project, dev-journal]
label: [blog, library-update]
summary: Progress on assorted projects
thumbnail: /blog/assets/Eleanor-Roosevelt-UDHR.png
description: This week's projects include the blog's code and a quick library update.
spell: Eggbug
proofed: true
---

* Ignore for ToC
{:toc}

I couldn't find any holidays for today, but *tomorrow* marks the [World Day of Social Justice](https://en.wikipedia.org/wiki/World_Day_of_Social_Justice), also known as Social Justice Equality Day, bringing attention to the need to press and fight for social justice, in a world of poverty, discrimination, and more.  Why would that draw my attention in early 2025?  We'll probably never [figure it out](https://politizoom.com/vances-munich-speech-big-hit-in-moscow-eu-girds-for-global-shift/)...

![Eleanor Roosevelt holding poster of the Universal Declaration of Human Rights](/blog/assets/Eleanor-Roosevelt-UDHR.png "I actually thought that I had used this picture before, but apparently not")

On that brief note, on to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

At this point, the direct fallout from updating the [Simple Icons](https://simpleicons.org/) font *should* have mostly gotten cleared away, with the code-points adjusted to fit the new version, in both the link-annotation icons and the programming language identifiers.  In addition, a few categories of link annotations should now show with the recommended colors.

Speaking of colors, because that raises contrast issues, in dark mode, the link annotations appear with a couple of shadows to outline the icon in white, making dark icons more visible against dark backgrounds.

Along the way, an analysis of off-site links showed that the blog pointed more than a few times to now-defunct-but-still-archived-on-the-Internet [Cohost](https://cohost.org), so those will now show with their proper icon, sadly not [Eggbug](https://web.archive.org/web/20241223053503/https://cohost.org/rc/tagged/eggbug){% emoji trademark %}.

## Library Updates

I needed to bump library versions for the [**Generic Board Game**](https://github.com/jcolag/generic-board-game) repository, not that I ever got around to using it for anything.

## Next

I have more of the Simple Icons overhaul to take care of---and really want to think about ways to auto-generate (at least) the link annotations from the CSS that they supply, so that I won't need to go through this tedious process ever again, and maybe get better coverage of outbound links without needing to manually add them---and when I finish committing all that mess, I'll probably move back to the Open Badges work.

* * *

**Credits**:  The header image is [64-165](https://www.flickr.com/photos/fdrlibrary/27758131387/) by the [FDR Presidential Library & Museum](https://www.flickr.com/photos/fdrlibrary/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
