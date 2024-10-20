---
layout: post
title: Getting the Most from Mastodon (and Friends)
date: 2024-10-20 07:01:04-0400
categories: 
tags: [mastodon, social-media]
summary: An updated attempt at a gentle guide to the Fediverse
thumbnail: /blog/assets/31796917134_49240d896d_o.png
offset: -15%
description: Figuring out how to make Mastodon more homey than a Twitter clone, for people heading (or already) there.
update: [
  2022-11-20-mastodon.md,
  2023-03-26-etiquette.md
]
spell: Pinkary Rochko Groucho Friendica Pixelfed Bookwyrm Lemmy PeerTube Akkoma Mobilizon Fedi href Deitz bookstodon Carnac duolingo DuolingoUpdate tsk-ing Mammut americanum
proofed: true
---

* Ignore for ToC
{:toc}

I originally wanted to get this out last month (sorry), but as people look for new social media homes, whether from the closure of Cohost or {% x %} finding some new way to discredit itself and everybody who spends time there, I want to make some suggestions for a better experience on Mastodon and the so-called Fediverse in general, since I imagine a lot of people will head there.  Note that I've borrowed parts of this post from earlier posts, either deliberately or because we keep ending up in this situation from other places closing.

![A mastodon skeleton from above](/blog/assets/31796917134_49240d896d_o.png "You must toot, because she can't...")

Regardless, you should find links to those prior posts at the top of this one, if you need more depth.

Why do I not talk about other platforms, here?  Well, most social networking platforms don't really warrant much explanation, because they only have one mode of use.  When you log into [Pinkary](https://pinkary.com/), to pick a newcomer, you learn how to use the application in front of you and go.  On the Fediverse, though, you have so many people writing software for so many audiences, that you can find almost any (software) experience that you can imagine.

## Overview

I realize that not everybody wants to go through the Fediverse bit.  For many people, the choice of any media often boils down to wishing that a *slightly less egregious billionaire* will tell you what to care about.

Also, depending on when you heard about the Fediverse, it has one of a handful of reputations.

If you have spent time around it for a long time, like myself, it has a reputation as a friendly and welcoming space.  The majority of major players in creating ActivityPub identify as a gender or sexual minority in some respect, and so they took the lessons of harassment on Twitter at the time, and built a system resistant to those problems.  As such, many people have considered the network friendly to minority groups.  And yes, this *does* sound a lot like denying racism on the basis that you have a Black friend.

The friendliness absolutely has a flaw, in that every server needs to "figure out moderation" for itself.  And because you have a wide variety of people interested in hosting their own corner of social media, you get widely varying moderation techniques and focuses.  You'll get some servers that cater to racism and hate speech, whereas you'll have others that ban anything that might make somebody uncomfortable, and everything in between.  As a result, while people like myself---straight, white men---rarely see any harassment at all, because we don't sift through everybody's replies looking for horrible people, that doesn't make them go away, and moderation somebody allows them through.

Then spring 2022 hit, and people fled Twitter because Apartheid Clyde bought the place.

The influx of Twitter users gave the Fediverse a new reputation, that of an insular community with a rigid culture.  Every site tried to defend its culture against wave after wave of people looking to "score points" by posting ugly pictures of Donald Trump or whatever, but somehow the Fediverse got the blame, possibly because "use a content warning" sounds more like tone-policing than a site taking action against people with progressive views.

Anyway, I point this out because, if you'd rather go look for a slightly less egregious billionaire to hand you an algorithm to tell you who you should follow and what issues matter, this week, or if you think that you found a small company that'll sustain itself, go ahead and skip this post.

## Feel Free to Skip Mastodon As Such

First, always bear in mind that Mastodon acts as "part of the Fediverse," a collection of applications speaking (dialects of) the same language, which allows them to interact.  Because [Eugen Rochko](https://zeonfederated.com/) started the project in 2016, Mastodon looks a lot like Twitter did at that time, minus the features that the alt-right at the time used to direct harassment at people at the time.  Some worrisome-at-the-time features have since found their way in, and others have made it to some stage of development.

However, those constraints don't work for everybody.  And a lot like the Groucho Marx line, "those are [Mastodon's decisions], and if you don't like them...well, I have others."

