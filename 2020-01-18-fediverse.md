---
layout: post
title: Free Social Networking Showdown - The Fediverse
date: 2020-01-18 09:01:12-0500
categories: media
tags: [socialmedia, freesoftware, fediverse, gnusocial, mastodon, socialshowdown]
summary: How do the Fediverse social networks stack up?
thumbnail: /blog/assets/iot-technology-concept-city-transport-smart-1575603-pxhere.com.jpg
offset: -25%
---

* Ignore for ToC
{:toc}

There's more detail in [this post]({% post_url 2020-01-04-social-intro %}), but this is one of a series of posts investigating the Free-as-in-Freedom social networks that are available, to see how they compare to the for-profit networks that exploit users.  Each post is an overview of the system I have been and will be working with, along my general impressions.

Feel free to contribute your own findings as I go, either on the same networks or pointers to and descriptions of any networks I may have missed.

![Network](/blog/assets/iot-technology-concept-city-transport-smart-1575603-pxhere.com.jpg "Network")

This week, we have one of the richer ecosystems in the space.  Because of that, please forgive me if I miss some critical feature that one of the newer implementations provides.

## The Fediverse

It's not a term I care for, but this is the common term for the collection of social networking interfaces that interact with either the [OStatus](https://en.wikipedia.org/wiki/OStatus) protocol or its successor, [ActivityPub](https://en.wikipedia.org/wiki/ActivityPub).  It previously included networks such as Status.net, Identi.ca, GNU social, Friendica, and Laconica, but the standardization as ActivityPub has caused a proliferation of other interoperable networks.

{% pull Twitter without the Nazis %}

