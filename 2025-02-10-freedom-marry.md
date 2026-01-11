---
layout: post
title: Developer Diary, Freedom to Marry Day
date: 2025-02-10 07:12:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, open-badges]
summary: Progress on assorted projects
thumbnail: /blog/assets/Wedding-in-New-Orleans-November-11-2017.png
description: This week's projects include the blog's code and more work on Open Badges.
spell: Webmentions Rubocop gitignore
proofed: true
---

* Ignore for ToC
{:toc}

In the United States, today we mark [National Freedom to Marry Day](https://en.wikipedia.org/wiki/National_Freedom_to_Marry_Day), celebrating---and, before we recognized it as legal, promoting---same-sex marriage.  It conveniently lands on [Abraham Lincoln](https://en.wikipedia.org/wiki/Abraham_Lincoln)'s birthday, which also has developed connotations of fighting for equality.

![A wedding between two men, surrounded by the wedding party](/blog/assets/Wedding-in-New-Orleans-November-11-2017.png "Jazz Hands seems to have missed the point...")

And with that, on to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Because I've needed to link to the sites, recently, the styles added more link-annotation icons.  You'll now see specific icons for the following sites.

- [IMDb](https://imdb.com)
- [Instagram](https://instagram.com)
- [JSON](https://json.org)
- [Kickstarter](https://kickstarter.com)
- [Open Badges](https://openbadges.org)
- [YAML](https://yaml.org)

Another Mastodon domain got in there for the Webmentions, too.

In addition, because of something that I'll talk about for *next* week---and you can probably see in the above list, if you visit the post on the web---the dark mode coloration now has a shadow to outline the icon and make it more visible against the darker background.

## Badging

{% github jcolag/badging %}

The credential-embedding tool no longer takes the single command-line arguments for a data file, since it previously added arguments for individual organization and recipient/badge files, given that the former should change far less frequently than the latter.  Some seemingly constant data has now become part of the code itself, so that nobody needs to worry about maintaining badge types and schema URLs.

You'll also see improved method signatures to better comply with [Rubocop](https://rubocop.org/)'s checking, and the repository also complies with [REUSE](https://reuse.software/).  The latter includes a `.gitignore` file to remove my experimental badges from consideration.

Finally, now that the code includes that aforementioned constant data, the repository now has a sample issuer organization YAML file, showing that it only needs an ID, name, and type.

## Next

Behind the scenes, I upgraded the version of the [Simple Icons](https://simpleicons.org/) font.  While it gives me a wider range of icons---for example, in the credits for this post, you might notice that Wikimedia Commons now has a different icon than other Wikipedia properties---it changed the Unicode code-points assigned to the characters, breaking my stylesheet.  That means that I've needed to update a lot of that section of code, and will need to confirm that I got it right, section by section.

While I had to do all that work anyway---I should probably automate the process, now that I know that this problem might happen on upgrades---I also noticed that their CSS file, which I only use as a guide for creating my links, includes *color* suggestions for the icons.  As an experiment, then, I have added colors to the icons in use, in hopes of making the icons clearer even at small sizes.

All that work needs verification and pushing to the repository, so expect that to happen during the week, in addition to whatever I have time to figure out on Open Badges.

* * *

**Credits**:  The header image is [Wedding in New Orleans, November 11, 2017](https://commons.wikimedia.org/wiki/File:Wedding_in_New_Orleans,_November_11,_2017.jpg) by [Jami430](https://commons.wikimedia.org/wiki/User:Jami430), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
