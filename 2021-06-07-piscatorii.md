---
layout: post
title: Developer Journal, Ludi Piscatorii
date: 2021-06-07 07:11:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/PonteSantAngeloRom.png
offset: -42%
---

* Ignore for ToC
{:toc}

We don't have *great* holidays, today, so the most interesting is [*Ludi Piscatorii*](https://en.wikipedia.org/wiki/Ludi_Piscatorii), a Roman celebration of the [Tiber](https://en.wikipedia.org/wiki/Tiber).  It's a weird---and stereotypically pagan---celebration, where fishermen simply sacrificed the day's catch to the gods.  So, it's a day to *not* eat fish, I guess.

![The Tiber River](/blog/assets/PonteSantAngeloRom.png "The Tiber River")

So many fascists want their government to be the next Roman Empire, and I have to assume that the rest of the world does realize that the only thing that made them aspirational was the lack of a nearby competitor.  The reality is that there were, you know, fish holidays.

Anyway...

## Side-Story:  Grammatical Emoji?

Some readers might appreciate a peculiar issue that I ran into, which isn't technically *my* development work, but does relate to the blog.

As I've probably mentioned, after a few months posting, I decided to add a morning check on the spelling, grammar, and style for the day's blog post.  I use [Proselint](http://proselint.com/) for the bigger issues and [LanguageTool](https://languagetool.org/) for the small pieces.  You could probably pinpoint the change, because I probably suddenly started deleting the word "very" and stopped hyphenating adverb-noun pairs, among other things like no longer being subject to typos from a lousy laptop keyboard.  I keep meaning to go back to polish early posts, but haven't had the time, except when a post sees extra traffic...but that's an unrelated story, and I shouldn't digress during the digression.

In any case, [yesterday's post]({% post_url 2021-06-06-do-work %}) on the difference between claiming to be an ally and actually *being* an ally includes the rainbow flag emoji (🏳️‍🌈) when I mention Pride Month in passing.  It seems that LanguageTool didn't appreciate that, because it claimed a spelling error and suggested the following as possible corrections.

 * ☀️
 * ♂️
 * ♻️
 * ⚠️
 * ✏️
 * ✔️
 * ❤️
 * ➡️

I don't want to suspect anybody on the project of malicious intent, and I can't find anywhere in the code that could suggest that this might be intentional.  However, I think that it's safe to say that "rather than a symbol of the LGBT community, did you mean garbage or to warn people about something, instead?" is terrible optics.  It's especially bad, given that I can't remember seeing a case where the tool has complained about any other emoji.

I have some theories about what's happening---the emoji is actually four separate emojis, which could look different---but I'm definitely going to file a bug report, because someone who identifies as a gender or sexual minority is eventually going to feel that the team would rather they not use the tool.  I'll wait until just after I post this, because I want to see if it's a reproducible problem with the flag in parentheses, separate from the sentence.

## Miniboost

As I mentioned a couple of weeks ago, the default appearance of [**Miniboost**](https://github.com/jcolag/Miniboost) now uses colors from the [Solarized](https://ethanschoonover.com/solarized/) color scheme.  It seemed like the best choice, since the scheme was actually designed with some mathematical rigor and the files---which I don't actually use, but can certainly learn from---have been released under the MIT license.

While I was messing around with that, I also split the color of the in-editor text from the color of the user interface text, because I've found some cases---especially in darker environments---where it's easy to confuse the boundaries.

Because it annoyed me at the right time, I also finally fixed the issue that HTML entities in a note title would show as the raw text, `Q &amp; A` instead of `Q & A`, for a simple example.

There were also libraries to update, so I took care of the remainder for **Miniboost**.  Lesson:  Don't let them pile up.

This project just won't die, but I guess the frequency that I use it inevitably means that ideas and bugs are going to show up.

## Fýlakas Onomáton

A couple more libraries were updated here, too.

## GitHub Profile

The commit technically belongs to this week instead of last week, because the automated cycle doesn't trigger until after midnight, but for the people interested in this sort of thing, here are the changes to [my GitHub profile <i class="fab fa-github"></i>](https://github.com/jcolag).

 * I touched up the text to be more coherent.
 * I added visualizations for [interaction streaks](https://github-readme-streak-stats.herokuapp.com/demo/), [language usage](https://github.com/anuraghazra/github-readme-stats), general statistics (same repository), some [silly trophies](https://github.com/ryo-ma/github-profile-trophy), and a [view counter](https://github.com/antonkomarev/github-profile-views-counter).
   * These are for my own tracking purposes, but if someone wants to get excited about my being a "super repo creator," I guess that's fine.
   * Amusingly, my most used language is...*Java*.  Only two of my repositories have any Java in them.  [**ComicScanner**](https://github.com/jcolag/ComicScanner) is a mostly empty project that was going to be an applet (remember those?) to track versions of comic files---abandoned when the community seemed to stop caring about it---and [**Bì Shēng**](https://github.com/jcolag/bisheng) was going to be a sample [Cordova](https://cordova.apache.org/) mobile app that I intended as a bloggable project to illustrate how to attack a project in a new environment.  I guess they must both have a large amount of generated boilerplate code, so I decided to exclude those projects from the list, and those numbers make more sense.
 * I threw in a link to my [Buy Me a Coffee](https://www.buymeacoffee.com/jcolag) page.  I hadn't planned on promoting the link or looking for donations, but I'd also be lying if I said that the thought of my weird little projects paying some of my bills wasn't appealing.

The result is probably more cluttered, and the images are certainly less accessible, but I found GitHub's tracking of commit streaks somewhat motivating, back when it was available.  The other graphs might be handy, at some point, though the view count---crass as it is---is mostly just to satisfy my own curiosity.  I assume that it'll go away, after a week or so of realizing that nobody visits my GitHub profile.

## Next

As much as I'd like to finally finish [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton/), I think it's probably a better idea to add an extra commit to my "budget" and clear out as many library updates that'll fit.  Those really should never fall too far behind, and the oldest is two months old, which is unacceptable.

That should also give me time to move forward on my "secret"---unless you read the [Entropy Arbitrage newsletter](https://entropy-arbitrage.mailchimpsites.com/) or figured it out from Sunday posts---project that probably won't be Free Software at launch.

* * *

**Credits**:  The header image is [The Ponte Sant'Angelo with a view of St. Peter's Square and St. Peter's Basilica](https://commons.wikimedia.org/wiki/File:PonteSantAngeloRom.jpg), made available under the terms of the [Creative Commons Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
