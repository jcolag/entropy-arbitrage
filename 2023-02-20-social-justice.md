---
layout: post
title: Developer Diary, World Day of Social Justice
date: 2023-02-20 06:40:05-0500
categories:
tags: [programming, project, devjournal]
labels: [blog, javascript, twitter-archive]
summary: Progress on assorted projects
thumbnail: /blog/assets/27758131387_302d739453_o.png
offset: -15%
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate the [World Day of Social Justice](https://en.wikipedia.org/wiki/World_Day_of_Social_Justice), recognizing the need to promote the same.

Alternatively, if you'd like something a bit less vague, we in the United States also celebrate today as [Presidents' Day](https://en.wikipedia.org/wiki/Presidents%27_Day), honoring those who have served as President...some celebrated more reluctantly than others.

![Eleanor Roosevelt reading the Universal Declaration of Human Rights](/blog/assets/27758131387_302d739453_o.png "I should send all my correspondence on paper like that...")

Before you click over to take advantage of deep discounts on furniture and mattresses, let's talk programming...

## Twitter Archive

{% github jcolag/twitter %}

I added a public license, Creative Commons Attribution Share-Alike 4.0 International, exactly like this blog.  With the usual caveat that anything that I might have discussed or quoted that doesn't come from a public domain or Free Culture source needs to hide under the Fair Use doctrine's umbrella---particularly the images---if anybody finds me saying something particularly clever, then they can feel free to build on that.

I also modified the archive's stylesheet, to include a rudimentary dark mode.  I doubt that anybody will care about that but me, but it makes me more comfortable.  As you might guess, especially at this time of year, I do a lot of my tinkering in the non-daylight hours, and as I've described before, I have scripts to [turn on dark mode at sundown]({% post_url 2022-11-09-night %}).  As a result, checking an old tweet on a bright white screen feels fairly jarring.

I'll think about submitting it as a pull request, at some point.

Oh, one issue to worry about, in publishing this to GitHub Pages, and I resolved the issue during the week via an issue on the project:  [Search Doesn't (Always?) Appear on GitHub Pages](https://github.com/tweetback/tweetback/issues/70).  We found two problems.

 * First, GitHub Pages won't deploy any folder whose name starts with an underscore character, so `_pagefind` breaks the search itself.
 * Then, the search results didn't seem prepared for a path prefix, so the result results didn't link anywhere.

The first problem had a straightforward configuration solution.  I needed to add to the line invoking `npx` as follows.

```javascript
execSync(`npx pagefind --source _site --glob \"[0-9]*/**/*.html\" --bundle-dir pagefind`, { encoding: 'utf-8' });
```

Of that, the `--bundle-dir pagefind` differs, to redirect it away from the folder with the underscore.

The latter problem required providing a `processResult` function on the index page.  Because it runs repeatedly, it prepends the path's prefix (`/twitter`, for my archive) if it can't already find it in the URL.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage %}

I have gone through my old posts and, for any links pointing to my tweets, they now point to [my Twitter archive](https://jcolag.github.io/twitter/).  Interestingly, I only found *two* tweets referenced outside a [social media roundup post](/blog/tag/linkdump).  After all, now that my archive exists---and especially since I don't want to push people towards Twitter---it no longer makes much sense for my blog to point at Twitter.

For anybody who might need to do something similar, I ran this command against the post source files.  I should note that this updates the modification time of every file, so depending on your needs, you might want to handle this differently, like using `xargs` to send search results to the `sed` replacement.

```console
sed -i 's/twitter.com\/jcolag\/status/jcolag.github.io\/twitter/g' _posts/*.md
```

This does not change the links to anybody else's tweets, and I probably won't bother trying to do that.  I reference---by tweet or by profile---roughly twenty Twitter accounts.  None of those users have registered archives, and several of them belong to a certain political party that spent a day [thanking their deity of choice for Twitter's CEO](https://www.dailykos.com/stories/2023/2/10/2152274/-Elon-Musk-is-spoon-feeding-Republicans-a-conspiracy-and-they-re-dutifully-spewing-it-out-in-Congress), suggesting that they *probably* won't leave in the near future...

Regardless, I then went through some posts manually, updating anywhere that I might have suggested that people follow me on Twitter, since anybody doing so will find themselves highly disappointed.

## Entropy Arbitrage, Part 2

{% github jcolag/entropy-arbitrage-code %}

I updated the script that generates the aforementioned social media roundup posts on Fridays.  It now has a couple of additional snarky `title` attributes for the Medieval calendar diagram.  The tags for content warnings and embedded images now get generated automatically.  And it now provides a brief "follow me" section at the end.

That last item probably has the most interesting story of the three.  When I started publishing the Friday posts, I included a similar suggestion at the end of the posts, finding them during the manual step that I described in the previous section.  After a few weeks, that section vanished, probably because it never really felt right for me to drive business to Twitter.

By contrast, it fits squarely within the mission of the blog to send people to Mastodon.

Oh, and while I had things to do in the blog code, you might notice slightly darker text in posts.  Most people probably won't notice the difference, but it improves the contrast significantly.

## Next

Because blog and Twitter things derailed me, I didn't have time to work on the [**Mastodon Tool Trunk**](https://github.com/jcolag/tool-trunk), so I'll want to get back to that.

I also have some changes to make on my Twitter archive.

* * *

**Credits**:  The header image is [64-165](https://www.flickr.com/photos/fdrlibrary/27758131387/) by the [FDR Presidential Library & Museum](https://www.flickr.com/photos/fdrlibrary/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
