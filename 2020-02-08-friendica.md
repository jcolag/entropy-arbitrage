---
layout: post
title: Free Social Networking Showdown - Friendica
date: 2020-02-08 08:07:12-0500
categories: media
tags: [socialmedia, freesoftware, friendica, socialshowdown]
summary: How does the Friendica social network stack up?
thumbnail: /blog/assets/sunrise-trees-fog-canon-XC10-nature-tree-1446447-pxhere.com.jpg
offset: -50%
---

There's more detail in [this post]({% post_url 2020-01-04-social-intro %}), but this is one of a series of posts investigating the Free-as-in-Freedom social networks that are available, to see how they compare to the for-profit networks that exploit users.  Each post is an overview of the system I have been and will be working with, along my general impressions.

Feel free to contribute your own findings as I go, either on the same networks or pointers to and descriptions of any networks I may have missed.

![Mist in a park](/blog/assets/sunrise-trees-fog-canon-XC10-nature-tree-1446447-pxhere.com.jpg "Mist in a park")

Note that I've added a specific [socialshowdown tag](/blog/tag/socialmedia/) to easily collect these posts, if you want to easily find the others in the series.

## Friendica (prev. Friendika, Mistpark)

After a non-trivial amount of research, I'm still not _quite_ sure what the overall deal is, here.  On one level, the network seems to be a lot like the [Fediverse]({% post_url 2020-01-18-fediverse %}) applications and doesn't seem to really try to distinguish itself, to the point that I'm not _entirely_ sure that they're separate networks.

{% pull ...the ability to interconnect with other networks. %}

This is confused further by Friendica's apparent big feature, which is the ability to interconnect with _other_ networks.  That is, you can host a server that allows you to add outside blogs, Diaspora streams, Fediverse feeds, bug trackers, and others into your "newsfeed;" servers can also allow posting to Twitter, WordPress blogs, and others.

 * Central Website:  <https://friendi.ca/>
 * System Architecture:  Federated
 * Source Code Repository:  <https://github.com/friendica/>
 * License:  GNU Affero General Public License v3
 * My Account:  jcolag@libranet.de, <https://libranet.de/profile/jcolag>

### Getting Started

Like the other federated systems, you need to select a server, though I don't know if there's any difference between servers as you see with GNU social.  Sign up and wait for the e-mail that assigns your password.

Which is to say, we're already not off to a good start.  E-mailing a password is the first lesson in bad security.  But OK, sure, continue...

If you want to install your own, the [instructions](https://github.com/friendica/friendica/blob/develop/doc/Install.md) aren't exactly front-and-center, nor are they particularly clear.  I didn't even try.

### User Experience

{% pull ...a mostly-blank screen... %}

The page you're first confronted with is uploading a profile picture (and the default cartoon house cat), which seems like an odd choice.  Skipping the upload takes you to a mostly-blank screen with a _sidebar_ including a link for [Tips for New Members](https://libranet.de/newmember), which is _sort of_ a DIY on-boarding.

Like the original experience with the site, it prioritizes setting up your profile over finding things to read.  But at least it _does_ point out that you should change your bad password in that section.

{% pull ...a seemingly-easy way to relocate between servers and the ability to create multiple profiles on the same account... %}

While changing the password, the settings indicate that this might be a Facebook-like experience, with a "wall" for friends to post on.  There is also a seemingly-easy way to relocate between servers and the ability to create multiple profiles on the same account, which might be very useful to certain people.

Once I found a couple of people to follow, it seems that there are two oddities:

 * Like Facebook, the network prioritizes "friend requests," mutual relationships.  Given that this is such a sparse group, that seems overly-familiar for strangers.
 * If you find a way to follow someone (I bypassed the interface and pasted `https://libranet.de/follow/?url=` in front of the user's profile URL in the address bar), it still requires that the user approve your request, which is...odd.

Otherwise, things seem to be more or less what you'd expect, particularly if you're expecting Facebook's user interface.

### Community

It took a while to find the global "community stream."  Interestingly, most of the posts are from other networks (Diaspora* and Mastodon), so that's not very enlightening regarding the Friendica community's character.  But I _did_ see a couple of posts that I appreciated, at least.  Plus random porn, for...no particularly obvious reason.  I'm not judging, it just seemed out of place.

{% pull ...may just not be much community there... %}

The local community seems fine.  I don't see much of note, either way.  A fair amount is in languages I don't read and there are a lot of basic posts of links (from non-crazy sites, I should point out after the [Minds]({% post_url 2020-02-01-minds %}) fiasco) without context.  There are also a *lot* of images that are all supposed to be the funniest thing ever, but...aren't; I guess they're probably funnier if it's your first day on the Internet.  So, there may just not be much community there, without the outside networks.

### Verdict

I don't know, honestly.  It's not terrible, but I honestly don't see any reason to spend time there over any of the other options.  The idea of aggregating other networks, however, might be useful or interesting to certain kinds of users.

* * *

**Credits**:  The header image is [sunlight beams through trees at sunrise in a foggy park](https://pxhere.com/en/photo/1446447) by [Rob Smith](https://pxhere.com/en/photographer/1206799), made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).  It was chosen in reference to Friendica's prior name, *Mistpark*, since no relevant free-licensed images are available.
