---
layout: post
title: Free Social Networking Showdown - Scuttlebutt
date: 2020-01-25 08:47:12-0500
categories: media
tags: [socialmedia, freesoftware, scuttlebutt]
summary: How does the Scuttlebutt social network stack up?
thumbnail: /blog/assets/hand-photography-animal-cute-leg-finger-960645-pxhere.com.jpg
offset: -16%
---

There's more detail in [this post]({% post_url 2020-01-04-social-intro %}), but this is one of a series of posts investigating the Free-as-in-Freedom social networks that are available, to see how they compare to the for-profit networks that exploit users.  Each post is an overview of the system I have been and will be working with, along my general impressions.

Feel free to contribute your own findings as I go, either on the same networks or pointers to and descriptions of any networks I may have missed.

![Hermit Crab](/blog/assets/hand-photography-animal-cute-leg-finger-960645-pxhere.com.jpg "Hermit Crab")

This time through, we have an entire social network designed to work without much of a data network.

## Scuttlebutt

 > > ...complete decentralization...

The Scuttlebutt network (also *Secure Scuttlebutt* or *SSB*) stands out from many other systems by its complete decentralization.  Rather than sign up for an account on a server, you run an application on your local computer that communicates directly with the people you follow to get the latest information.  Likewise, the people who follow you get all of the updates you know about.  This makes it possible (even if not particularly convenient) to communicate around the world even without a global network, making the network useful even to people who are offline for extended periods of time.

 * Central Website:  <https://www.scuttlebutt.nz/>
 * System Architecture:  Peer-to-Peer and Offline
 * Source Code Repository:  <https://github.com/ssbc/patchwork>, among others
 * License:  GNU Affero General Public License v3
 * My Account:  @RoHPOaN65z8ZVYwPr19Ni4KgYCE05k+FAKMdDPyHbvs=.ed25519

### Getting Started

In the simplest case, you can install [Patchwork](https://ahdinosaur.github.io/patchwork-downloader/), start the program, and be on your way.  But that's also an uphill route to using the network, since your posts remain contained on your hard drive until you can find a friend to invite to follow you.

 > > ...the pub, a (non-human) user on the network whose sole job it is to follow people who follow it.

So, the reality of getting the ball rolling is the *pub*, a (non-human) user on the network whose sole job it is to follow people who follow it.  This makes it easy to connect large groups of people from around the world without much effort.  See [this list](https://github.com/ssbc/scuttlebot/wiki/Pub-Servers) for known pubs and hope that the list is maintained regularly enough to find a couple that work.

Once you've subscribed to a couple of pubs (and seen them subscribe back), like Diaspora, you can quickly follow a handful of topics/hashtags and get a sense of who you'll find interesting enough to follow and/or interact with.  Since the Scuttlebutt community is still small, it's also probably worthwhile for a lot of new users to write an introductory post including the `#new-people` hashtag.  People in the know can then provide some further guidance or at least some words of encouragement.

Oh, and ask around for the current best practices for backups at that time.  Your identity is a private key, and if you lose that, you no longer have access to the network under your existing identity.

### User Experience

Patchwork's experience is...straightforward and unexciting, really, which isn't a bad thing.  You have your stream of updates, a list of the topics you follow, a place to write, and so forth.  About the only feature of note (because it's mildly unpleasant) is that the update feed is thread-based and reverse-chronological, with no highlighting as to what posts are new.

Posts, as with Diaspora, are written in Markdown.  Unlike Diaspora, Patchwork is going to make you learn to write your own Markdown.

Other Scuttlebutt applications, however, have wildly divergent experiences.  Some use the network to play games.  Some integrate third-party functionality to create a fully distributed and open counterpart to [GitHub](https://www.github.com), [ssb-server](https://github.com/ssbc/ssb-server/).

 > > ...every action is indelible.

One thing to keep in mind is that every action is indelible.  Every post (including every typo), every like, every follow, every unfollow, every unlike, and so forth, it's all activity that you're publishing to your network.  The most obvious effect is that you can't go back and edit mistakes in old posts, but it also means that your interests could be tracked and monitored without your knowledge, by anybody willing to connect to the network.

![Hermies](/blog/assets/hermies.png "Hermies")

The indelible actions, however, mean that Scuttlebutt continues to work (in a limited way) even if you're not connected to a network.  You can still read through all the historical posts and publish posts and replies.  Your contributions won't be distributed to anybody until you can connect to someone, but you can still interact in preparation for the next time when connectivity is available.

There are three significant flaws I see in the system. 

 * First, unavoidable and arguably a feature, you basically can't talk to a person unless there's a chain of intermediate users or hubs relaying the messages; without that connection, they don't even know you exist.
 * Second, the only moderation comes from ignoring people, meaning that you see everything the people you follow interact with, even the parts that don't interest you at all.
 * Finally, you have your entire network stored on your computer.  The longer you use Scuttlebutt and the more people start using it, the more space it's going to take on your hard drive.  Likewise, if you lose access without a backup, consider your account lost.

Those aren't *terrible*, of course, but they're worth pointing out, because they're very different than the potential issues with other networks.

### Community

 > > Scuttlebutt's community is very active and friendlier than many of the others.

While small, Scuttlebutt's community is *very* active and friendlier than many of the others.  Not surprisingly, lot of the talk is about Scuttlebutt itself; combined with the lack of filters mentioned before, this means that you'll read a *lot* of posts about possible tweaks to the protocol.

While I do see a lot of people who call themselves libertarians (which can often be something of a red flag, in my experience), most of them seem to be less right-wing/pro-corporate ideologues than "we need to empower the disadvantaged" liberal and aren't convinced that governments (or corporations) can handle all of it.

One problem I have noticed is an aversion to any actual community moderation.  As mentioned, the only recourse a user has to stop a problematic actor is to have the software ignore that actor, and there doesn't appear to be any interest in changing that.  This means that, potentially, an influx of bad users creates a terrible experience for later newcomers while the older parts of the community---the people who might have actual clout---are blissfully unaware of the problem.

 > > ...would fracture the community...

Compounding that, a solution to bad actors that I've seen recommended and that some people already use is to disconnect their accounts from the pubs.  If embraced widely, this would fracture the community such that it would be almost impossible to interact with someone who has been using Scuttlebutt for more than a few months.  You would end up with the experience of seasoned users who choose to only interact with each other and the entirely separate experience of everybody else, which isn't a great look.

### Verdict

 > > ...my favorite of the networks.

Despite my misgivings above, I *think* this might be my favorite of the networks.  As mentioned, the people are generally nice and interested in fostering conversation and learning about the world.  The software is also surprisingly appealing.

Admittedly, I dropped off the network for months for lack of time, but I did miss it.  I don't recommend doing this if you can avoid it, though, because it took *forever* to update the database.

#### <i class="far fa-handshake"></i>

* * *

**Credits**: The header image is [Hermit Crab](https://pxhere.com/en/photo/960645) by an unknown photographer from [PxHere](https://pxhere.com), made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).  [Hermies](https://en.wikipedia.org/wiki/Secure_Scuttlebutt#/media/File:Hermies.png), the Secure Scuttlebutt mascot, by [Paul Frazee](https://pfrazee.hashbase.io/), is available under a [Creative Commons Attribution-Share Alike 4.0 International license](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
