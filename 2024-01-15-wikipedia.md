---
layout: post
title: Developer Diary, Wikipedia
date: 2024-01-15 07:14:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Wikipedia-logo-version-2.png
offset: -15%
teaser: This week's projects include Notoboto, mostly. Yes, again, but this time with a search box.
spell: Lemmy Notoboto Miniboost Nohat Unported
proofed: true
---

I don't suppose that anybody really *celebrates* today, but today marks the twenty-third anniversary of the launch of [Wikipedia](https://en.wikipedia.org/wiki/Wikipedia), which has grown from a project meant to crowdsource writing for the team's "real" encyclopedia, to one of the cornerstones of the Free Culture movement and arguably the Internet as a whole.  Likewise, where we initially all looked at Wikipedia skeptically as a source of information, we have since learned that we need to look at *all* sources of information skeptically.  A quick check tells me that roughly four out of every five posts on this blog contains at least one link to a Wikipedia article, so I suppose that I should celebrate, at least a bit.  {% emoji party popper %}  OK, that feels like enough.

![Wikipedia's logo, an incomplete sphere made of large, white jigsaw puzzle pieces. Each puzzle piece contains one glyph from a different writing system, with each glyph written in black](/blog/assets/Wikipedia-logo-version-2.png "Has the Wikimedia Foundation manufactured and sold stuffed toys of this globe?  I feel like that'd work far better than Jimbo randomly begging for money every so often...")

Well, my projects probably won't ever grow as ambitious as Wikipedia, but let's talk about progress anyway...

## Social Media

I should probably have mentioned earlier that, while I mostly lost track of the issue shortly after [mentioning it over the summer]({% post_url 2023-08-07-purple-heart %}), at some point, my Lemmy instance fixed the log-in problem---apparently, other people had a similar issue---and therefore, you can once again [find me on Lemmy](https://lemmy.sdf.org/u/jcolag).  Mind you, I haven't spotted many conversations of interest to me, yet, so you won't find much *activity*, but you can find me if you need another route to do so.

Also, I don't like admitting this, but after so long away, I've had trouble *remembering* that I can get into the server again, so I might not always get to things in a normal amount of time...

## Notoboto

{% github jcolag/Notoboto %}

Little things annoy me, so I *finally* themed the context menu to match the application.

Syntax highlighting should now work better for lists, level-one headings, and quotes.  The lists and quotes didn't indent subsequent lines as you'd expect, because the regular expression only caught the list "bullet" itself, rather than the full line.  All three of them, now, indent second-and-after lines far enough that it should come close to matching the text of the first line.  Oh, and the code only tries to update the syntax highlighting, if the contents of the note have changed; previously, it would go through the process on every key-press, which you wouldn't normally notice, unless you tried to scroll down a lengthy note with cursor keys and start typing...

Finally, you'll see the *start* of a search feature.  At this time, it only performs a case-sensitive search, and tracks its own search state instead of the current caret position, but it definitely proves the feasibility of finishing the feature.  It also provides functionality that I would never have gotten out of [**Miniboost**](https://github.com/jcolag/Miniboost) and that unfinished user interface toolkit.

## Next

I imagine that I'll want to spend some time finishing and improving the search-and-replace feature(s) in **Notoboto**, though I do notice library updates building up again, too.

* * *

**Credits**:  The header image is [New Wikipedia’s logo](https://commons.wikimedia.org/wiki/File:Wikipedia-logo-v2.svg) by [Nohat](https://en.wikipedia.org/wiki/User:Nohat), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
