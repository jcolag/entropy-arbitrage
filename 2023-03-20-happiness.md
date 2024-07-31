---
layout: post
title: Developer Diary, International Day of Happiness
date: 2023-03-20 06:32:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Mario-Canete-Farias-in-2007.png
teaser: This week's updates include new project Socialite and the blog's code.
proofed: true
offset: -29%
---

* Ignore for ToC
{:toc}

Today marks the [International Day of Happiness](https://en.wikipedia.org/wiki/International_Day_of_Happiness), a United Nations project to "make people around the world realize the importance of happiness within their lives."  It also includes a campaign to make people happier, through exactly the sorts of changes that you might expect, like reducing poverty and inequality, protecting the environment, and so forth.

![A smiling 95-year-old man from Pichilemu, Chile](/blog/assets/Mario-Canete-Farias-in-2007.png "I think that I might like the flannel/sweater/sport-coat combination...")

I don't know if talking about code actually makes me happy, or only lets me vent my frustrations, and I'd rather not introspect on that point...

## Socialite

{% github jcolag/socialite %}

Because I have a variety of small social media projects that come and go as I investigate them, I decided to create a repository for this sort of transient work, something between a dump site and an incubator.  Because I expect to jump around to different things and keep most scripts relatively superficial for now, I call it **Socialite**.

So far, you'll find:

My un-shortening script---[`unshort.rb`](https://github.com/jcolag/socialite/blob/main/unshort.rb)---which finds shortened URLs (based on an accompanying list of shortening sites) in a file and recursively replaces them in-place, until it finds the original.  I used this to prevent [my Twitter archive](https://jcolag.github.io/twitter/) from redirecting everything *back* to Twitter.

A prototype script---[`post.js`](https://github.com/jcolag/socialite/blob/main/post.js), which I'll rename soon---to post a message to [Cohost](https://cohost.org/jcolag/).

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Somehow, I never committed it to the repository, but at least for Friday posts, I've started working on a process to blur out any images that people might consider sensitive, specifically those that I've marked as "sensitive" on social media.  I noticed that I hadn't published any of those changes, so started doing so.

If you review the JavaScript and CSS on the blog, you can see where this will end up.  While the images that go up on social media don't always show up on the blog---because they don't have a compatible license, since so many organizations have inexplicably gotten themselves subscriptions to Getty Images, even when they publish under Free Culture or similar licenses---some will.  And of those, a subset will have an upsetting quality to them, at least for many readers.

For example, social media has an extensive trope of images that I call "revile at the ugly authoritarian."  These sorts of pictures tend to turn my stomach.  Not only do I not need these creeps mugging in my face, and not only do they circulate to provoke an emotional reaction for the sake of "engagement," but they strongly evoke the racist and sexist ways that media has tried to "other" and maintain hatred of women and disadvantaged groups.  I can think of other categories of images, but while I consider them a part of the articles that I post, I don't want them centered on my blog.

As a result, I want the images to act similar to how they do on social media, mostly blurred, until the reader interacts with the image.  For now, I only have the code committed to toggle the new (but not committed) `sensitive` CSS class.

```javascript
window.addEventListener('load', (e) => {
  Array.from(document.getElementsByClassName('sensitive')).forEach((i) => {
    i.addEventListener('click', handleImageClick);
  });
});
function handleImageClick(e) {
  const cs = e.target.classList;
  if (cs.contains('sensitive')) {
    cs.remove('sensitive');
  } else {
    cs.add('sensitive');
  }
}
```

For all the images marked sensitive (with the CSS class), add or remove the class on a click event.

## Next

This week, I need to finish committing the sensitive-image code, getting the CSS into place.  While there, I also have an update to the [Prism](https://prismjs.com/) code that handles syntax highlighting of the code that I post.  I realize that it needed a refresh anyway, and while I had the page open, I added more programming languages to highlight, since my code snippets don't always show up well.

In addition, I'll probably keep working on **Socialite**.

Oh, and I *might* start working on a Mastodon front-end.  As I follow more people, it takes me more time to "quickly check updates" there.  A lot of that time, I spend seeing the *same* messages that (frankly) I didn't care about the first time, or someone amplifying every single message of a thread, which I end up having to read in reverse order.

In any case, now that I have a general sense of how the Mastodon API works, it seems reasonable to put together a custom client that acts the way that I actually want it to work.

* * *

**Credits**:  The header image is [Mario Cañete Farías in 2007](https://commons.wikimedia.org/wiki/File:My_Grandfather_Photo_from_January_17.JPG) by [Diego Grez Cañete](https://www.wikidata.org/wiki/Q15304738), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
