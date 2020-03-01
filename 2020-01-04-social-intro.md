---
layout: post
title: Free Social Networking Showdown
date: 2020-01-04 07:01:12-0500
categories: media
tags: [socialmedia, freesoftware, intro, socialshowdown]
summary: How do the various free software social networks stack up?
thumbnail: /blog/assets/Social_graph.gif
---

![Social graph](/blog/assets/Social_graph.gif "Social graph")

As mentioned, [for the new year]({% post_url 2019-12-31-new-year %}) and as fallout from [my discussion]({% post_url 2019-12-20-social-media %}) about corporate-run social media, I have a couple of longer-term projects in mind, including taking a closer look at the Free-as-in-Freedom social networks that are available, to see how they compare to the for-profit networks that exploit users.  At the time I previously wrote, I had already been looking at a couple of them and wanted to pursue the field in a bit more detail.

This series of posts, to be published on Saturday mornings, is an overview of the systems I have been and will be working with, along my general impressions.  Feel free to contribute your own findings as I go, either on the same networks or pointers to and descriptions of any networks I may have missed.

## Disclaimers

Note that I haven't tried hard to find communities on any of the networks.  Instead, I looked at who seems to be represented in either the public "stream" of posts or the list of accounts recommended to me as a new user.  A more ambitious and outgoing user might well have an entirely different experience from me.  I suspect that's not the case, since it would be hard to hide an entire community, but it's possible.

In most cases, I also probably won't be putting much effort (if any) into running my own instance of the network.  I would *like* to be able to say how much administrative work is involved, but don't know that I'll have the time or temperament for many.

## Glossary

For the people not already versed in the relevant concepts, here's a quick summary of what you'll want to know to make sense of the posts that follow:

 * **Protocol**s are the simple languages that systems use to communicate with each other.  For example, the address in your web browser probably starts with [`https`](https://en.wikipedia.org/wiki/HTTPS), standing for "**H**yper**t**ext **T**ransfer **P**rotocol (**S**ecure)."

 * **Centralized** systems run the same way that the more familiar commercial services generally do, with one website or server where you register and connect.  That central service can have any rules the owners please and enforce them however the owners please.  However, if you can connect to the central service, you have access to the entire network.

 * **Federated** systems work like e-mail.  You run a server of your own or sign up with a service, and the location of the server becomes part of your address.  Because each server speaks the same language (protocol), you can send to and receive from any server.  However, you're relying on that server to connect to the rest of the network.

 * **Peer-to-Peer** systems treat each user as a separate service that sends to and receives from other users, directly, rather than mediated by official third parties.  While there's no *direct* reliance on third parties, there are still intermediaries in transfer and potential security concerns with inviting all the required connections onto each user's computer.

 * **Offline** systems generally have no central repositories of content or history, instead expecting each participant to maintain a copy, much like (and often inspired by) [blockchain](https://en.wikipedia.org/wiki/Blockchain) systems.  This allows each user to read and write content without a connection to the network, then update their local content and the network when a connection becomes available, possibly even transmitting through a friend in person.

 * **Markdown** is a simple programming language in the same sense as HTML, a way to "mark up" text to provide it with structure and formatting, like headings.  You can read more about it at [Markdown](https://daringfireball.net/projects/markdown/) from its original pages.  It's the formatting system used for comments on this blog, and used by many Free Software social networks, because it's easy to learn and convert to other formats.

 * **Markup**, from which Markdown gets its name, is a generic idea representing the ability to add style and structure to text.  You have just seen a link to more information on Markdown, but you may also be familiar with [HTML](https://en.wikipedia.org/wiki/HTML) (*H*yper*t*ext *M*arkup *L*anguage) or [LaTeX](https://en.wikipedia.org/wiki/LaTeX).

 * A **Repository** is a place where programmers leave source code in a way that makes it easy to track the entire history of the work.  Since the networks we'll be talking about are all Free Software, it's important to know where to find it.  You should probably be using one for a lot of your own work, actually, but that's another discussion for another day.

## Format

Each post will try to cover similar ground, so that I'm comparing the systems apples-to-apples instead of a more ad hoc approach.  Expect a summary something like...

 * Central Website:  The place to go for information on registering and the network in general.
 * System Architecture:  Generally, one of Centralized/Federated/Distributed/Offline, describing how users interact.
 * Source Code Repository:  The place to go to get the network source, file issues, and contribute changes.
 * License:  The public license under which the server software is available.  To be involved in this Showdown, it *must* be an [OSI-approved license](https://opensource.org/licenses/category), since anything outside them won't be Free Software.
 * John's Account:  The place to connect with me on the network in question.
 * Font Awesome:  Where [<i class="fab fa-font-awesome"></i>](https://fontawesome.com/icons?d=gallery&s=brands&m=free) has a brand icon for the network, I'll list it.

And then longer-form descriptions of how the network pans out.

 * Getting Started:  An overview of how and where to sign up, and what that process looks like.
 * User Experience:  Important elements of the interface, if there are any of note.
 * Community:  An overview of the people I found, there.
 * Verdict:  What I like and dislike about the network, and whether I would recommend it to others.

That should be a reasonable start to conversations on the topic.

## Next

So, with that in mind, we'll get started next Saturday, talking about [Diaspora*](https://diasporafoundation.org/).

#### <i class="far fa-handshake"></i>

* * *

Credits: The header image is an animation of a social graph coming together, made available under a [Creative Commons Attribution, Share Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license by [Festys](https://ru.wikipedia.org/wiki/%D0%A3%D1%87%D0%B0%D1%81%D1%82%D0%BD%D0%B8%D0%BA:Festys).
