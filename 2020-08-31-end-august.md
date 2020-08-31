---
layout: post
title: Developer Journal, September Eve
date: 2020-08-31 06:50:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Les_Très_Riches_Heures_du_duc_de_Berry_septembre.png
---

Yep.  No holidays.  No birthdays that caught my interest.  It's just the last day of August, meaning we're entering the season of decent holidays.  OK, that's actually not true.  There are quite a few regional and diaspora-based holidays.  It's also [Alma Mahler](https://en.wikipedia.org/wiki/Alma_Mahler)'s 141<sup>st</sup> birthday, which is fun, but licensing would forbid me from embedding Tom Lehrer's [song about her <i class="fab fa-youtube"></i>](https://www.youtube.com/watch?v=QL6KgbrGSKQ), so that's not particularly useful.

[Les Très Riches Heures du duc de Berry septembre](/blog/assets/Les_Très_Riches_Heures_du_duc_de_Berry_septembre.png "Les Très Riches Heures du duc de Berry septembre")

But tomorrow?  Tomorrow is [Emma Nutt Day](https://en.wikipedia.org/wiki/Emma_Nutt), celebrating the world's first female telephone operator.  Things look up quickly for September, in other words.  OK, sure, I could've gone with "Emma Nut Eve" like I've done for other holidays, but that sounds silly and I *really* liked that header image.

In any case, just a short update.

## Uxuyu

As I suggested [last week]({% post_url 2020-08-24-music %}) and probably in weeks before, this week has gone almost entirely to setting up [**Uxuyu**](https://github.com/jcolag/Uxuyu) to store twtxt messages as they're received.  It's not complete, but I've laid the groundwork, so it should be easy from here.  Some of it involved refactoring so that I could reuse existing code, but mostly it was just making space in what's now a general database thread and getting the information there.

And...that's it.

## Next

Now that I have gotten the foundation for the feature settled, the big job is going to be implementing and testing the code to store the messages.

After that, assuming another project doesn't come up, I need to adjust the mentions to look for the user's URL and maybe think about implementing the avatars.  I don't expect that either would be difficult, but just needs me (or someone else, if you're volunteering...) to pay attention.

* * *

**Credits**:  The header images is [Les Très Riches Heures du duc de Berry septembre](https://commons.wikimedia.org/wiki/File:Les_Tr%C3%A8s_Riches_Heures_du_duc_de_Berry_septembre.jpg) by the Limbourg brothers and others, long in the public domain.
