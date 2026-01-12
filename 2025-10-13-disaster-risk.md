---
layout: post
title: Developer Diary, Disaster Risk Reduction
date: 2025-10-13 07:07:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [codeberg-move, glance, key-wand, mini-server, qr-frame]
summary: Progress on assorted projects
thumbnail: /blog/assets/Turun-palo-1827.png
offset: -30%
description: This week's projects include my server, the AttaCard resolution code, Translations, Etched Windows, old programming languages (PosTuring, Thue, TM Asm), mostly moving from GitHub, plus Ham Newsletter and new project Key Wand.
spell: ZnydPZ Genoan PosTuring AttaCard Shiori keywand Clearbit Thue vlWUKL Asm tmasm IOCCC Séjour Mulâtre Borland Finnberg
proofed: true
---

* Ignore for ToC
{:toc}

Today, to help me avoid ranting about Christopher Columbus *again*[^ZnydPZ], we observe the [International Day for Disaster Risk Reduction](https://en.wikipedia.org/wiki/International_Day_for_Disaster_Risk_Reduction), encouraging everyone, resident and official alike, to build more disaster-resilient communities.  In the United States, given that we now have a national government whose solution for natural disasters lies somewhere between denial and bribery, that may resonate a bit more deeply than it has in previous years.

[^ZnydPZ]:  He lied about his credentials to get funding, treated the natives so poorly that even the Spanish imperial government convicted him and gave him a life sentence, compiled and published a list of favors he believed that people owed his heirs due to his brilliance, went to the grave insisting that he made it to India, only became an American icon because European powers claimed everybody less pathetic, and required an entire alternate-universe history where everybody believed in Flat Earth theory until this Genoan creep sailed to definitely *not* India.  Oh, and he tried to become an end-times prophet near the end of his life (again, in prison), a totally normal and healthy thing to do.  You've heard me go through this before, I assume, or you can track down prior years when I couldn't find a better holiday for early-to-mid October...

![After the Great Fire of Turku](/blog/assets/Turun-palo-1827.png "A little Spackle and two hundred years will fix that right up.")

We also *do* have what many of us in the United States now more properly refer to as [Indigenous Peoples' Day](https://en.wikipedia.org/wiki/Indigenous_Peoples%27_Day_%28United_States%29).

With that, on to the week's projects.

## Mini-Server, Part 14

I haven't really found a solid use for it, but [Glance](https://github.com/glanceapp/glance/tree/main) impressed me enough to install it on my server.  It'll take some time to learn the configuration well enough that it can actually show information that interests me, but it does look fairly nice.

### QR Frame, Round 2

Oh, I did hear back on my [QR Frame question](https://github.com/zhengkyl/qrframe/issues/4) about hosting it.  The creator did a bit of work that *might* do the trick for some people.  It didn't quite work for my setup, but I'll assume for now that has more to do with my not reading something properly.

## PosTuring

{% codeberg jcolag/PosTuring %}

Continuing the process of moving my old programming languages over to Codeberg, this repository holds an interpreter for a language that closely mimics Emil Post's [Post-Turing Machine](https://en.wikipedia.org/wiki/Post%E2%80%93Turing_machine), standing as one of the handful of unique, complete models of computation that appeared at around the same time from independent research.

And connecting the *T*s in the names of the two mathematicians credited gives us the English word [posturing](https://en.wiktionary.org/wiki/posturing), which made me happy at the time...

## AC Resolve

{% codeberg jcolag/ac-resolve %}

Last week, I reintroduced the [AttaCard Generator](https://codeberg.org/jcolag/attacard-generator), so it made sense to also bring this project across, a first pass at implementing game mechanics for the (hypothetical) card game.

## Ham Newsletter

{% codeberg jcolag/ham-newsletter %}

While I bumped a couple of library versions for the code, here, based on GitHub's advice, I mainly have the---I hope working---script to get the month's worth of bookmarks from [Shiori](https://github.com/go-shiori/shiori).  I based it on existing scripts that interact with a REST API, and worked from the [advice received](https://github.com/go-shiori/shiori/discussions/1154) from the project creator last week.

## Key Wand

{% codeberg jcolag/keywand %}

You might recall, in previous weeks, my trying and failing to get [Cloverleaf](https://cloverleaf.app/) to work installed locally.  At some point, I said that, since the application really only needs a handful of routine HTML elements for a user interface and some math to create arbitrarily long passwords.  Well, that idea stuck in my head.

I haven't *quite* finished, such as completely saving and using the options.  However, by using the JavaScript from Cloverleaf and removing/replacing anything that wouldn't serve staticly, it doesn't produce the same passwords as the inspiration, but it absolutely works.  If you ignore the options screen, you can even [try it out](https://jcolag.codeberg.page/keywand/) from Codeberg Pages.

The domain/organization does something semi-interesting, or I suppose *will* do it once I finish the code for the options.  It has two mutually exclusive success modes, each of which does something different but useful in different cases.

In the version that most mimics Cloverleaf, if you provide a recognized name (that you can autocomplete) such as `Wikipedia`, then Key Wand will use Cloverleaf's (possibly outdated) password data to set the minimum/maximum length and valid character set.

However, you can also provide a domain name such as `wikipedia.org`.  In this case, if you have set the API key, then it will validate the name by pulling the logo from [Logo.dev](https://www.logo.dev/)[^8RLLzx].  This should help ensure that you definitely have a consistent password by showing the logo, but doesn't do any work trying to make sure that the generated password fits the site's requirements like the previous approach does.

[^8RLLzx]:  The Logo.dev team created the site to replace the more famous Clearbit, which Hub Spot recently purchased and plans to shut down in around seven weeks when this post goes out.  In theory, the search API could plausibly try to tie the domain name to the password requirements.

## Thue

{% codeberg jcolag/Thue %}

Back to programming languages, this also continued the idea of working with minimal or obscure computational models.  In this case, the language operates as a series of grammar transformations.

As mentioned in the documentation, I believe that for many years, the [language's Wikipedia article](https://en.wikipedia.org/wiki/Thue_%28programming_language%29) made editors hesitant to delete [my own Wikipedia article](https://web.archive.org/web/20161226221754/https://en.wikipedia.org/wiki/John_Colagioia)[^vlWUKL], though ultimately deleted.  

[^vlWUKL]:  For the record, best I could figure, one of my former students put pages together for a lot of the school's teaching staff at the time.  Mine probably survived longer than most, even though NYU started playing whack-a-mole with its faculty pages, because people *technically* recognized my name from other projects like this.  It didn't get archived anywhere that I can find it, but I believe that my first Wikipedia edit, in fact, landed on my article's Talk page, where I indicated that I probably don't qualify as notable, and so wouldn't mind if they deleted it, but would make myself available if anybody wanted to make me so...

## TM Asm

{% codeberg jcolag/tmasm %}

And I believe this makes the last of the old programming languages to migrate.

In this case, I borrowed (but didn't actually use in the repository) the Turing Machine emulator for a [1989 IOCCC winner](https://www.ioccc.org/1989/paul/index.html), and wrote an assembler (a compiler for an assembly language) to generate the code format required by the emulator.

If I remember correctly, the example program for generating the Fibonacci sequence *should* assemble to the code used in the IOCCC entry, give or take.  I have not confirmed that, however.

## Translations

{% codeberg jcolag/translations %}

As many of you know, I have a soft spot for reading old fiction.  During my find-public-domain-elements-to-reuse phase, I made ample use of [Project Gutenberg](https://www.gutenberg.org/) when I could, helped get some predecessors to the [Digital Comic Museum](https://digitalcomicmuseum.com/) running, picked up the typical smattering of reprints of the classics, tracked down early printings of many more obscure books and magazines than I should probably admit to, and have even paid handsomely for a handful of *photocopies* of original sources.  While I have stopped buying them, I still occasionally poke around for obscure stories, such as yesterday's post [featuring an alternate history of the first major trans-Atlantic crossing]({% post_url 2025-10-12-beauchene %}), which I have had transcribed for years in case I needed it.

In any case, you can't get all of it in English.  Some, as far as I know, doesn't have an English translation.  Others have translations, but usually only in hard-to-find sources, and never in a condition where people have permission to repurpose the contents.  This repository started to fix that with Victor Séjour's [Le Mulâtre]({% post_url 2020-02-23-mulaitre %}), which I translated to English (from the French) for a Black History Month post early in the blog.

Nothing has happened in here since, but I do have at least one other story that I expect to eventually serialize on the blog, so you might watch for that someday.

## Etched Windows

{% codeberg jcolag/etched-windows %}

Another blast from the distant past, I have moved my old Etch-A-Sketch{% emoji trademark %} repository over here, too.  I wrote this for Windows 3.1 and eventually (reluctantly) Windows 95, starting in a previous century, so don't even know if you could find a legitimate way to build it today.  But it did eventually have a wide assortment of absurd features, including a LOGO-like interpreter, a way to connect multiple instances to "collaborate" on images, and more.

To compile it, I *believe* that you'd need a contemporary version of [Borland Turbo C](https://en.wikipedia.org/wiki/Turbo_C) for (at least) the resource compiler.  For the full experience, you would also need [Install Shield](https://en.wikipedia.org/wiki/InstallShield) to create the installer from the included script.  And heck, I don't even remember how to build a help file anymore...

## Next

I'll probably run out of worthwhile repositories to bring over to Codeberg, soon, so I'll continue doing that until I run out.  And work on Key Wand will wrap up.  And I might have other projects waiting in the wings...

* * *

**Credits**:  The header image is [After the Great Fire of Turku](https://www.kansallisgalleria.fi/fi/object/573977) by Gustaf Wilhelm Finnberg, long in the public domain due to expired copyright.
