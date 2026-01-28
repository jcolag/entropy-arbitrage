---
layout: post
title: Developer Journal, Bloody Thursday (Belated)
date: 2020-07-06 07:04:23-0400
categories:
tags: [programming, project, devjournal, uxuyu]
labels: [blog, ethics, harm, safety, uxuyu]
summary: Progress on assorted projects
thumbnail: /blog/assets/Confrontation_between_a_policeman_wielding_a_night_stick_and_a_striker_during_the_San_Francisco_General_Strike,_1934_-_NARA_-_541926.jpg
offset: -30%
---

* Ignore for ToC
{:toc}

Besides some areas celebrating Independence Day on Saturday, on Sunday, Americans also commemorated the start of the [1934 West Coast Waterfront Strike](https://en.wikipedia.org/wiki/1934_West_Coast_waterfront_strike), when longshoremen in every port along the West Coast of the United States refused to work for four days.  Two workers were killed by police, with the now-familiar conflicting reports of the police innocently responding to reports of violence and protesters coming away injured versus the police provoking the protesters to violence.

![A confrontation](/blog/assets/Confrontation_between_a_policeman_wielding_a_night_stick_and_a_striker_during_the_San_Francisco_General_Strike,_1934_-_NARA_-_541926.jpg "A confrontation")

Over the course of the protests, truck drivers, movie theaters, night clubs, and many small businesses joined the strike.  A fractured union with opportunistic leaders seemed to hand a victory to the employers, but smaller strikes proved that the full strike had strengthened employees and weakened employers as they gave in to demands.

Anyway, if you like desktop applications for obscure social networks, this week is for you...

## Uxuyu

I've been able to spend a good amount of time on **Uxuyu**, this week.

When posting, the application now auto-expands @-references, so that you don't need to know the URL of the people that you want to talk to.  That is, if you send a message referring to `@jcolag`, my handle will be replaced in your feed with:

 > `@<jcolag https://john.colagioia.net/twtxt.txt>`

It's not *perfect*, of course.  Multiple people can take the same handle, which is a problem.  But it's a good-enough solution for most people, for now.  All things considered, we're currently handling name collisions poorly in general.

**Uxuyu** also now supports a small set of commands.  You can `/follow` or `/unfollow` one or more users.  You can call `/registry` to download information from the user registries, mostly for my debugging.  And you can call `/peer` to get all currently known feeds, in case you don't want to wait for the next cycle.

## Entropy Arbitrage

The first issue of mailing list has been delayed while I try to work out some ideas.

## Non-Code

Over at the [Digital Comic Museum](https://digitalcomicmuseum.com/), where we make sure comics whose copyrights have lapsed have a home (though I still don't understand the date cutoff), we've been discussing how to handle the fact that many older comic books don't have the same cultural sensitivities that audiences expect today.  So, I've been writing something that serves as a disclaimer and content advisory...but is also brief enough that the people who'll benefit from reading it will see it as useful.

As you might guess, I don't generally trim down what I write, so that has been an interesting experience.

We may go with something else, but whether it goes live or not, I'll make sure people can read it.

## Next

The remaining feature I want to see in **Uxuyu** is to reduce the frequency of accessing feeds that aren't available or that haven't updated, so I *may* work on that.  However, it also occurs to me that I should log my output instead of sending it to the console.

It might also make sense to look at a different library to make web requests.  The [request](https://www.npmjs.com/package/request) package is deprecated---which would be fine for the experimental nature---*but* many users haven't kept up their TLS certificates and there is at least one user who hosts their feed on a [gopher](https://en.wikipedia.org/wiki/Gopher_(protocol)) server.  **Uxuyu** currently can't access either kind of feed.

I have some other things I might want to do, too, like sorting the @mentions, making it possible to view the feed of somebody you don't follow, and it's probably time to refactor the main window, since it's almost twice as long as JSLint wants.

Otherwise, I *might* be nearly done with the project in the next week or two, assuming that I don't find any bugs.  Or, rather, the degree to which the project is unfinished is because the necessary features aren't available in [Proton Native](https://proton-native.js.org/#/), yet.  Regardless, as I expected, having **Uxuyu** makes [twtxt](https://twtxt.readthedocs.io/en/latest/) *much* more pleasant to keep up.

I also want to get back to [**VSCode Rat](https://github.com/jcolag/vscode-rat), since I haven't touched that all week.

* * *

**Credits**:  The header image is [Confrontation between a policeman wielding a night stick and a striker during the San Francisco General Strike, 1934 - NARA](https://commons.wikimedia.org/wiki/File:Confrontation_between_a_policeman_wielding_a_night_stick_and_a_striker_during_the_San_Francisco_General_Strike,_1934_-_NARA_-_541926.jpg), courtesy of the U.S. Information Agency and placed into the public domain as a work prepared by the United States government.
