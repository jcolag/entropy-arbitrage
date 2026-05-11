---
layout: post
title: Developer Diary, Minnesota Statehood
date: 2026-05-11 07:44:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update]
summary: Progress on assorted projects
thumbnail: /blog/assets/Pose_lake_Minnesota.png
offset: -26%
description: This week's projects include the blog's code and more library updates.
spell: Unported CPREP Notoboto Priedhorsky
proofed: true
---

* Ignore for ToC
{:toc}

Today, at least in the United States, we celebrate the ratification of [Minnesota](https://en.wikipedia.org/wiki/Minnesota)'s statehood.  Even if you don't spend much time in the United States, you probably recognize Minnesota from its fairly significant representation in the news as a sometimes-literal battlefield against Homeland Security officers hunting for anybody who might have overstayed on a visa at some point.  Workers and businesses staged the general strike and boycott at the end of January, providing the template for the national action earlier this month.

![Pose Lake in the Boundary Waters Canoe Area Wilderness. Sunset over Pose Lake, a small lake accessible only by foot. Boundary Waters Canoe Area Wilderness, Minnesota](/blog/assets/Pose_lake_Minnesota.png "I could've gone with something governmental, but absolutely not when a picture like this sits right on the Wikipedia page...")

And with that, on to the week's projects.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

Following up on some minor glitches last week, the mock-keyboard keys---such as {% key Any %}---now stay on a single line.  The plugin doesn't see much use, but on the rare occasions that a key has multiple words on it, wrapping to the next line looks fairly ugly.

Also, because it came up recently, any links to [Wikitravel](https://wikitravel.org/en/Main_Page) now show on the blog with the Wikimedia logo.  To my disappointment, neither icon set that I use includes a Wikitravel-specific logo, but most places that I've thought to check have pretty thin information, so I don't exactly expect to point there too often on the blog.

## Library Updates

Still working through the backlog, I needed to bump library versions for [Bicker](https://codeberg.org/jcolag/Bicker), the [CPREP Background Generator](https://codeberg.org/jcolag/cprep-background-generator), [Ham Newsletter](https://codeberg.org/jcolag/ham-newsletter), and [Notoboto](https://codeberg.org/jcolag/Notoboto)'s semantic search code.

## Next

It looks like the library versions have started stacking up faster than I get through them, so this week may not change much from last week.

* * *

**Credits**:  The header image is [Pose Lake, Minnesota](https://commons.wikimedia.org/wiki/File:Pose_lake_Minnesota.jpg) by [Reid Priedhorsky](https://en.wikipedia.org/wiki/User:R27182818), made available under the terms of the [Creative Commons Attribution-Share Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
