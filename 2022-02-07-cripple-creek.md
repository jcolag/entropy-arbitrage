---
layout: post
title: Developer Journal, Cripple Creek Miners' Strike
date: 2022-02-07 07:19:05-0500
categories:
tags: [programming, project, devjournal]
labels: [blog, dashboard, ham-newsletter, library-update, miniboost]
summary: Progress on assorted projects
thumbnail: /blog/assets/Cc_martiallaw.png
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the anniversary of the start of the [Cripple Creek Miners' Strike](https://en.wikipedia.org/wiki/Cripple_Creek_miners%27_strike_of_1894) in 1894, notable not just as a union victory, but also the only time in history---as the strike dragged on---that a United States state militia would be deployed in *support* of workers, rather than shooting at people to force them back to work.

![The town under martial law](/blog/assets/Cc_martiallaw.png "The modern world doesn't contain nearly enough of those small-wall-on-wheels gizmos...")

In any case, let's get moving on projects.

## Morning Dashboard

{% github jcolag/dash %}

The changes were relatively light for the morning dashboard generator.

The most important issue was adding "freezing rain" to the list of weather conditions that get identified in the daily bar graph.  Basically, I need to wait for these conditions to arise to see them get rejected---the code prints anything unrecognized---before the weather's name can be translated to a visual difference.  In this case, it's not perfect, but I use 🧊 the ice emoji.

Beyond that, the documentation now explains the [QPF](https://en.wikipedia.org/wiki/Quantitative_precipitation_forecast) values, and I bumped a couple of libraries.

## Miniboost

{% github jcolag/Miniboost %}

My note-taking application needed a library bumped.

Maybe more interestingly to people running Node.js applications, something changed on my system that began causing errors when running **Miniboost**, crashing the program before it could start.  Searching for the error message suggests that it's an [OpenSSL](https://en.wikipedia.org/wiki/OpenSSL) issue, probably low on the technology stack, since nothing this program does involves encryption.

The solution to the error is to set an environment variable, instructing libraries to use older versions of algorithms.

```console
export NODE_OPTIONS=--openssl-legacy-provider
```

Because I can never remember to do tedious things like this, and because I don't want to continue using obsolete encryption in *all* software, I added it to the application's `package.json` file on startup.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

The blog itself required some minor changes to the styling for the recent GitHub previews.  I'll tweak that until I'm happy, I guess.

While looking at the styles, though, I realized that the code snippets---such as you see above, setting the environment variable---had a peculiar, sickly border that looks reasonable inline (like `this`), so that has changed, as well.

Finally, I added the asset repository's metadata to the places that the development server should ignore.  Otherwise, when the [asset repository](https://gitlab.com/jcolag/entropy-arbitrage-assets) automatically commits and pushes to GitLab on Tuesday nights, the blog scrambles to update based on invisible files.

## Ham Newsletter

{% github jcolag/ham-newsletter %}

In what appears to be a recurring theme over the last few months, I ran into a snag while trying to send out the latest [**Entropy Arbitrage** Newsletter](https://entropy-arbitrage.mailchimpsites.com/)...which, yes, of *course* you should sign up to receive.  Interestingly, the first attempt succeeded, but something went wrong in the generation.  After that, the generation-side worked, but the code couldn't get the request through.

After waiting for a bit---Mailchimp has something of a reputation for making quick changes to their API and realizing that people rely on the older behavior---I started investigating the almost-worthless error message that some part of my request was a string instead of an object.  Of course, everything is sent over HTTP, so *everything* in the API is a string, but...sure.

The lack of specificity was new, but the error message dates to at least 2017, where developers were converting objects to JSON, then converting those *strings* to JSON.  Reasoning that the library I use for web requests might have added an internal convert-to-JSON step, I took out my calls to `JSON.stringify()`, which fixed the problem.

While I was already editing things, I also updated the verbiage about translating the blog.  Here's the old version.

 > Remember, all content is made available under the CC-BY-SA license, so if anybody needs to provide a translation, you don’t need my permission.

In retrospect, that comes off as if I didn't want to be involved.  So, future issues of the newsletter---did I mention that you should subscribe?---will indicate that, while I don't *need* to be involved in translation efforts, I'm also happy to help if I can.  It took nearly two years to come to that realization...

## Other Library Updates

I also bumped versions of a library on [**Generic Board Game**](https://github.com/jcolag/generic-board-game).

## Next

Uncomfortably like [last week]({% post_url 2022-01-31-medammephi %}), I don't have much of a plan for the upcoming week.

I'd like to play with some new user interface technologies, since it doesn't look like [Valence Native](https://github.com/valence-native/valence-native) has plans to keep up to date, let alone move forward.  The fact that some part of it relies on an outdated SSL implementation makes it seem like more trouble than it's worth.

* * *

**Credits**:  The header image is [Cripple Creek, Colo., under martial law, 1894](https://en.wikipedia.org/wiki/File:Cc_martiallaw.png) by Rastall, Benjamin McKie. University of Wisconsin, long in the public domain.
