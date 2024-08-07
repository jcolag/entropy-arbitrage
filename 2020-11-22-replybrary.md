---
layout: post
title: Replybrary
date: 2020-11-22 09:56:12-0400
categories:
tags: [announcement, twitter]
summary: A Twitter-bot that tries to be useful
thumbnail: /blog/assets/4189390241_d6fef03f49_k.png
offset: -18%
---

* Ignore for ToC
{:toc}

Today---probably right as this post is released, but maybe plus or minus an hour or so, plus testing---marks the launch of [**Replybrary**](https://twitter.com/replybrary), a Twitter-bot that tries to provide useful links in political discussions on request.

![It's a robot!](/blog/assets/4189390241_d6fef03f49_k.png "It's a robot!")

(Note:  The problem with getting this running---besides my own stupidity of allowing typos into the JSON and script---was convincing Node.js to update to a usable version.  Somehow, that's a nightmare on my server, even though I obviously did it on my home machine...)

To use it, send `@replybrary` a message with keywords, such as:

 > `@replybrary Columbus`

At this time, since I only have one relevant link in the library, it'll reply to you---as part of a thread---informing you that, for your keywords, it found <https://www.thenation.com/article/archive/the-invention-of-christopher-columbus-american-hero>.

It will parrot back your keywords, if they fit, in case you would like to then delete your original message.  The purpose is that *you* are not the one providing the article and taking heat from it.  You're asking a bot to do it, and the bot is just going to reply to harassment with apologies that it can't find any useful information on the obnoxious message.

However, if the keywords don't fit, **Replybrary** will drop them as it starts chopping URLs off the list to make room.  So, try to be mindful of that and limit the length of your requests by using as few keywords as you can get away with; the bot isn't smart enough to narrow down the search, since you could be asking about multiple things.

## The URLs

Because the world tends to want to be a more egalitarian place, you'll find that most of **Replybrary**'s responses indicate that things like democracy, gender equality, and racial equality work better than their opposites or that show evidence of inequality being both deliberate and systemic.

I had some links in mind already, but I've added a hundred or so recurring links that I used to refer to when I was [regularly posting on Quora]({% post_url 2020-01-12-quora %}) and I'll eventually try to corral a decent number of the links posted in my [weekly Twitter roundup](/blog/tag/linkdump) posts.

In other words, it's not going to feed or (at this time) debunk your favorite conspiracy theory.  If you want a bot to do that, you can deploy your own instance of [**library-twitterbot**](https://github.com/jcolag/library-twtterbot) with its own set of URLs.  I have a rundown on [how to do set this up]({% post_url 2020-10-28-twitter %}) that I wrote last month.

You can see a full list of the current set of keywords and the associated links for each [here](https://john.colagioia.net/replybrary.html).

## Contributing

I already mentioned [the GitHub repository](https://github.com/jcolag/library-twtterbot) for the code, if you see anything it should do differently.  If you have recommendations for new or better URLs, [that repository](https://gitlab.com/jcolag/replybrary-urls) is on GitLab, instead, to keep them separate.

I have some standards for what URLs I'm willing to add to the bot's library, but if you have something, send it along, especially since many of the links I have on hand are older.  In an ideal world, you'd be able to send new articles directly to the bot for review, but I haven't figured out a good way to handle that, yet.

* * *

**Credits**:  The header image is [Gabriel in robot costume](https://www.flickr.com/photos/21550937@N03/4189390241) by [Roy Luck](https://www.flickr.com/photos/royluck/), released under the terms of the Creative Commons [Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