You might already know this network in the form of Mastodon, PeerTube, or any number of other "faces" to the underlying network and protocol, and that's unfortunately confusing when added to the name changes the rest of the system has had over the years.  In short, Mastodon, PeerTube, and similar systems all run on and show you the ActivityPub network, which (especially as Mastodon) has been described by a a few writers as *Twitter without the Nazis*.

 * Central Website:  Probably one of the following, depending on your preference of social network type.
   - <https://gnu.io/> - Microblogging
   - <https://joinmastodon.org/> - Microblogging
   - <https://pleroma.social/> - Microblogging
   - <https://joinpeertube.org/> - Video publishing
   - <https://pixelfed.org/> - Image publishing
   - <https://writefreely.org/> - Blogging
   - <https://joinmobilizon.org/en/> - Event scheduling
   - <https://nextcloud.com/> - File sharing
 * System Architecture:  Federated
 * Source Code Repository:  <https://git.gnu.io/gnu/gnu-social/issues>, among others
 * License:  GNU Affero General Public License v3
 * My Account:  @jcolag@mastodon.social
 * Font Awesome:  [<i class="fab fa-mastodon"></i>](https://fontawesome.com/icons/mastodon?style=brands) seems to be the only one

### Getting Started

Like with Diaspora, you have the easy way of finding an existing public server ([mastodon.social](https://mastodon.social) is probably the most common, since it's easy to find and remember, though there's some legitimate worry about a "main" instance being run by the lead developer, especially when moderation has been...uneven, one of the driving forces behind the Pleroma project) and register.  And you have the hard way of setting up your own server.

Unlike Diaspora*, when signing up to your own or another instance, there is no on-boarding process of selecting topics or making a first post involved in any of the ActivityPub-based systems I looked at.  So, a new user is basically left on their own.

#### Local Installation

I didn't try to install a Mastodon instance, both because I already use Mastodon and because [the instructions](https://docs.joinmastodon.org/admin/install/) are...a lot.  Instead, I tried Pixelfed and GNU Social.

Pixelfed had some sort of incomprehensible PHP conflicts.  I'm not a PHP person, generally, so I wasn't able (or particularly inclined) to figure out if this was a problem or if my machine or their code is behind on requirements.  That said, [their instructions](https://docs.pixelfed.org/installing-pixelfed/) would be simple enough, assuming that Composer and Artisan were the right versions.

GNU Social's [installation instructions](https://git.gnu.io/gnu/gnu-social/blob/master/INSTALL) are even easier, and installation boils down to "put the code on your website that can run PHP."  That was fine, *but* the configuration page (which is *great* to see, by the way, instead of requiring blindly messing around with files) issued a series of warnings about using deprecated features and then bombed out, apparently trying to execute bad SQL.

In short, these all take some effort, ambition, and technical expertise to get running.  [WriteFreely](https://writefreely.org/start) looks promising on this front, however, but it's less of a social network, from what I understand.

### User Experience

Mastodon is, famously, a lot like Twitter with a larger message length, and many ActivityPub systems tend to be similar in structure and format to commercial sites.  PeerTube looks a lot like YouTube <i class="fab fa-youtube"></i>, for example.  Pixelfed closely resembles Instagram <i class="fab fa-instagram"></i>.  Mobilizon could pass for Meetup <i class="fab fa-meetup"></i>.

{% pull ...they're interoperable, meaning that the platform you choose is irrelevant... %}

However, because all the networks share the same underlying layers, they're interoperable, meaning that the platform you choose is irrelevant; you can still interact with everybody and everything else on the Fediverse.  So, if you subscribe to a PeerTube channel in Mastodon, the videos show up in your feed.  If you then reply to such a video, the reply shows up as a comment in PeerTube.  For example, I do exactly this:  One of the accounts I follow is [@peertube@vidcommons.org](https://vidcommons.org/accounts/peertube), so whenever someone over there posts a public domain or free culture video, it shows up in my Mastodon feed, ready for me to watch.

Speaking of VidCommons, it's pretty easy to embed a video, too...

<iframe width="560" height="315" sandbox="allow-same-origin allow-scripts" src="https://vidcommons.org/videos/embed/c864d88c-f45c-4d6f-9312-e1761bb9596f" frameborder="0" allowfullscreen></iframe>

(PeerTube's videos, incidentally, play through [WebTorrent](https://webtorrent.io/), basically an implementation of BitTorrent that works on a webpage.  In theory, this *could* produce choppy playback and unavailable videos, but I haven't run into either problem, yet.)

{% pull ...each server has a lot of flexibility in design and moderation. %}

Another difference to other networks is that each server has a lot of flexibility in design and moderation.  This leads to the different servers being able to attract and cultivate different niche communities, meaning that you can find servers where people share interests in specific media franchises, hobbies, technologies, aspects of their lives or identities, and so forth.  Picking an account on such a server doesn't limit your conversations to those topics, of course, just that there's a shared interest across the sub-community.

Another (related) feature of possible interest are the Local and Federated Timelines.  The Local Timeline shows every public message posted on the server, hopefully making it easy to find people to talk to and follow.  The Federated Timeline is all public messages the server can see as they see them, similar to Twitter's old "firehose."

{% pull the content warning system %}

And one feature, specifically from Mastodon, to appreciate is the **content warning** system, a way to flag a post so that it appears with *only* a briefer summary until a reader clicks through.  While most obviously applicable to messages that might trigger post-traumatic stress in readers, include "not safe for work" content, or reveal information ("spoilers") that readers might want to remain ignorant of, it also sees wide use as a signal to followers that it's a topic that might not be of interest or could be boring to a significant subset of readers; think political opinions or baby pictures.

### Community

{% pull ...might be limited to open source projects cloning their Twitter feeds out of a resigned sense of obligation... %}

ActivityPub communities can appear to be mostly isolated from each other in a way that can feel more extreme than other networks.  For example, creating an account on a random server with no other connections can produce a strong impression that the entire user base might be limited to open source projects cloning their Twitter feeds out of a resigned sense of obligation plus an assortment of people who have been (rightly) banned from Twitter.

However, it seems that entire communities on Twitter have been transplanting their more social communications over to Mastodon in blocs.  In my specific case, discovering that a couple of other software designers I sort of know had been using Mastodon quickly brought my feed into a state where something other than conference announcements.

### Verdict <i class="far fa-thumbs-up"></i>

{% pull ...a more polite and collaborative culture... %}

Once you find one or more sub-communities or a themed server of interest, the Fediverse seems very close to the ideal of a social network unencumbered by advertising.  As mentioned, you'll often hear Mastodon in particular described as having a more polite and collaborative culture, even among people who have almost exactly the same group of people around them on Twitter.  By their absence, it's a prime example of how advertising revenue and anger go hand-in-hand.

Where that fails, the content warnings go a long way towards defusing major problems.

So, overall?  The Fediverse is one of the winners.

#### <i class="fab fa-mastodon"></i>

* * *

**Credits**: The header image is [Big data connections. IOT](https://pxhere.com/en/photo/1575603) by [asawin](https://pxhere.com/en/photographer/2102671) from [PxHere](https://pxhere.com), made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
