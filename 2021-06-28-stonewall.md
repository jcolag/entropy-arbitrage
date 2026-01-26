---
layout: post
title: Developer Journal, Stonewall Uprising
date: 2021-06-28 07:32:23-0400
categories:
tags: [programming, project, devjournal]
labels: [cprep, fylakas-onomaton]
summary: Progress on assorted projects
thumbnail: /blog/assets/ChristopherPark3358.png
offset: -31%
---

* Ignore for ToC
{:toc}

Today marks fifty-two years after the [Stonewall Rebellion](https://en.wikipedia.org/wiki/Stonewall_riots), a complex uprising against police raids on a so-called "gay bar."  Something often lost in the retellings are the roles of non-white people, such as [Marsha P. Johnson](https://en.wikipedia.org/wiki/Marsha_P._Johnson) and [Sylvia Rivera](https://en.wikipedia.org/wiki/Sylvia_Rivera), whose names should be on our mind, this time of year.

![Nearby Christopher Park](/blog/assets/ChristopherPark3358.png "Nearby Christopher Park")

A number of demonstrators congregated at Christopher Park after the first night of demonstrations, represented in the image by the (probably protected by copyright, though I admittedly didn't bother to check) white figures sculpted by artist [George Segal](https://en.wikipedia.org/wiki/George_Segal_(artist)), not to be confused with the more famous actor who passed away in March.

The week's software development is more of the focus, though, on Mondays...

## CPREP

The big change to [**CPREP**](https://github.com/jcolag/background-generator), this week, was updating the [Big Five](https://en.wikipedia.org/wiki/Big_Five_personality_traits) traits, to display them more clearly.  Using the trait name *and* names for the two extremes, the results are (in my opinion) far more readable, something like the following, without the header row.

|Low|Value|High|
|---|-----|----|
|reserved|extraversion: 5|outgoing|
|critical|agreeableness: -39|friendly|
|confident|neuroticism: 83|nervous|
|careless|exactitude: -84|organized|
|cautious|openness: 57|curious|

Along with shading the middle column, "when it comes to being agreeable, they're more critical than friendly" is more intuitive to interpret than "39% not agreeable," even when the extremes of the scale aren't quite antonyms.

I also (finally) updated the data from the CIA World Factbook.  So, if you've been concerned that the languages or religions might be falling out of date over the last few months, it should no longer be an issue.  Similarly, there's an unused pull request that adds names from Bermuda, which I've added to the naming file.

## Fýlakas Onomáton

I finally made some time for [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton).  After getting my footing to remind myself where I was on the project after more than a month away from it, I was able to start adding a process to connecting apps to the server.

I originally planned to generate an API key for each user, allowing the user to revoke and re-generate the key.  Then, I realized that I wasn't going to want to retype a GUID (or whatever) into the app.  So, a better solution was to mimic television apps:  Send the app to a fixed page on the server, which generates a short code of only letters and digits.  Then, ask the user to log in and go to the activation page to type that code.

It'll require changes to [**Doritís Onomáton**](https://github.com/jcolag/doritis-onomaton), of course, but anything I did would need *some* additions.

## Next

Yikes, I didn't paste this in when I posted.

The short version is that I expect this week to mostly focus on **Fýlakas Onomáton** and, if I finish that, going back to **Doritís Onomáton** to update it to match.

* * *

**Credits**:  The header image is [Sheridan Square](https://commons.wikimedia.org/wiki/File:ChristopherPark3358.jpg) (despite the picture clearly being of Christopher Park) by an uncredited photographer, made available under the terms of the [Creative Commons Attribution-Share Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
