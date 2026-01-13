---
layout: post
title: Developer Diary, Susan B. Anthony
date: 2024-11-18 07:12:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, ruby]
summary: Progress on assorted projects
thumbnail: /blog/assets/Daily-Graphic-Woman-Who-Dared.png
offset: -30%
description: This week's projects include the blog's code and a batch of library version updates.
spell: CPREP Fýlakas Onomáton
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the 152<sup>nd</sup> anniversary of [Susan B. Anthony](https://en.wikipedia.org/wiki/Susan_B._Anthony) and her fourteen conspirators for having the *unmitigated gall* to cast votes in the 1872 presidential election despite their lady-parts.  Without their brave civil disobedience and capture of the media's attention before and during the trial, it might have taken longer for the United States to grant universal suffrage.

![A caricature of Susan B. Anthony on the front page of the New York Daily Graphic](/blog/assets/Daily-Graphic-Woman-Who-Dared.png "Why has nobody turned this sketch into a Saturday morning cartoon?")

Anyway, on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

The Creative Commons license-logo plugin now mostly works.  Based on the parameter, it picks the HTML entities that represent the license components, and wraps them in a `span` element for later styling.  As I've said, I don't know how much I'll use it, because almost no fonts support the characters on top of *actual* text, but the option now exists to conveniently note that an organization releases its work under {% cc by-nd %} (CC BY-ND) and have it show neatly on the blog...though at the expense that everybody else sees unknown Unicode characters, the boxes with numbers.

I say that it "mostly works," because using a Ruby hash object to look up the license information feels extremely clunky.  Specifically, I use this, provided in its entirety, in case somebody needs a similar mapping or has a better idea.

```ruby
licenses = {
  '' => '&#xa9;',
  '0' => '&#x1f16d;&#x1f10d;',
  'by' => '&#x1f16d;&#x1f16f;',
  'by-nc' => '&#x1f16d;&#x1f16f;&#x1f10f;',
  'by-nc-nd' => '&#x1f16d;&#x1f16f;&#x1f10f;&#x229C;',
  'by-nc-sa' => '&#x1f16d;&#x1f16f;&#x1f10f;&#x1f10e;',
  'by-nd' => '&#x1f16d;&#x1f16f;&#x229C;',
  'by-sa' => '&#x1f16d;&#x1f16f;&#x1f10e;',
  'pd' => '&#x1f16e;'
}
```

Everything except for the copyright symbol {% cc %} and the public domain mark {% cc pd %} start with the Creative Commons mark, followed by the specifics for the license.  As mentioned, it'll do the job, but this feels like a non-idiomatic way of specifying that to me.

Anyway, in addition to that, I stopped deferring the JavaScript code for [Prism](https://prismjs.com/).  It looks like it needs to run synchronously to style the code-blocks, leaving readers (for a week or two) looking at gray code on a white background, which did nothing for readability.

## Library Updates

Without much of a plan, I noticed that I needed to bump library versions for [**Bicker**](https://github.com/jcolag/Bicker), the [**Cohost Export**](https://github.com/jcolag/cohost-export), [**CPREP**](https://github.com/jcolag/background-generator), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), the [**Renewals Database**](https://github.com/jcolag/RenewDB), and [**Slack Up**](https://github.com/jcolag/slackup).

## Next

Once again, I find myself without much of a plan.  I'll probably polish off the remaining library updates, find some way of sneaking the license names into my Creative Commons plugin, and probably mess with the blog's styling again, but otherwise, we'll need to find out together...

* * *

**Credits**:  The header image is [Daily Graphic - Woman Who Dared - caricature of Susan B. Anthony](https://commons.wikimedia.org/wiki/File:Daily_Graphic-Woman_Who_Dared-caricature_of_Susan_B._Anthony.jpg) by an unidentified artist (MW?) for the **New York Daily Graphic**, long in the public domain due to an expired copyright.
