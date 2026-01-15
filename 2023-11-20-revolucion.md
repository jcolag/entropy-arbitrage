---
layout: post
title: Developer Diary, Día de la Revolución
date: 2023-11-20 07:34:05-0500
categories:
tags: [programming, project, devjournal]
labels: [blog, json-resume, pebble]
summary: Progress on assorted projects
thumbnail: /blog/assets/Feliz-Dia-de-la-Revolucion-Mexico.png
teaser: This week's projects include my Pebble archive, a theme for JSON Resume, and some blog corrections.
spell: Día de la Revolución Cucaracha Homestuck Hussie Feliz Dia Revolucion
---

* Ignore for ToC
{:toc}

Today, Mexico celebrates [Día de la Revolución](https://en.wikipedia.org/wiki/Revolution_Day_%28Mexico%29), commemorating the start of the [Mexican Revolution](https://en.wikipedia.org/wiki/Mexican_Revolution), which overthrew the [Díaz](https://en.wikipedia.org/wiki/Porfirio_D%C3%ADaz) political machine.

Closer to home---wherever you live, assuming that you don't live in Mexico, either---then you might wish to spare a moment, today, for the [Transgender Day of Remembrance](https://en.wikipedia.org/wiki/Transgender_Day_of_Remembrance), memorializing people murdered due to transphobia.  And maybe we could...I don't know, *stop* with the whole "bigotry makes sense as a reason to murder" thing. {% emoji shrug %}

![Children from the Montessori Kindergarten singing "La Cucaracha"](/blog/assets/Feliz-Dia-de-la-Revolucion-Mexico.png "The caption tells me what they sang; I couldn't confirm it beyond that, if anybody needs authentication")

Anyway, on to the projects...

## Pebble

{% github jcolag/pebble %}

I believe that I have squeezed all Pebble's actual intellectual property out of my archive of posts.  I may have overlooked something, though, so if anybody happens to investigate the archive in detail, please report anything that looks shady.

In addition, all pages now have an (admittedly bland) dark mode.

Finally, the main page now has an explanation for the existence of the archive, so that the page doesn't start by confronting people with thanking me.

## Thorough (JSON Resume Theme)

{% github jcolag/jsonresume-theme-thorough %}

A former colleague---who shall remain nameless, since they presumably wouldn't want me announcing their current interest in such things---took an interest in [JSON Resume](https://jsonresume.org/).  In talking, they raised the issue that none of the themes appears to use the complete data *and* renders it cleanly to the PDF export.

Because I have a soft spot for [plain text formats]({% post_url 2022-04-27-plain-text %}), I took this defect as a challenge, and started work on my own theme, based on the default [boilerplate theme](https://github.com/jsonresume/jsonresume-theme-boilerplate).

In doing so, I believe that I have discovered that I greatly dislike working with [Handlebars](https://handlebarsjs.com/), which has the most inconsistent syntax that I've ever seen.  But hey, we use what they make available...

Also of possible interest, I believe that this makes the first project that---for consistency with the ecosystem, not my preference---I have released under the MIT license.  I don't yet know if I'll bother to publish it on NPM or JSON Resume's theme registry.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage %}

After publishing three posts on popular web comic **Homestuck** for the [Free Culture Book Club](/blog/tag/bookclub)...

 * [Part 1]({% post_url 2023-11-04-homestuck-1 %})
 * [Part 2]({% post_url 2023-11-11-homestuck-2 %})
 * [Part 3]({% post_url 2023-11-18-homestuck-3 %})

...People brought to my attention that I had misread copyright notices on the profusion of overlapping fan sites, and *erroneously* came to the conclusion that creator Andrew Hussie had ceded rights to the franchise into the public domain.  In reality, fans have gifted various discussions and art into the public domain, but Hussie retains the copyright to the original.

As such, I have rewritten the posts as apologies, and left the discussion of the comic in the git history.  Honestly, it surprises me that this sort of thing doesn't happen more often, given that anybody could (illegally, but plausibly) impersonate a creator or creator's estate to claim that they have released some famous work under a public license...

## Next

I need to finish up the **Thorough** stylesheet.  Depending on how my week goes, I may go back to some recent projects or work on something new.

* * *

**Credits**:  The header image is [¡Feliz Dia de la Revolucion Mexico!](https://www.flickr.com/photos/uteart/4119501357/) by [Ute](https://www.flickr.com/photos/uteart/), made available under the terms of the [Creative Commons Attribution 2.0 International](https://creativecommons.org/licenses/by/2.0/) license.
