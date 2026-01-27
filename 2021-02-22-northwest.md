---
layout: post
title: Developer Journal, Northwest States Anniversary
date: 2021-02-22 06:46:23-0400
categories:
tags: [programming, project, devjournal]
labels: [cprep, nonogram]
summary: Progress on assorted projects
thumbnail: /blog/assets/1889ConstitutionalConventionParadeBismarkND.png
offset: -61%
---

* Ignore for ToC
{:toc}

We narrowly missed a few interesting holidays that we (the blog) will presumably pick up in future years, but the big anniversary in the United States is probably the signing of the [Enabling Act of 1889](https://en.wikipedia.org/wiki/Enabling_Act_of_1889), which would create Washington State, Montana, North Dakota, and South Dakota.

![Constitutional Convention Parade](/blog/assets/1889ConstitutionalConventionParadeBismarkND.png "Constitutional Convention Parade")

Yesterday also kicked off the beginning of [National Engineers Week](https://en.wikipedia.org/wiki/National_Engineers_Week_(U.S.)) in the United States.  Since it's a bit pretentious to celebrate (among) the best-paid workers in the country who often refuse to unionize, it has come to be a celebration of the importance of [STEM subjects](https://en.wikipedia.org/wiki/Science,_technology,_engineering,_and_mathematics).

## Picture to Nonogram

The [**Picture to Nonogram**](https://github.com/jcolag/picture-nonogram/) project is now essentially complete, plus or minus any tweaking and peripheral scripting.  The timer now ends when the user completes the puzzle, it links to the original image when the image is displayed, and I've cleaned up most of the code.

It's solid enough that I have started posting a daily puzzle every midnight (Eastern time), as I [announced yesterday]({% post_url 2021-02-21-nonogram %}).

## CPREP

A brief flash of inspiration also led me to revisit [**CPREP**](https://github.com/jcolag/background-generator), dealing a bit more with personality traits.

I added a completely superficial generation of so-called [Big Five](https://en.wikipedia.org/wiki/Big_Five_personality_traits) traits, the model with some actual statistical research backing it.  It'd be better if it was based in something where the material to learn about it was in the public domain, since I believe that everything else in the system comes from a public domain source, but since this is literally just five pairs of names, it's probably more or less safe.

I also decided to quickly use the person's generated age range and the Chinese zodiac sign to provide approximate years that the person could have been born.  It's not perfect, since some ranges are too short to cover all possible signs, and it completely neglects that the sign doesn't change on the first of January.  But I'd call it a decent first pass.

## Next

I should continue the cleanup work for **Picture to Nonogram** and include the script that I use to archive the previous day's puzzle and generate the new one.  It would also be nice to make the new **CPREP** changes more sophisticated, such as adjusting the starts of the years and possibly using astrological information to adjust the Big Five values.

* * *

**Credits**:  The header image is [1889 Constitutional Convention parade in Bismark, North Dakota at Main and 4th streets](https://digital.denverlibrary.org/digital/collection/p15330coll22/id/68795) by David Francis Barry, long in the public domain.
