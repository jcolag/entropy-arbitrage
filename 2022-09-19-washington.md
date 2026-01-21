---
layout: post
title: Developer Journal, Washington's Farewell Address
date: 2022-09-19 07:05:05-0400
categories:
tags: [programming, project, devjournal]
labels: [globe, iungimoji, mystic-t-square]
summary: Progress on assorted projects
thumbnail: /blog/assets/Valley-Forge-prayer.png
proofed: true
---

* Ignore for ToC
{:toc}

In 1796, George Washington planned to retire from office, and as the first President of the United States, chose to do so with a [series of essays](https://en.wikipedia.org/wiki/George_Washington%27s_Farewell_Address) about his, and what he hoped had become the American, philosophy.  In it, he warns of people who want to empower states or blocs of states at the expense of the overall union, supports the Constitution, warns against the consolidation of political parties, commends moral education, acknowledges the need to go into debt to invest in the country, and so forth.  Not every thought quite has the relevance that it did at the time, and some seem laughable and even hypocritical today---such as warning against permanent alliances while discussing the United States *as* a permanent alliance to protect---but enough of the points still resonate that I encourage people to read it in full.

![Washington's prayer at Valley Forge](/blog/assets/Valley-Forge-prayer.png "...and I would love another tweed scarf like this one, and what do YOU want, kid-in-the-hat?")

While you hum a few bars from **Hamilton** to yourself---those increasing numbers of you who didn't read it in school will recognize parts of it from *One More Time*---I'll talk about code.

## G.L.O.B.E.

{% github jcolag/g-l-o-b-e %}

This mostly amounts to clean-up, this week.

I added the CSS file that I mentioned overlooking [last week]({% post_url 2022-09-12-dezayas %}), so the footer no longer sits in the middle of the page.

You might also notice that I moved the link to the archived games to the configuration panel, and shifted the onus of refreshing the page to exiting that configuration panel.  It makes more sense there, both in terms of the basic workflow---people won't expect the game to restart on touching a setting---and to more easily allow for multiple options to configure.

My list of countries now has---I believe---a complete set of translations, though I unfortunately can't guarantee that it translates those countries *accurately*.

## Iungimoji

{% github jcolag/iungimoji %}

A lot of the work on **Iungimoji** looks like the work on **G.L.O.B.E.**, though later by a few days.

Therefore, much like last week, here I created the configuration modal.  Adaptations of the original process included already realizing that exiting the configuration modal should restart the game, and---probably more importantly, to me---putting the CSS in place *before* changing the HTML.

Oh, and I also fixed a reference to the query string, so that I don't need to process it twice.

## Mystic T-Square

{% github jcolag/mystic-t-square %}

While yes, I probably should have taken care of this weeks ago, I only finally noticed that **Mystic T-Square** doesn't show a background image.

It turns out that I probably copied that line from another program, and it referenced an `images` folder that...doesn't exist.  A straightforward fix, but a serious nuisance to not have an error showing oversights like this.

## Next

Now that I have a model and process for handling configuration options, I want to add the "big" configuration options for each game.  **Iungimoji** has a size parameter that could stand to persist across games.  **G.L.O.B.E.** has at least the *potential* for translation---because the file has the country names---into Breton, Chinese, Croatian, Dutch, French, German, Italian, Japanese, Korean, Persian, Portuguese, and Spanish.  And both games could stand to make it more straightforward to change the date used as the seed, which could probably piggy-back on the existing process used for the new games.

* * *

**Credits**:  The header image is [An engraving of George Washington praying at Valley Forge](https://commons.wikimedia.org/wiki/File:Valley_Forge_prayer.jpg) by John C. McRae, 1866, based on a painting by Henry Brueckner, long in the public domain.
