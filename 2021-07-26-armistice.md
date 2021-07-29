---
layout: post
title: Developer Journal, Korean Armistice Anniversary Eve
date: 2021-07-26 06:32:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Korean-War-armistice-agreement-1953.png
---

Tomorrow will be the sixty-eighth anniversary of the [Korean Armistice Agreement](https://en.wikipedia.org/wiki/Korean_Armistice_Agreement), a cease-fire that has been so successful that...the war has technically never ended, still governed by the armistice.  It wasn't until 2018 that the [Panmunjom Declaration](https://en.wikipedia.org/wiki/Panmunjom_Declaration) brought a commitment to find common ground, actually end the war, reconcile, and consider reunification.

![Signing the Armistice](/blog/assets/Korean-War-armistice-agreement-1953.png "Signing the Armistice")

Anyway, we have code to talk about.

## Fýlakas Onomáton

I updated the last of the easy libraries on [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton).

The server also now allows [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) requests.  I may end up undoing this once I deploy the server, but it looks like Flutter can't retrieve data from servers running on local machines without this change, so it's there for the duration, in case anybody else is using the code to test something like Flutter.

Speaking of which...

## Doritís Onomáton

The [**Doritís Onomáton**](https://github.com/jcolag/doritis-onomaton) app can now retrieve and display the authentication code, instructing the user to visit the server's activation page.

There seems to be something off with the handling (or my understanding of the handling) of `Future`s in Dart.  As far as I can tell, `future.then((value) => ...` won't parse a block of statements in that unnamed ("lambda") function, expecting extra right-braces.  Calling a (named) function does work, and has the virtue of forcing the developer to refactor that sort of mess, but it's still a nuisance to watch out for.

## Picture-to-Nonogram

I wasn't expecting to return to [**Picture to Nonogram**](https://github.com/jcolag/picture-nonogram) for a while, but I woke up one morning to an e-mail notifying me that there was no [daily puzzle](/nono/).  Investigating, the issue is that my easy source for CC0-licensed images [PxHere](https://pxhere.com/) is now "protected" by Cloudflare, meaning that a simple web request isn't going to be able to get at the pages.

I spent some time looking for an alternative---you'll probably see some new public domain stock photo sites listed in the next issue of the [**Entropy Arbitrage** Newsletter](https://entropy-arbitrage.mailchimpsites.com/), if you subscribe before Saturday morning---but none of them had a "random" page.  Ultimately, I decided that, with a direct link to the original page, I *should* be able to get away with using Wikimedia Commons, which has a [Random File](https://commons.wikimedia.org/wiki/Special:Random/File) link.

This introduces its own set of potential problems, but I'm going to ignore them for now.  While (as I said) I can probably get away with linking to the original page to provide licensing information, I'm going to eventually want to extract the authorship and licensing information from the page.  Similarly, there are plenty of files on Wikimedia Commons that are *not* images, so it's almost certainly just a matter of time until the script panics over trying to shrink and desaturate a song.

I also fixed a small bug in the nightly script, which was causing the archived puzzles to not have proper CSS files attached.

## Entropy Arbitrage

This week has seen the debut of a new layout for quotes, which I happen to like.  However, that "small change" to the CSS triggered a series of problems that led me to learning how to [write Jekyll plugins]({% post_url 2021-07-21-jekyll %}), the topic of my Wednesday [tech tip](/blog/tag/techtips) post, if you'd like to learn how to do that.

In short, [the blog's code](https://github.com/jcolag/entropy-arbitrage-code) now has a plugin each for pull quotes and reduced-size images pushed to the right-hand side of the page.

At some point, another library also needed bumping to the current version, so you'll find that in the commit history, too.

### Style Clashes

Oh, and this should be invisible to everybody---it'll actually just get wrapped into the next auto-commit of [the blog's assets](https://gitlab.com/jcolag/entropy-arbitrage-assets)---but in case it's useful information to anybody, here's another detail in the plugin saga.  Around two out of three times when I would deploy the updated blog (local or remote), there was a chance that my new styles would vanish.  I could fix this manually, by changing my CSS---actually [SASS](https://en.wikipedia.org/wiki/Sass_%28stylesheet_language%29)---where it was correct, and letting Jekyll rebuild.

The problem was an oddity that (apparently) sometimes happens in Jekyll, the compiled version of my CSS file---that is, the SASS code converted to a normal stylesheet---was sitting in my `assets` folder.  Since the styles had been fairly consistent, I may never have noticed the problem.  However, the new styles having significant effects, it was now a "race condition" to find out whether the copy or the compilation would happen last.

Nobody seems to know where this precompiled CSS comes from---it's possible that it showed up when I had my [minor crash]({% post_url 2021-03-15-police %}#entropy-arbitrage) and copied the assets from the deployment---but the file isn't needed for anything, so I deleted it and haven't had the problem, since.

## Next

If you (for whatever reason) follow the [**Entropy Arbitrage**](https://github.com/jcolag/entropy-arbitrage) *post* repository, you know that I have written a third plugin for the blog, `cite` for quote citations (to get rid of the bogus headings), and I'll need to check that and the added styles in.  That also requires a change in the script that generates my [Twitter roundup posts](/blog/tag/linkdump).  Unlike the pull quotes and small images, I won't bother to revise old posts to use the new plugin, unless I can convince something like [`sed`](https://en.wikipedia.org/wiki/Sed) to do it for me.

Otherwise, I feel like I've been saying this for months, but this week, I should be able to figure out how to complete the activation process on **Doritís Onomáton**.  Once that's done, I can deploy **Fýlakas Onomáton** to `onamaton.club`, run some final tests with the API key, and start the ordeal of putting the app into the Android and iOS stores.

* * *

**Credits**:  The header image is [Korean War armistice agreement 1953](https://commons.wikimedia.org/wiki/File:Korean_War_armistice_agreement_1953.jpg) by F. Kazukaitis, U.S. Navy, in the public domain as a work of the United States government.
