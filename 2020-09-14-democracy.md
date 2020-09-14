---
layout: post
title: Developer Journal, International Eve of Democracy
date: 2020-09-14 08:09:23-0400
categories:
tags: [programming, project, devjournal, uxuyu]
summary: Progress on assorted projects
thumbnail: /blog/assets/A_coloured_voting_box.png
offset: -33%
---

Tomorrow is the [International Day of Democracy](https://en.wikipedia.org/wiki/International_Day_of_Democracy), a United Nations celebration of democracy in all member states.  This year's theme---perhaps unsurprisingly---is the [effects of COVID-19](https://www.un.org/en/observances/democracy-day) on democracy around the world.

That makes it a good day to get involved.  Register to vote or check your voter registration, if you're in a country where that's not automatic.  If you have an election coming up and aren't a likely vector for spreading the coronavirus or the flu, consider signing up to become a poll worker.  Volunteer for a campaign or two [to get involved with a political party]({% post_url 2020-08-30-parties %}).  As authoritarians realize that their philosophy and rhetoric don't hold water and aren't compelling to anything like a majority, they're attacking democratic institutions and it's worth fighting back, especially when fighting back is that easy.

![Voting box](/blog/assets/A_coloured_voting_box.png "Voting box")

Today is also [Hindi Divas](https://en.wikipedia.org/wiki/Hindi_Day), celebrating the adoption of Hindi as an official language of India.  I realize that India has had its own share of political problems, of late, and that Hindi is a latecomer to the subcontinent---being the "Indo" in [Indo-European](https://en.wikipedia.org/wiki/Indo-European_languages), it's more related to English and Russian than it is to most of its neighbors---but if a quarter to a third of a billion people speak something as their primary language, it's probably worth a celebration.

On to the project updates...

## Miniboost

This was just the general maintenance of updating packages, this week.

## Uxuyu

I did a little more work to make room for the eventual avatar images and also refactored the code a bit to make the database expansion easier.  Most of this week, however, started the work of pushing cached messages back to the main program for display.

It's worth mentioning that I still wouldn't recommend turning on the message-caching behavior, because it's *probably* buggy, but as long as you expect stupid problems that may eventually require destroying and re-creating your database, but it's a start.

## Entropy Arbitrage

I *finally* updated my blog-deployment script to get a count of pages under each tag.  So, if you bump over to [the tags page](/blog/tags/), you can get a rough sense of which topics occur more frequently than others.

## Next

I need to take another look at **Uxuyu**'s message-caching decisions, because they seem to potentially do the wrong things.  It may not happen this week, but I also want to see if there's some way of getting the posts from the database to the main program faster, because it *appears* that it takes longer to retrieve the cache than to receive the HTTP responses.

There are also library updates piling up that I should probably deal with.  And I may want to tinker a bit with the slide-out "trays" on the blog, so that they don't interfere with people reading on narrow screens like phones; I finally took a good look at that and it's definitely not ideal.

The input box on the [search page](/blog/search/) should probably automatically get focus, too.  That's just a stupid oversight on my part.

* * *

**Credits**:  The header image is [A coloured voting box](https://en.wikipedia.org/wiki/File:A_coloured_voting_box.svg) by [Anomie](https://en.wikipedia.org/wiki/User:Anomie), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license.
