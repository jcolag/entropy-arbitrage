---
layout: post
title: Free Social Networking Showdown - RetroShare
date: 2020-03-14 07:38:25-0400
categories: media
tags: [socialmedia, freesoftware, retroshare, socialshowdown]
summary: How does the RetroShare social network stack up?
thumbnail: /blog/assets/retro_network.png
offset: -23%
---

There's more detail in [this post]({% post_url 2020-01-04-social-intro %}), but this is one of a series of posts investigating the Free-as-in-Freedom social networks that are available, to see how they compare to the for-profit networks that exploit users.  Each post is an overview of the system I have been and will be working with, along my general impressions.

Feel free to contribute your own findings as I go, either on the same networks or pointers to and descriptions of any networks I may have missed.

![A RetroShare Network](/blog/assets/retro_network.png "A RetroShare Network")

Note that I added a specific [socialshowdown tag](/blog/tag/socialmedia/) to easily collect these posts, if you want to easily find the others in the series.

## RetroShare

RetroShare bills itself as "secure communication for everyone," a decentralized system designed to mimic most typical communication services (forum, chat, e-mail, and so forth) with anonymity outside of friend relationships.

 * Central Website:  <https://retroshare.cc/>
 * System Architecture:  Peer-to-Peer
 * Source Code Repository:  <https://github.com/RetroShare/RetroShare>
 * License:  GNU General Public License v2
 * My Account:  `2b7c2ab9ad1cbb4ecee9cb9f35503557`

Note that, despite documentation stating that RetroShare is licensed under the GPLv2, the repository has a `LICENSES` folder including AGPLv3, AGPLv3 or later, Apache 2.0, GPLv3, LGPLv3, MIT, and CC-BY-SA 4.0, with no real indication of what license covers what or why GPLv2 isn't represented at all.

### Getting Started

I wasn't able to get the Ubuntu software repository to work, so downloaded the AppImage file.

Running the program, you're asked to fill in...

 * The type of node (Standard, over [Tor](https://en.wikipedia.org/wiki/Tor_(anonymity_network)), and over Tor and [I2P](https://en.wikipedia.org/wiki/I2P),
 * A user name,
 * A password, and
 * Some randomness by moving your mouse around the window.

There are some advanced options that I didn't bother with (I assume they're for people installing on multiple computers), and running I2P also apparently requires additional configuration.  I went for the most straightforward approach.

It takes a bit to set itself up, and...you're ready to go.  More or less.

### User Experience

There's something very wrong with the styling, in that almost all the input text is the same color as the box its typed into.  Other minor features seem slightly broken, like how I can't open links directly into a browser from the RetroShare window.

Otherwise, you have a few different screens.

 * Home:  The program starts here, but there isn't much to work with, just a certificate to send to your friends and a place to add a friend's certificate.
 * Network:  Here, there are a few visualizations of how you're connected with other users and people.
 * People:  This is basically your standard contact database.
 * Chats:  An instant messaging interface.
 * Mail:  A screen that looks like a typical e-mail client.
 * Files:  Lists of uploads and downloads.
 * Channels:  Even after reading the help screen, I'm admittedly still not sure what this is.  It's described something like a hashtag, but I'm not convinced there's anything like a microblogging interface that would go with it.
 * Forums:  Sort of like the *Mail* screen, this allows access to forums on different nodes.
 * Links:  This screen is another mystery, with buttons to "Subscribe" and "Submit a new Post," but they're disabled with no indication of how they're fed.
 * Log:  Self-explanatory.
 * Preferences:  So many options...

So, there's a lot going on, and odds are that no user will care about the majority of the interface.

### Community

To start with, there is no community.  The entire point is that your network must be deliberately built.  And obviously, if you just do that, your community should be as good as your social circle already is, because those are the people you'll be involved with.

To find other people, you need to...

 * Find a RetroShare Chat Server (i.e., [search](https://duckduckgo.com/?q=retroshare+chat+server))
 * Copy your certificate from the RetroShare window's *Home* screen.
 * Paste your certificate in to register with the server and submit.
 * Copy the server's certificate you get in exchange.
 * Back in RetroShare, click *Add friends certificate*.
 * Click *Paste*.  It automatically pastes the certificate, so you can click *Next*, then *Finish*.
 * Wait for the process to finish.

You're now connected to a server!

In my case, I went to [retroshare.ch](https://retroshare.ch/), because it was the first working server I found.  I now have access to one chat and one forum topic, both dedicated to RetroShare certificate exchanges to find people to interact with.

Right-click to open the forum or chat and, after it loads, you get what looks a lot like threaded e-mail, with replies indented underneath the original message.

Predictably, since this is a forum specifically for certificate exchanges, the overwhelming majority of the messages are people offering up their certificates, with replies being people acknowledging that they did so.  No information on anybody, mind you, just the certificates.  Most of the posts were in English, when I looked, with a couple in what I assume to be Russian but didn't verify by trying to translate.

This is all well and good, but it exposes an obvious problem:  It's a *lot* of work to get to the point where you can get a sense of what's going on and get involved in conversations.

### Verdict <i class="far fa-thumbs-down"></i>

It's probably not a bad system, overall, but it's such a slog to decide if it's worth continuing to use it that the network doesn't feel like it's worth my time to explore further.  Unless, I guess, a bunch of great people read this post and immediately e-mail me their certificates to me.  *Then*, maybe I'll give it another shot.

Otherwise, I predict that---with it's emphasis on censorship-resistance, free speech, anonymity, and privacy---RetroShare is very likely to be popular with terrorists of various ideologies and a handful of people who just use privacy tools on principle.

#### <i class="far fa-handshake"></i>

* * *

**Credits**:  The header image is [retro_network](https://github.com/RetroShare/documentation/blob/master/docs/img/concept/retro_network.png) by [the RetroShare Team](https://github.com/RetroShare) and is made available under the terms of a [Creative Commons Attribution-Share Alike 4.0 International license](https://creativecommons.org/licenses/by-sa/4.0/deed.en).
