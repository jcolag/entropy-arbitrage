---
layout: post
title: Developer Diary, World Refrigeration Day
date: 2023-06-26 07:14:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Baron-Kelvin.png
teaser: This week's projects include my Mastodon Tool Trunk, my newsletter for June, and social media changes.
proofed: true
---

Today celebrates [World Refrigeration Day](https://en.wikipedia.org/wiki/World_Refrigeration_Day), which...OK, look, *technically* this violates my internal and informal rules, because it amounts to a commercial for an industry, in this case established by the World Refrigeration Day Secretariat in Derbyshire, England.  However, they think too small.  Refrigeration changed the world, from allowing us to buy food out of season, in various forms, to reducing food waste, to enabling organ transplants, to allowing the distribution of some medication and vaccines, to helping us endure heat waves, and more, and at least they used [Lord Kelvin](https://en.wikipedia.org/wiki/William_Thomson,_1st_Baron_Kelvin)'s birthday as the date.  Therefore, I say that we appropriate the holiday for our own purposes...

If you don't love that, though, we also have the [International Day Against Drug Abuse and Illicit Trafficking](https://en.wikipedia.org/wiki/International_Day_Against_Drug_Abuse_and_Illicit_Trafficking) and the [International Day in Support of Victims of Torture](International Day in Support of Victims of Torture).  The former inspires...let's call them "mixed feelings," given the directions that the [War on Drugs](https://en.wikipedia.org/wiki/War_on_drugs) has taken.  And the latter?  Sure, we both support torture victims, but you didn't really want to start your week looking at pictures of that violence, did you...?

![William Thomson, 1st Baron Kelvin, writing](/blog/assets/Baron-Kelvin.png "Thank goodness he didn't go into interior design.")

I don't know.  On to the projects, I guess.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the first.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), though I don't quite trust the company, you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee (the link in the previous paragraph, the *Follow* button to the upper-right of the page), you'll get it on Tuesday morning, the fourth of July---happy {% emoji fireworks %} [birthday to the United States](https://en.wikipedia.org/wiki/Independence_Day_%28United_States%29), a week or so early---because I never publish blog posts on Tuesdays, making that a nicer match than Saturdays.

What will you find inside?  For June, I wrote a piece on the feeling of "cramming for television," a preview of an upcoming project, media consumption skewed toward honoring [LGBT Pride Month](https://en.wikipedia.org/wiki/Pride_Month), and probably a bumper crop of links interesting enough to bookmark.  If you've become a member on Buy Me a Coffee, then you can already see previews for some of that.

## Social Media

If it made any sense to care about the details, I'd almost consider breaking this out into its own post, due to the length.

### T2

I should mention that you can now [find me on T2](https://t2.social/jcolag), the...weird Twitter clone made by former Twitter employees.  No, not that one; I mean the *other* one.  And I mean the social media platform, not the film about an ooze-bot trying to police the timeline.  For now, expect this to look like a lot of social media, where I'll add it to the list of sites where I post announcements about new work here on the blog, and occasionally reply to interesting posts.  And if I find a lot of people who I like, I'll spend more time than that.

### Post, Spoutible (Less)

Also, due to newly added constraints on my time, I'll probably only drop in at Post and Spoutible when I post an announcement there or on the weekends.  It takes too much time, and they both have too much of the kind of content that already didn't interest me on Twitter.  If I have to look at one more "meme" that primarily wants to remind me that some terrible politician doesn't have an attractive face, or read one more person begging everyone to share their worthless post with our followers... {% emoji exploding head %}

### The Usual Suspects

I remain active [on Mastodon {% emoji elephant %}](https://mastodon.social/@jcolag/) and [on Cohost](https://cohost.org/jcolag), despite Cohost's announced precarious financial position making me think that we won't have it around soon, at least not in its current form.

### Lemmy

Experimentally for now, you can also [find me on Lemmy](https://vlemmy.net/u/jcolag), the Federated Reddit clone.  I never really warmed to Reddit---I have an account there, and over the years have commented maybe a dozen times, and posted far less than that---so the flight from there doesn't affect me, but I could see this working.  Feel free to suggest any communities that sound like my kind of thing, if I haven't already seen them.

### Matrix

Also---reminded by signing up to Lemmy---we'll have to see whether it sticks, because I don't see much conversation that interests me, but after a *long* time away, I've started visiting Matrix again.  I'll try to drop by at least a couple of times per week for a while, so feel free to say hello at [`@jcolag:matrix.org`](https://matrix.to/#/@jcolag:matrix.org), as long as you don't mind the chat lagging by several hours.

### USENET?

Even less likely that it'll stick, despite the format making *far* more sense for me than any social media would, a comment on Lemmy pointed me to [Eternal September](https://www.eternal-september.org/), which supplies free [USENET](https://en.wikipedia.org/wiki/Usenet) accounts...*minus* the binary groups, in case you had aspirations {% emoji pirate flag %} of engaging in twentieth-century-style piracy.  I say that I probably won't keep up with anything, there, because I've only found one newsgroup of even potential interest, `rec.arts.int-fiction`, the Interactive Fiction newsgroup that I followed twenty-odd years ago.  I poked my head into the *Babylon 5* and *Star Trek* groups, but the minimal conversation didn't seem to cover anything of interest to me.

### Future Options

For Lemmy and Matrix, though, if readers show up there, you could probably convince me to run a community or chat room.  Especially if [members](https://www.buymeacoffee.com/jcolag) find it interesting, I could hold periodic "office hours" on Matrix, where you can track me down "live" for a few hours every month on a private room.  I also *nearly* created a Free Culture community on Lemmy, before realizing that readers already don't post comments here.  But since I've already considered it, it probably wouldn't take much effort to persuade me otherwise.

Seriously, if that sounds like something useful to anybody, get in touch.  Or feel free to do the work and invite me.

## Mastodon Tool Trunk

{% github jcolag/tool-trunk %}

All of this week's time went here, actually, without too much to show for it.

The *Rummager* now gets better use out of [Pantry](https://getpantry.cloud/), using a specific "basket" of data, sending it in the correct format, and actually waiting for the data before laying out the timeline.  As a result, you shouldn't see the same toot twice, anymore, at least in this interface.

You'll also notice that the initial batch of toots downloaded from the server has grown to the maximum.

## Next

This week, I'd expect more work on the *Trunk Rummager*.  I need to figure out how to use HTMX---or whatever I end up using---to make the API calls.  When grabbing toots from the API, it should also keep retrieving until it finds a toot that it has shown before.

Also, maybe I'll look at the Matrix API, and see if I can't figure out how to automatically post blog announcements there.  If I can do that, then I wouldn't mind creating an *Entropy Arbitrage* chat room and letting it cook along for anybody who wants to talk about posts or related topics without relying on the comment system used below.

* * *

**Credits**:  The header image is [Baron Kelvin](https://commons.wikimedia.org/wiki/File:Baron_Kelvin.jpg) by an unknown photographer, long in the public domain due to an expired copyright.
