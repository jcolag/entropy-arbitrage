---
layout: post
title: Developer Journal, Ensisheim Meteorite
date: 2022-11-07 06:32:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/chronicles-nuremberg-ensisheim.png
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the 530<sup>th</sup> anniversary of the [Ensisheim meteorite](https://en.wikipedia.org/wiki/Ensisheim_meteorite) crash in France, important as Europe's oldest meteorite fall that still has preserved material *and* as the earliest meteorite fall for which we have a date.  Yes, as usual, we have to treat November as a month of anniversaries.

![A woodcut from the Chronicles of Nuremberg (1493) showing the meteorite landing in Ensisheim](/blog/assets/chronicles-nuremberg-ensisheim.png "We won't go into detail on the bizarre chain of custody on this rock...")

But also, if you have citizenship in the United States 🇺🇸 and haven't already done so by mail or through early voting:  Go vote, *tomorrow*, and bring a friend or colleague to atone for your procrastination.  Grab some snacks and water, too, because everything that I've heard says to expect longer lines than most mid-term years.

That out of the way, let's talk code.

## CPREP

{% github jcolag/background-generator %}

I don't have much to report here that I haven't said before...unless I've imagined typing those things, in which case I need to work on improving my fantasy life dramatically.  Regardless, I've continued working on the basic infrastructure for getting this page to run as a standalone web app.

The `index.html` file no longer references the CSS files used by [Express.js](https://expressjs.com/), because those include URLs that require a different relative path than the standalone can use.

Similarly, I've started setting up the infrastructure to replace `fs.readFileSync()` calls with `fetch()` calls.  For the games that I've talked about over the past couple of months, it doesn't seem like a *huge* problem to use two chained callbacks to finally get the data---one to extract data from the response as an array of bytes, then another to turn that into usable information--but working with seven files of different types requires a bit more effort, especially to reuse code.

## GitHub Administrative Tasks

Somehow, I got dragged down the rabbit-hole of GitHub's "achievement" system.  Normally, I'd completely ignore this sort of clear self-promotional nonsense that will impress nobody.

Maybe it has something to do with the inane badges showing up on almost every user profile in lock-step, but something about it got my attention.  I started searching discussions of the achievements, and the simplicity of some of them convinced me to quickly take the steps required to get the achievement.

I don't think that it improves my life or career in any way, other than *maybe* now having interacted with the GitHub Sponsorship program.  But I suppose that it mildly amused me for a few minutes over a couple of days.

No, wait, something else improved.  I set [my profile repository](https://github.com/jcolag/jcolag) and the [repository for these blog posts](https://github.com/jcolag/entropy-arbitrage) to allow for Discussions, in case that interests anybody.  I didn't bother to chase the relevant achievement, but it exposed me to the new system.  And if people *use* those discussions---to recommend future blog posts or ask general questions---so much the better.

While I can't say that I recommend following in my footsteps, if you want to go on your own hunt for achievements, [this repository](https://github.com/Schweinepriester/github-profile-achievements)---I have nothing to do with it---appears to have the most up-to-date information on what people can get and the simplest path through.  And then people show up in the comments to beg for people to help them game the system, because petty people fill the Internet...

## Next

I assume that I'll continue working on **CPREP**, but I may also get distracted again.

* * *

**Credits**:  The header image is a woodcut from **The Chronicles of Nuremberg** (1493) by Hartmann Schedel, illustrating the meteorite, long in the public domain.
