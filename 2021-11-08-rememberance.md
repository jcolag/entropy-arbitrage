---
layout: post
title: Developer Journal, Intersex Solidarity Day
date: 2021-11-08 06:40:03-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Intersex_Pride_Flag.png
proofed: true
---

* Ignore for ToC
{:toc}

I talked about the situation with Intersex people on [Intersex Awareness Day]({% post_url 2021-10-25-intersex %}), so I won't go into it, here.  Today, however, is the [Intersex Day of Remembrance](https://en.wikipedia.org/wiki/Intersex_Day_of_Remembrance), also known as Intersex Solidarity Day.

![Intersex flag](/blog/assets/Intersex_Pride_Flag.png "I see no reason not to recycle the flag from two weeks ago...")

The date was chosen to commemorate the birthday of [Herculine Barbin](https://en.wikipedia.org/wiki/Herculine_Barbin), a nineteenth-century French citizen who forced the courts to repudiate their assigned gender.  Barbin wrote a memoir, which has the most confusing publication history that I've seen.  After an hour of research, I *still* can't tell if any of it was published during their lifetime or if it's just been small quotes until the recent full translation into English.

On to the week's code.

## INTERN

Work on [**INTERN**](https://github.com/jcolag/intern) continues.

The biggest deal has been organizing the search results to increase the priority when search terms are near each other.  As of this week, a file's search score is the number of times that consecutive search terms appear soon after each other, magnified if the exact search terms are used.  In other words, if **INTERN** finds the exact search phrase in a file, that file scores significantly higher than a file that only contains the stems of the search terms.

The server now also responds to requests other than searches.  **INTERN** responds to `@on` with the list of files modified on the specified date, or today, if no date is specified.  It also *almost* responds to `@ago` for files changed some number of days prior to the current date, for times when looking up the date isn't interesting; stupidly, I actually just copied the code for `@on` and forgot to change and test it, but it's hard to imagine that parsing an integer is harder than parsing a date.

Finally, there was an issue getting the modification time for a file, which I solved.

## Ask INTERN

As mentioned, I've wanted an excuse to tinker with the [Haskell](https://www.haskell.org/) programming language, so **INTERN**'s client is [**Ask INTERN**](https://github.com/jcolag/ask-intern)---whose executable I expect to name `ask`, for simplicity---is the project that will become the server's "official" client, to the extent that a personal project can have an official anything.

## Next

One significant problem that I have with using **INTERN** is that my [**Miniboost**](https://github.com/jcolag/Miniboost) note files are named with UUIDs, which isn't enlightening.  Now, I can obviously just *open* the file---I don't just want to know that search results exist, after all---but it seems like it would be easier to make sense of the results if I extracted the title from the CSON files, and maybe the note category, too.

I probably won't touch it this week, but I've also previously mentioned that I'd like to index my web history, so that it's not necessary to remember the title of a page to find it.  Updates would make an excellent job to schedule overnight, when nothing else is going on.  However, that would also require going through the process of extracting text from HTML, not to mention churning through the hundred thousand pages currently listed in my Firefox history.  Even if I filter out the probably useless visits---social media, any page that I control, shopping, weather, searches, and so forth, which accounts for a lot---that's still a huge list of pages.

Otherwise, I'll mostly work on **Ask INTERN**, probably, since it doesn't do any real work, yet.

* * *

**Credits**:  The header image is the [Intersex Pride Flag](https://ihra.org.au/22773/an-intersex-flag/) by Morgan Carpenter and AnonMoos, made available under the terms of the [Creative Commons CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/deed.en).
