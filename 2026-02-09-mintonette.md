---
layout: post
title: Developer Diary, Mintonette
date: 2026-02-09 07:56:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, social-media]
summary: Progress on assorted projects
thumbnail: /blog/assets/monks-volleyball-Sikkim-India.png
description: This week's projects include a quick social media update and more blog post labeling.
spell: mintonette Dukkha samudaya moHqTN Sukanto Debnath
proofed: true
---

* Ignore for ToC
{:toc}

A hundred thirty-one years ago today, at least so the story goes, YMCA physical education director William G. Morgan created the popular sport mintonette, adapting badminton for a larger group, as a lower-intensity workout than the still-new basketball.  You've never heard of it?  Ah, right.  Because the name makes no sense whatsoever, people quickly renamed it [volleyball](https://en.wikipedia.org/wiki/Volleyball).

![Buddhist monks playing volleyball](/blog/assets/monks-volleyball-Sikkim-India.png "Dukkha, samudaya, spike!")

And with that, on to the week's projects.

## Social Media

Admittedly, if people *need* to interact with me through a chat interface, I have two points to mention.

- I won't get to you any faster than any other channel.  No application gets to control my life.  The formats only really change the expectation of how the conversation will progress.
- If the previous item doesn't dissuade you from setting up chat, I mostly recommend [Matrix](https://matrix.to/#/@jcolag:matrix.org) or [Signal](https://signal.me/#eu/6x4C_EgG-Kc44nOQp2bou8C4aIIOKBDT3mfaR42f8xRGP28wHThBq5M4rQmRxvGV), at least at the moment.

That said, [Signal Contingency Plan's zine](https://archive.org/details/signal-contingency-zine/signal-contingency-zine/) convinced me that, yeah, Signal's centralization does make it a target for authoritarian government officials---like the sort who arrest journalists and direct law enforcement to shoot protesters, hypothetically...---using their control (via corporate lackeys) of infrastructure to block it.  And it always makes sense to have possible substitutes.

Also, they reminded me that [Delta Chat](https://delta.chat/en/) exists.  A couple of years ago, I created a "profile" back when the system piggybacked on an existing e-mail account[^moHqTN], but didn't like the Electron app churning away on messaging, and so abandoned it after a couple of tests.  At this point, I couldn't even guess how to get back into that account, not that it had anything in it.

[^moHqTN]:  Delta Chat uses SMTP (e-mail) as its protocol, with every part of an interaction looking exactly like an e-mail, though with encrypted nonsense as the message body.  As such, I have a folder on a disused Yahoo! Mail account that contains a bunch of PGP-encrypted messages to and from Delta Chat bots of the day.  It would appear that it no longer uses a person's e-mail account, at least by default, but using SMTP still makes it difficult to block the entire network, and moving to a different server still takes much less effort than finding and moving everybody who you know over to (for example) a new Signal server.

All that to say that you can now [find me on Delta Chat](https://i.delta.chat/#72934D5E850D1586B958DB9D6E69B79C7F175C3C&i=-W2WnyhD569T2ac3I0Tzki1l&s=TsCyTf663YDqc7yK59we0gr3&a=hgg6sm7oi%40nine.testrun.org&n=John+Colagioia), if you like that sort of thing.

Yes, I did this mostly to draw *your* attention to a (mostly) secure messaging system, not because I expect anybody to reach out[^1MvcLN].  In fact, if you plan on using it for (ahem) certain kinds of activities, you might want to note that Signal and Delta Chat have different vulnerabilities.  For Signal, you would mostly worry most that somebody will put pressure on Signal's service providers---their hosting, their name servers, and so forth---to prevent people from using it, cutting off secure communication.  For Delta Chat, by contrast, you would mostly worry about an adversary gaining access to the server contents; while they would only get the *messages* in an encrypted form, they would also get clean metadata, revealing when individuals contacted each other, which could reveal organizers of an event or similar information.  That doesn't make either bad, but means that you take different kinds of care on different platforms.

[^1MvcLN]:  As far as I know, the number of people trying to contact me on chat platforms because I linked to my account here comes *pretty* close to zero...

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-posts %}

As you might have guessed, most of the week went to labeling [Free Culture Book Club](/blog/tag/book-club) posts.  You can now find projects back to April 2021 by license, medium, genre when I could identify something consistent, and language where not English.  You'll also stumble across labels for [adaptations](/blog/tag/adaptation) of some earlier piece, [classic](/blog/tag/classic) for those rare pre-public-license works where the creator actively released them more recently under a Free Culture (or similar) license, works that have [non-Free elements](/blog/tag/elements-with-copyright)[^r1gDTK], works where we have [lost some material](/blog/tag/incomplete-archive) to bit-rot, and works where the creator mentions [using AI tools for some portion of the work](/blog/tag/llm-used), usually something that they only mention at the end, after I spend hours wondering why certain aspects feel so lifeless...

[^r1gDTK]:  We have a bit of a misnomer, here, because it also includes items where the "official" release carries a non-commercial license except that the components have a Free Culture release, or similar.  But I didn't think of that when I identified the first instance.

This, I think, also finally gives a fairly good sense of what the [tag search page](/blog/tag-search) does, since these labels mean that you can now find all projects licensed under CC BY-SA, for example, then reduce that list to the short stories (with that license), and then narrow it down further by picking a genre.  Or you can find the projects released as both comic and prose, by combining those labels.  In the (far) future, when it becomes a more consistent struggle to find works by new creators, and so I'll need to circle back to people who we've already seen, the posts will probably also need labels by creator.  I don't see much value in that *today*, though, since interested people can search for the name, and dozens of tags that point to one project makes the tag page less useful.

## Next

As you have probably already guessed, this week, I'll continue labeling posts, at least until I make it through the Book Club in a couple of days.  After that, I'll probably start on the Sunday posts.  That'll probably happen on a less-regular schedule, though, because only partially tagging developer diary posts where I worked on a specific project (or Book Club posts of a certain medium) makes those tags/labels "broken," but nobody will probably mind if I don't catch every post that refers to personal pronouns or the Enlightenment.  And I should really get back to the usual sorts of projects.

* * *

**Credits**:  The header image is [Buddhist monks play en:volleyball in Sikkim, India](https://www.flickr.com/photos/sukanto_debnath/557599560) by [Sukanto Debnath](https://www.flickr.com/photos/sukanto_debnath/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license.