Do you want to write longer-form posts?  Maybe you'd rather take a crack at a [Friendica](https://friendi.ca/) server.  Do you want something more like Instagram?  [Pixelfed](https://pixelfed.org/) might work for you.  Would you rather have something more like a blog?  Take a look at [Write Freely](https://writefreely.org/) or [Plume](https://joinplu.me/).  Do you want to review books?  Maybe you'd rather look at [Bookwyrm](https://joinbookwyrm.com/).  Would you rather something that looks like a forum?  Maybe [Lemmy](https://join-lemmy.org/) will work for you.  If people might pay for your posts, [Sub Club](https://sub.club/) might go well.  Or you could look for podcasting, video-sharing, music-sharing, bookmarking, event-planning, code-hosting, second-hand sales, and more.

And critically, as long as the software supports ActivityPub---the aforementioned "language" (protocol)---you share the same network.  Not everybody has a consistent interface, but you can use a Mastodon account to follow PeerTube channels and reply to videos as if leaving a comment, for example, or go through many other variations.  Mastodon probably has the most polish after eight years of active development and one of the smaller scopes, but other options certainly exist.

Sometimes, even though everything should theoretically talk to everything else, you'll want accounts on different kinds of systems on the Fediverse, if the interaction between platforms doesn't work as well as you'd like[^1].  Nobody has a problem with that, as long as you don't maliciously misrepresent yourself.  I have a couple of Mastodon accounts, and Akkoma account, a Lemmy account, and a Bookwyrm account, myself, used to varying degrees.  Eventually, I'll probably need a [Mobilizon](https://mobilizon.fr/) account for some event.

[^1]:  And increasingly, you'll get Fediverse accounts with membership in various places, meaning that those accounts may start piling up like e-mail accounts often do.

I'll assume, though, that you'll end up on Mastodon, because as much as people complain about it, the system does have the most polish, and so people gravitate to it.

## Quick Mastodon Basics

You probably want to know that Mastodon limits posts to five hundred characters, though now has the capacity for (ugh) threaded posts, if you want the "engagement" of people interacting of random parts of your longer post.

However, you'll also want to know that tags count against your character limit, *but* URLs always count as fifteen characters, no matter their length.  If your user interface knows that, it lets you cram in more than you'd expect.

## Servers, Instances, Pods, and More

This audience probably already knows this by now, and I wrote about it in more depth in a post [introducing Mastodon to people]({% post_url 2022-11-20-mastodon %}) a couple of years ago, but the Fediverse scatters the load around the Internet, so that no single group needs to shoulder the burdens of maintaining a social network.  How do you choose your server?

If you want to carefully research this decision, pick a large or curated list of servers---you'll sometimes see terms like "instance" or "pod," which largely depend on how programmer-oriented or stylistic the speaker/writer feels---like [Mastodon Instances](https://instances.social/) or [Fedi Garden](https://fedi.garden/), or if you want to drill down into more specific traits, maybe [Fediverse Party](https://fediverse.party/) and/or [Fediverse Observer](https://fediverse.observer/), and check for servers for people with your interests or other requirements.  You can compare that information with what each site allows and doesn't allow in its terms of service, and maybe check what block-lists they use to protect their users from dealing with poorly moderated servers.

If you pick a "bad" server, it'll probably look a bit like corporate social media, in that moderation will happen unevenly, or the site might need to close down when the owner's priorities change.  You can always move your identity to a new server, if you don't like where you ended up.  You can't drag your history of posts from server to server---they'll always stay where you posted them despite the ability to export them---but ActivityPub automatically redirects people when they go looking for you, so you won't generally need to worry about losing your friends or audience.

As such, I often recommend pushing past the whole Paradox of Choice thing and picking any site that doesn't seem overtly awful.  I like the analogy of shopping for insurance or even mustard, where all the products look similar, and no amount of research will provide you with the optimal choice for you.  If you have friends on a server, then that server will probably work fine, even though that doesn't generally work for insurance *or* mustard.

## My Voice Is My Passport

If you have a website of your own---and you really should, even if you only use it to link people to where they can contact you or read what you post elsewhere---then you'll want to set up validation.  Like verified accounts on other social media platforms, this makes it more difficult for somebody to pose as you.  Unlike other platforms, you do this on your own.  This involves two steps.

First, you need to provide a link from your website to your Mastodon account, ideally on every page, but not for this.  For example, on my website, the HTML code looks something like this.

```HTML
<a href="https://mastodon.social/@jcolag/" rel="me">Mastodon</a>
```

Mine starts a sentence in a bulleted list, explaining why it doesn't provide anything like instructions about following.  You can dress it up to say "follow me on Mastodon," replace the text with an image, or whatever else you might need.  You can actually even *hide* the link, if you don't want to point people to your account or if you have another link elsewhere.  It only matters that you have the link with your profile in the `href` attribute and the `rel="me"` bit.  In English, it says "I consider that link (to my Mastodon profile) part of my identity."  You'll hear the people deeply interested in the technology side of this refer to it as [identity consolidation](http://microformats.org/wiki/rel-me).

Once you finish that, run over to your Mastodon preferences, under *Public Profile*.  There, you'll see a small table labeled *Extra Fields*.  There, you can insert any information that you want people to know about yourself.  My extra fields include these.

|Title|Value|
|-----|-----|
|Pronouns|he/him|
|Personal Website|<https://john.colagioia.net>|
|PGP Key|<https://keyoxide.org/hkp/261994FEE8CA821E96F171CE9D576E45591D6FC8>|

By the way, you can pull your `rel="me"` link from the *Verification tab*, while you have your profile open.

PGP keys give you an alternate route to verify your account.  I don't know that it helps anything at this stage because I don't see how it identifies me better than anything else, but if you want to do it, I walked through the process in that aforementioned introduction-to-Mastodon post, under the heading [The Techie Solution]({% post_url 2022-11-20-mastodon %}#the-techie-solution).

Regardless, validating with a website also gives everybody a little help, which we'll talk about next.

You can also use that table for anything that you want people to know about you that doesn't fit in your biography.  I have pronouns.  Somebody else might use it to indicate a book that they've started reading.  Verification tops the list of important uses, though.

## Voices and Passports, Revisited

Before you stop working on validation, assuming that you do have a website of your own, you might want to slip an unrelated-even-though-that-makes-no-sense bit of HTML into your page *header*.  Mine looks like this.

```HTML
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="fediverse:creator" content="@jcolag@mastodon.social">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- and so forth -->
```

We care about the `fediverse:creator` line (#4), specifically.  This allows Mastodon, and eventually other Fediverse participants, to [highlight journalism](https://blog.joinmastodon.org/2024/07/highlighting-journalism-on-mastodon/) by connecting links to that page with your account on the Fediverse.  I don't pretend that I do anything like journalism, but I still find the mechanism valuable, because it helps to connect my writing across different platforms.

Anyway, to finish setting this up, under that same *Public Profile* configuration, select the aforementioned *Verification* tab, then scroll down to *Author attribution*.  It gives you the `fediverse:creator` tag to add, then add the domain name(s) of the website(s) where you write.  For example, I have a list that includes `john.colagioia.net`.

In my case, having set that up, when people link to one of my blog posts (in a way that produces a preview), it adds a *More from John Colagioia* link underneath the preview, so that people can quickly find me on Mastodon, too.  If you have pages that people might want to read, and you want those people to find you on the Fediverse, you'll probably want to add that, too.

### Even Deeper

Oh, if you don't work on HTML routinely, then you might want to know that the previews for your pages draw from [Open Graph](https://ogp.me/) metadata in the HTML heading.  If previews don't show up as you'd prefer, then you probably want to add or modify the headers for your page.

Or, rather, you'll want to add or modify them on *future* pages, since your Mastodon server has probably already cached its preview.  But set them on all pages on your website, for other servers, all the same.  If you use a blogging system that has seen use for a while, then it probably already has something built in already to do it.

## Browser Extensions

The Fediverse has two major complications that other social networks don't have.  Conveniently, people have solved them with browser extensions, and I'll share the two that I use, here.

### Graze

Because we have our accounts on different servers, you'll get into the occasional awkward situation where you'll click to follow somebody (or like a post, or whatever) in a hurry, only for the site to tell you that you need to log in or track down the person or post from your own server.  Nobody likes that situation, but without some sort of weird single sign-on solution that *probably* becomes a security risk, servers can't guess at your identity.

Jared Zimmerman's [Graze](https://addons.mozilla.org/en-US/firefox/addon/graze/) plugin---definitely for Mastodon, maybe for other browsers, too---skips over the problem by rewriting Mastodon pages that you visit to redirect the buttons to whatever server you set up.  With the plugin installed and configured, when I click on a link to somebody's post on a different Mastodon server, it acts like I looked at it on `mastodon.social`.  I can like the post, boost it, or bookmark it, and I can follow the person without any extra steps.

If you have multiple accounts that you want to use in different contexts---for example, identities that you want to keep separate---this might not work with you, but for me, it makes all Mastodon servers look interchangeable.

Likewise, if you don't like or can't use Graze, then the search-box on your server quickly becomes your friend.  "Search" for the URL for any profile or post from your server, and it handles the connections as you'd expect.

### Street Pass

Social networks, shockingly, don't help if we can't find people there.  And since the Fediverse still mostly acts like a small community despite [millions of users](https://fediverse.observer/stats), people don't always publicize their accounts like they do for {% x %} or one of the more mainstream services.

Tyler Deitz's [Street Pass](https://streetpass.social/) plugin tries to solve this by exploiting the work that we did for identity verification in the [section before last](#voices-and-passports-revisited).  When you visit any web page for the first time, it looks for a `rel="me"` link that points to a Mastodon server.  If it does, the plugin's icon lights up and adds a link to the account on its drop-down list with the URL of the page that you visited.

After all, much like the author verification in the previous section, if you read and enjoy a blog post or article somewhere, then you *probably* want to know about the social media presence of the author or organization.  This saves you the trouble of hunting for it, at least for some cases.

By the way, when I said above that your identity consolidation link should go on every page of your website, I had this in mind.  You (probably) don't want to make people hunt for your account by only burying the link on one page, even though you only need one link for verification purposes.

## The User Interface

I don't know whether I'd call the prior sections "opinionated," even though they definitely derive from my opinions, but everything in this section, I absolutely call Opinionated with a capital-o.  Specifically, I dig into settings that I think will make your time on Mastodon less frustrating.

Note that I use Mastodon---and all social media---from desktop browsers, so those of you on mobile will need to poke around on your own to see what works for you, especially since every mobile app views the network differently.  You might also note that I only check in on Mastodon once in the morning and once in the evening, assuming that I have time for it; that already saves a lot of stress, and I highly recommend it.

### Slow Mode

I don't know why the software even presents this as an option.  However, as your top priority, I say that you should make sure that you turn on *Slow Mode*.

 > Hide timeline updates behind a click instead of automatically scrolling the feed

Do you want posts to skitter away when you try to click to like or report it because somebody needed all their followers to see the latest political cartoon?  By all means, turn it off.  But if you'd rather read the posts and interact with them like a healthy person, turn that setting on.  Rather than scrolling your feed, the heading will "glow" to signal you that you have newer posts to read.

As a bonus, if you feel rushed, you can ignore the glow and declare yourself "caught up" until the next time you check in.

### Advanced Web Interface

Mastodon's primary interface looks like Twitter, one column with your timeline, and nothing else.

By contrast, the "advanced" interface---the checkbox labeled *Enable advanced web interface* in the preferences---gives you multiple columns.  You get your searching and posting tools to the left, then your "Home" timeline, your notifications, **other things**, and then some convenient links around the software and (if you turned it on) trending hashtags.

Those "other things" include following tags or lists.  The latter, we should talk about.

### Use Lists

Getting back to the top of the post about the design decisions of the Fediverse and Mastodon, lists have a bad reputation from {% x %}.  While the design comes from the idea that somebody might want to look at a timeline of, say, comedians who share some common set of topics without needing to follow them, bigots use them to collect people to harass and then publish the list for other bigots to follow, without any of the offenders needing to otherwise interact with the unsuspecting targets.

Have no fear, Mastodon lists don't work that way.  Instead, Mastodon allows you to collect people who you already follow, and copy (or move) their posts from your main feed to a parallel feed.

I follow plenty of people, so my main timeline looks like a mess, especially during election season.  And most of it, frankly, I don't want to read[^2], especially if I don't have time to kill...and if I do have time to kill, I never want to kill that time on social media.  As a result, I currently have four lists of accounts that I consider a different (usually higher) priority than "everybody," and I present them here, to give you an idea of how they might work in practice.

[^2]:  I apologize to all the people who I follow but don't read.  I wouldn't follow you if I didn't see *something* interesting in your posts, but either the volume or the topics have my eyes glazing over...

* Low-Noise:  This list includes the handful of real people who I actually know in the outside world, as well as people who post clever things without clogging my feed up with other people's slop, fifty-post threads about their grocery shopping, how they managed in some daily game that I don't care about, or whatever other nonsense that you can find out there.  If I have time for nothing else, I make time to catch up on this list.
* Free Culture:  You know that I can't go long without getting excited about work that people can share, modify, and reuse without restrictions.  I follow a bunch of creators and projects on Mastodon, and I want to keep them somewhere that I can actually find them.
* Cohost Folks:  Since I actually did at least look at every post from everybody who I followed on Cohost, I don't want to lose the people who come find me on Mastodon, so they now have their own list.
* News:  I follow some small news organizations, and while I don't always have the mindset to want to read through the headlines---I mean, they don't really change that much, and if they change abruptly, I've already seen the catastrophe in my RSS reader---so I put them in their own column.  I also throw bots in here.

I have these lists "pinned" to the aforementioned advanced interface, so that I don't need to root around looking for the Cohost thing.  And I have them configured to remove the posts from my home timeline, so that I don't see them multiple times.

I then have a couple of pinned panels to follow tags---most of which I ignore, most days, because I don't have the time to peruse what other people have read on `#bookstodon`, for example---and that breaks up my monolith of a home timeline into something where I can prioritize.  And (as suggested above) if you activate the *Hide these posts from home* toggle on the list configuration, then you won't see the duplicates when you venture onto your home feed.  Lists make following random people about as low-stakes as you can possibly get.

Heck, if you want to go the sneaky route, you could move people who you *don't* care about to a list, and then "forget" to pin that list to your page, so that you still follow them but never see their ~~garbage~~ beautiful content.  I don't do it, but I've *thought* about it a few times for people who share a lot of content from bots...

## Content Warnings

I know, the big one.  This becomes the issue where people decide that this community doesn't want you.

First and bluntly, they probably don't.  New people trying to insist that their way of posting works better than everybody else's?  You know that doesn't work.  You have *probably* stood on their side of things, on some other site.  Nobody wants that "you have it all wrong" energy in their space.

Second, do yourself a favor and rethink the entire idea of content warnings.  We use them when a post has a good chance of triggering post-traumatic stress in people, but we should also use them more widely, so that the "main" use looks routine.  But also, content warnings give you an opportunity to add an extra comment to your post, so why would you *not* want to do that?

In a post from last year trying to distill [modern social media etiquette]({% post_url 2023-03-26-etiquette %}), I suggested the following list of reasons why you might want to consider a content warning, updated here (and adding a couple) with examples.

* As mentioned, the post refers to a common trigger for post-traumatic stress.  You might warn *CW: Sexual Assault*, for example.
* The post gets involved with a subject that requires extensive research to have any meaning.  You might warn *CW: US Horse-Race Politics*.
* The topic or the phrasing that you use might make the reader's situation uncomfortable, if they have a seat next to a curious stranger, colleague, boss, or child.  You'd probably warn *CW:  NSFW*.
* The post discusses a fictional work that people may not have seen/completed.  You'll almost certainly warn *CW:  Spoilers for XYZ*.
* The subject of the post made *you* furious or terrified about the topic.  You might go with *CW:  Processing Feelings* or even rant a bit in the content warning.
* The post goes out to a specific subset of your audience, and the rest of the group probably won't care.  You might try something like *CW:  Kid Pictures*.
* The post recycles an old joke.  You might want *CW:  Outdated Humor*.
* You have a funny joke about the post that doesn't fit *with* the post.  Only you know what fits in the warning.  I have amused myself in the past with warnings like *CW:  A Certain Musk-y Odor*, when talking about the Twitter's change in management, even though I can think of other reasons to hang warnings on those posts.  I've also enjoyed seeing people do a [Carnac the Magnificent](https://en.wikipedia.org/wiki/Carnac_the_Magnificent) bit using the warning to hint at but misdirect on a broader joke post, or to add a joke to make a serious post more palatable.
* You feel like making readers click through to read.  Why should we constantly live in an instant-gratification society, you know?

You probably get my point, here.  Rather than worry that people will harass you for not using enough warnings, look at it as an opportunity to add another layer to your posts.  The fact that it also makes different kinds of posts opt-in only means that we have converging interests.

That said, the Fediverse has had *so many* people come over from Twitter, where the algorithm rewarded you for shocking people, and fascists doing fascist things provided an easy way to shock people, content warnings almost seem quaint at this point, other than for nudity or pictures of outright gore, the sorts of things that you probably don't want a friend to have pop up on their screens while a manager or family member looks over their shoulder.

Oh, speaking of which, also mark sensitive media as sensitive.  Your *NSFW* warning could mean that you curse, but it could also mean photographs of victims of violence.  Let Mastodon blur it for people, so that they have an extra beat to decide if they want to click through.

## Alt Text

Likewise, describe your images, ideally in the context of your post.  Not everybody can see.  Not everybody has a good enough Internet connection to load every image.  Sometimes, software bugs prevent images from showing up.  Personally, I set Mastodon to blur all images, because I assure you that I don't care about your memes, your artsy photograph of a plant growing in your yard, or your painstaking sketch of intimate parts of human anatomy.  I could go on, but you get the idea:  If your image doesn't have a description, then assume that most people won't see it.

If you have trouble remembering to do that sort of thing, do yourself a favor and follow the [Alt Text Reminder](https://mastodon.social/@alt_text) bot.  She'll follow you back, then send you a polite, private reply if you post an image without its description.  Then, you can quickly edit the post before anybody notices, and look like you care.

A lot like the content warnings, though, so many people have joined the Fediverse from places with far worse cultures that, if you forget your image descriptions, the people who need them will probably stop following you---under the assumption that you don't want them in your audience---instead of complaining.

## Tagging

Please tag your posts something reasonable.  You'll want to do this for two reasons.

First, like most small and non-corporate social media spaces, nobody has any algorithm picking posts for you to see other than "things that people you follow posted, in chronological order."  Tagging your posts gives other people the opportunity to find you through a shared interest.  I've gotten to know people because of the few tags that I follow.

Second, and maybe equally importantly, people can filter posts by tag, so that they don't need to slog through posts that they won't care about.  For example, I have `#duolingo` and `#DuolingoUpdate` messages blocked, after at least a month of people whining about whatever corporate thing that the company had going on at the time.  It generated a lot of angst so deep in jargon that I couldn't make out what they cared about, so it seemed safe to assume that I wouldn't care.

You can add your one-off joke tags, but please build from a base of tags that people will recognize.

## Changing Cultures

I should note that, no matter what you've heard about the Fediverse culture, you probably have it both right and wrong, some of which I got into at the start of this post.

Especially among the "old guard" of Mastodon users---I guess including myself, given that my account dates to September 2017---you'll find a culture that angrily rejects a lot of what everybody saw in social media in 2016.  To those people, you *must* put a content warning on any post that might disturb well-meaning people (whatever that might mean) and add alt text to your images.  Tags had better have conventional meanings, as I hinted above.  If you want quote-toots, lengthy threads of short posts, or full-text searches of posts, then you should leave, because that way lies the destructive influence of mainstream social media.

And then Twitter's management changed, and Mastodon went from a toy that Free Software weirdos used to something that normal people actually know about, even if they don't use it.  With millions of people, most of whom came from the digital ~~sewer pipe~~ *town square* itself, the culture has changed drastically.  After all, when you have millions of people who don't even understand what a content warning *does*, you can't shame them into using them.

And to support these new people, Mastodon has added threads and search indexes---angering many people---and, as I mentioned above, other once-bad features have made it to somewhere in the development pipeline.

Every small site has this problem, in my experience.  People complain about how exclusive other spaces feel because they want to preserve how things work over there, then turn around and---without a hint of irony---complain about an influx of newcomers who refuse to learn how their space works.  Try not to become that person...

The culture has changed.  It will change again, probably many times.  And it goes to show that enforcing a culture doesn't really work.  If you "use the site wrong," unless you transgress enough that moderators might ban you, nobody can do worse than make disapproving sounds.

## No Crimes via DM

Every few months, some new genius "discovers" the fact that, when you set a Mastodon post to only show up for people mentioned---a private message, in other words---the server doesn't encrypt it. {% emoji exploding head %}

They write about this "discovery" in breathless tones, warning you not to use the private messages, as if anybody ever promised to encrypt them.  And they also do this as if any other social networking site provides end-to-end encryption for personal messages; they don't.  But it means that somebody needs access to the database to read those messages, since the software won't let anybody else see them through the interface.

In other words, this doesn't change from any other system.  Don't use the system to "secretly" plan or commit crimes, because police departments can demand copies of your personal messages from the server owners.  If you don't trust the people who own your server, then don't talk about anything that they could turn into gossip on their server.  If you must say something that you don't trust the owners to access, use another route to do it.

## Scheduling Posts

Did you know that you can schedule a post to go out on Mastodon whenever you want?  

The main web-based user interface doesn't show it, for some reason, but the server can accept posts scheduled to release in the future.  For example, the toots in my [social media roundup](/blog/tag/link-dump) posts generally get planned out and published over the prior weekend.  Then they post a little after nine in the morning and noon on weekdays, even though I don't make myself available at those times.

If you use almost any other software to post---web-based, native app, a script, or whatever---*other* than the official user interface, then it will probably let you set a time for your post.

Your server may have restrictions on the schedule, such as how many posts you can schedule in advance or how far in the future you can plan them, but I haven't heard anybody complain about it, so I don't imagine that those restrictions come up often.

## The API

Finally, if you like programming, I have good news:  Mastodon's API feels like one of the nicest that I've seen.

This has two outcomes of likely interest to people.  First, it means that, if you don't like something about Mastodon's user interface, you can probably find somebody who has made a replacement interface for your platform of choice.  If you wish that Mastodon worked as a text-only terminal application, wanted it to stitch together threads into a single long message, or let you change the colors of each person's posts, somebody *probably* has an interface---you'll sometimes see the term "front-end"---that does it.

However, as I mentioned, you have another outcome of interest, that you can quickly write programs that interact with Mastodon.  They designed it for people who wanted to write those aforementioned alternate user interfaces, so you can have a program that does anything that a user might.  If you want a bot, an archiver, a scheduler, notifications when certain people respond to you, or whatever, you can do that without much trouble.

I actually wrote a post on the few [pitfalls that I found working with the Mastodon API]({% post_url 2023-03-29-mastodon-api %}), which might prove useful to some of you trying to get started.

## Overall

That all said, enjoy yourself.  And ask questions instead of complaining, when something doesn't feel right, because (as mentioned) a solution probably exists, and you don't want to sound like the person tsk-ing everybody for not doing what {% x %} (or wherever) does.

* * *

**Credits**:  The header image is [Mammut americanum, Pleistocene; Aucilla River, Jefferson County, Florida, USA 8](https://www.flickr.com/photos/47445767@N05/31796917134) by [James St. John](https://www.flickr.com/photos/jsjgeology/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
