---
layout: post
title: Developer Diary, World Meteorological Day
date: 2026-03-23 07:44:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update]
summary: Progress on assorted projects
thumbnail: /blog/assets/world-meterological-days.png
description: This week's projects include updates to the blog and some library updates.
spell: Ahmadiyya SaLaVI
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate [World Meteorological Day](https://en.wikipedia.org/wiki/World_Meteorological_Day), commemorating the 1950 creation of the World Meteorological Organization.  I suppose that it doesn't provoke much more discussion than that.

![A person in a lab coat standing in front of the Sun, contrasted with aerial photography of somewhere on Earth's surface, declaring World Meteorological Day(s), the ocean, our climate, and weather](/blog/assets/world-meterological-days.png "I don't know if lab coats protect against solar flares")

If you'd like something a bit flashier, we also have [Pakistan Day](https://en.wikipedia.org/wiki/Pakistan_Day), celebrating the country's adoption of its constitution, and [Promised Messiah Day](https://en.wikipedia.org/wiki/Promised_Messiah_Day) among Ahmadiyya Muslims.

And on to the week's projects.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

While they admittedly don't show up as often as one might expect, at some point, the information tables became borderline unreadable.  Hazarding a guess, it could have happened when adding the dark color scheme, where mistaking a name could have forced things off the track.  In any case, those tables should now have a much higher contrast.

You'll also see some updated verbiage and links, here and there, plus a link on blog pages to the [`human.json`](https://codeberg.org/robida/human.json) thing that I mentioned last week.  At some point, it may come down.  It feels complicit with so-called [dead Internet theory](https://en.wikipedia.org/wiki/Dead_Internet_theory) by implying that we should expect slop as the default on the general Internet.  And that certainly holds true on big corporate sites, because they have no purpose *other* than to divert your attention in order to shove more ads into your retinas.  But for the Internet at large, the statistical long-tail of smaller websites, the overwhelming majority of domain names, the web that *matters* to anything other than stock portfolios, the idea doesn't hold water, because a slop-filled website doesn't matter unless it has high traffic.

Plus, like everybody else, I don't appreciate when a website demands that I verify my humanity by...doing tedious tasks best left to a computer, for some reason.  Why, then, would I want to do that on my website?  If people believe that my writing---and you've all *seen* my writing---looks like regress-to-the-mean, personality-free, "clean" LLM droppings, then they probably won't believe a JSON file.

Why bother trying it out, then?  I probably mentioned these ideas at some point, but I see two useful reasons for setting this up.  First, more than one person has asked me about the various no-AI "badges."  None of them strike me as viable, and a couple look like outright scams where they'll "certify" your work for a fee, but the web-of-trust angle, here, seems like the least-objectionable version of the idea.  And second, this model can work for *other* assertions that work better with external validation, such as Free Culture, ecological soundness, subculture, or similar.  Change the name of the file, update the browser plugins, and you have the makings of an "also available in Lojban" (or whatever) community signifier.

## Library Updates

I needed to bump library versions for [Bicker](https://codeberg.org/jcolag/Bicker), [Mastodon Tool Trunk](https://codeberg.org/jcolag/tool-trunk), [Morning Dashboard](https://codeberg.org/jcolag/dash), and [SaLaVI](https://codeberg.org/jcolag/salavi).

## Next

If my investigation into a certain technology sparks an idea, then I'll definitely have a new project to launch this week, and probably a blog post to help other people get to the point.  Otherwise, I'll probably continue to clean up library updates, since they continue to pile up.

* * *

**Credits**:  The header image is [World meteorological days](https://commons.wikimedia.org/wiki/File:World_meterological_days.png) by [Abhishek66666](https://commons.wikimedia.org/w/index.php?title=User:Abhishek66666&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
