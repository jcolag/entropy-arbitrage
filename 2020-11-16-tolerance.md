---
layout: post
title: Developer Journal, International Day for Tolerance
date: 2020-11-16 06:32:23-0400
categories:
tags: [programming, project, devjournal]
labels: [javascript, twitterbot]
summary: Progress on assorted projects
thumbnail: /blog/assets/hand-rock-wood-floor-cobblestone-wall-652711-pxhere.com.png
offset: -40%
---

* Ignore for ToC
{:toc}

![Handshake](/blog/assets/hand-rock-wood-floor-cobblestone-wall-652711-pxhere.com.png "Handshake")

As the title suggests, today is UNESCO's [International Day of Tolerance](https://en.wikipedia.org/wiki/International_Day_for_Tolerance).  Not much to be said about tolerance that I haven't said regarding the [Paradox of Tolerance]({% post_url 2020-07-12-tolerance %}), of course, so tolerate people, but be intolerant of intolerance of people.

## Replybrary

I believe that the [**library-twitterbot**](https://github.com/jcolag/library-twtterbot) is just about ready for deployment at [@replybrary](https://twitter.com/replybrary).  I want to clean up some code (see below) and still haven't collected the full set of URLs I want to start with, but expect a launch this week, with a brief announcement on Sunday.

The big piece I was missing until this week was reading any tweets that might have been missed.  Using the [twit]() library that I was already working with, that's just a matter of the following.

```javascript
twitter.get(
  'statuses/mentions_timeline',
  {
    count: 200,
  },
  (err, data, response) => {
    // Do something with data
  },
);
```

The `count` option is a maximum number of mentions to retrieve, because the count includes deleted and otherwise unreadable tweets that won't be returned.  In the case of **replybrary**, it processes the array of returned tweets, one by one, with the existing processing code skipping any tweet that has been seen previously.

I also added [ESLint](https://eslint.org/) configuration, which caught a couple of minor errors that could have been an issue.

## Next

I see a couple of minor places where **library-twitterbot** can be improved, such as some error reporting and I should probably run a [Prettier](https://prettier.io/) style check for consistency.

Otherwise, insert the usual "I need to get back to other projects," "I should start collecting issues for **Uxuyu**," and so forth.  Plus, I did throw together one small project that I'll upload for whoever needs the reference.

* * *

**Credits**:  The header image is [untitled](https://pxhere.com/en/photo/652711) by an uncredited photographer, who released it under the terms of the [Creative Commons CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
