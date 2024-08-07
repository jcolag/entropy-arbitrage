---
layout: post
categories: programming
tags: [programming, decentralization, socialmedia, moderation, community, cultivation, curation, socialshowdown]
title: Distributed Community Curation
date: 2020-04-25 07:39:38-0400
summary: An attempt at creating a distributed moderation system
thumbnail: /blog/assets/prague-shadows.jpg
offset: -29%
---

* Ignore for ToC
{:toc}

![Community](/blog/assets/prague-shadows.jpg "Community, back when clustering on a city street didn't risk people's lives")

After [making the rounds](/blog/tag/socialshowdown) of non-corporate social networks, I developed the idea that decentralized systems have a *serious* problem with what is traditionally called moderation, but is really a sort of community cultivation or curation.  I'm going to use [Scuttlebutt]({% post_url 2020-01-25-scuttlebutt %}) as my example, though most of the same ideas would apply to any distributed network and at least some of it also applies to the federated networks.

The problem is, basically, that as bad actors join the system, users can each choose to only block them individually.  That's fine on a personal level, but it's unfortunately the entire story.

{% pull ...but the public face of the community might be an open sewer pipe of obnoxiousness. %}

Thinking more globally, this creates a weird situation where experienced users of the network feel like they have a supportive, right-thinking community around them, but the public face of the community might be an open sewer pipe of obnoxiousness.  And that surface appearance rubs off on all the network's users, because nobody in their right mind would use a network packed with spam and hate speech unless they were a spammer or bigot.

Put simply, it's the burden of people who aren't *already* invested in the community to figure out the difference and spend time blocking all of the garbage.

And, of course, they won't do anything of the sort, because they have no reason to believe it's worth the trouble when they can just find a Mastodon instance that blocks garbage for them, wait for the [Openbook](https://www.open-book.org) people to get their act together, or return to Twitter and Facebook under new names.

It's less interesting to talk about, by the way, but there's also the flip-side of this problem in *discoverability*.  Just like we don't know who to ignore, we also don't know who might be worth listening to.  Like I mentioned [last week]({% post_url 2020-04-18-thoughts %}), too many social networks assume you already know who you want to follow, and provide no advice except maybe people who are currently active.  Those are both the same problem and could have similar solutions.

## Possibilities

So, if that's the problem, what solutions can we put together?  Keep in mind that decentralization means that that there is no power that can remove the bad actors from the network, nor does any user have anything like a view of the entire network.

{% pull ...the list of decisions to block a user.|left %}

What we *do* have, at some level, is the list of decisions to block a user.  To prevent the user from seeing content they have blocked, one of two things must happen.  If the network is federated, then the pod/instance needs to know about the block, just as a centralized system would.  In a fully-decentralized system, users would need to *publish* the blocking messages to prevent their peers from sending unwanted information to them.

To make the former work, the protocol would probably need to change so that the federated instances can inform each other of the blocks they know about.  But for a decentralized system, this would mean that many users would already have access to the information they need and pass it to their peers naturally.

So, if we have a program to scrape the feed looking for who has been blocked previously, we have a list of blocks on the network.  OK, technically, this is just the blocks that your peers know about, rather than the entire network, but this is just as good, since your peers are going to be the majority of your network.

From this, we could simply get a list of the users who have been blocked, sorted by the number of users who blocked them.  That then becomes a prioritized list of candidates who are worth quickly investigating to see if it's worth your effort blocking them, too.

{% pull ...theoretically possible to have the client software automatically block the most infamous offenders... %}

Assuming that all worked, it's at least theoretically possible to have the client software *automatically* block the most infamous offenders for new users.  They can always unblock later, of course.  It's also possible to weight the actions of different people differently, which I'll talk about later.

Regardless of the additional tweaks we can add to the case, we now have a solution to our problem:  By offering a default list of people who the community largely thinks should be blocked, new users would see almost no spam or hate speech when they start participating, unless they take specific actions to find it.

## Scuttling Away

Because decentralized systems seem more amenable to this analysis and because I already use it, [Scuttlebutt 🦀](https://www.scuttlebutt.nz/) is the obvious target, especially since the [Scuttlebot](https://scuttlebot.io/) library exists and I've already played with it for some minor projects.

If you're not a JavaScript person, you'll probably just want to ignore the code or skip ahead some, because it's probably going to get pretty tedious.  But the algorithms are fairly straightforward, so don't feel too intimidated and feel free to ask questions in the comments.

In any case, when I tried this out a year or two ago, I installed the libraries and skimmed the documentation looking for a way to get messages by type, and...it turns out that there's a `messagesByType()` method, so that wasn't nearly the research project I was expecting.

Best I can figure from discussions, since it wasn't explicit in any of the documentation, I gather that the message type I'm looking for is "contact," which includes blocking, following, and so forth.  So, that gives me code that looks something something like the following, for a first pass.

```JavaScript
const ssbClient = require('ssb-client');
const pull = require('pull-stream');

ssbClient(function (err, sbot) {
  pull(
    sbot.messagesByType({ type: 'contact' }),
    pull.collect(function (err, msgs) {
      console.log(msgs);
      sbot.close();
    })
  );
});
```

It's not *quite* that, since I check to see if there were errors at each step, but the flow is the same:  Open the client, get the block messages, organize them, print them in order, and close down.

Running a client such as Patchwork to connect to the network and running my script, I get a flood of messages, so we're definitely onto something.  It looks something like this, after I stripped out anything that might indicate who's involved:

```JSON
{
  key: '%key1=.sha256',
  value: {
    previous: '%key2=.sha256',
    author: '@userid1',
    sequence: 46,
    timestamp: 1234567890123,
    hash: 'sha256',
    content: {
      "type": "contact",
      "contact": "@userid2",
      "blocking": true
    },
    signature: 'somesignature'
  },
  timestamp: 1234567890123
}
```

The `key` is the message identifier.  The `previous` key tells you what the author saw most recently.  The `author` is the user who created the message.  The `content.blocking` item tells us that this is a user blocking the `contact` ID; you'll see messages with `content.following` instead of blocking, and contacts issued by a pub are marked with `content.pub`.

### Getting off Track

If you naïvely sift through the messages manually (like parsing out the `type` values) and try to piece together the crazy quilt of documentation for a rapidly evolving ecosystem, you might stumble on the `block` message type, which looks extremely promising.

However, with input from experts, I learned that `block` messages don't exist, probably a leftover on the network from someone's early experiment.  Ignore them and stick with `contact`, described above.

## Who Are These People?

So, that's the good news.  If we wanted to do this as simply as possible, we could harvest the `blocking` messages, count up the number of times each user has been blocked, and automatically block either anybody blocked by an objectively large number of accounts *or* some percentage of the top offenders.  Problem solved!

{% pull we can't leave our judgment to a few lines of code. %}

Except, hang on...looking up the IDs to find the accounts of these blockable candidates, I see a lot of names I would consider to be important to the community, whether they develop Scuttlebutt clients or are just friendly and interesting.  So clearly, we can't leave our judgment to a few lines of code.

(If anybody thought that this wasn't going to take a turn into the problems with easy solutions, I assume that you must be new here.  To catch you up, hi, the world is a really complicated place to live and easy solutions always have terrible consequences.  Also, Free Software and Free Culture are good things we should support, and I talk about *Star Trek* on Thursdays as an excuse to re-watch the original series...)

{% pull ...serve to compound the problem...|left %}

Plus, if we **did** automate the blocking process, it would only serve to compound the problem, by dramatically increasing the number of times those candidates have been blocked.  That leaves this approach open for exploitation.  We already know these systems can and are exploited on the corporate social networks, by marking everything a user says as "spam" and/or publishing "block-lists" for users to blindly import.

Any sort of automatic silencing is inherently a kind of weapon, so we're going to want to make sure that our version of the weapon is as safe to use as possible.  So, if this is going to work at all (no promises), we need to be more sophisticated about how we handle the data.  We want to block users who misbehave, not users who are the target of harassment.

### Follow Me!

One easy choice we could make---it's naïve, but not as naïve as merely counting block messages---would be to exclude users who have an absolutely or relatively high number of `following` messages issued for them.

{% pull ...we lose something in the translation and block someone people probably want to listen to. %}

For a concrete example that I hope won't embarrass him, one of the most-blocked Scuttlebutt users is [Andre Staltz](https://staltz.com/), creator of [Manyverse](https://www.manyver.se/), a Scuttlebutt client for Android devices.  It's weird to see people blocking him, because by all accounts and public evidence, he's a really nice guy who tries to do good things.  So, while a lot of people have blocked him, a much larger number of people also *follow* him, both for his thoughts and announcements on how the Scuttlebutt clients can/might/should change and also general discussion.  If we don't take both pieces of information into account, we lose something in the translation and block someone people probably want to listen to.

Similarly, a typical spammer probably won't have any followers, so that account is safe to ignore.

Therefore, we can take either the difference or ratio between the blocks and followings, and use the number to automatically block a bunch of lousy people.

Mission accomplished!

Right...?

Don't look at me like that.  You're creeping me out.

### The Enemy of My Enemy...

OK, OK.  You can probably already figure out that just performing basic arithmetic doesn't work, because it assumes that every account except for a few are both legitimate and operated by people who are basically good.  It ignores the possibility that an account might be popular among white supremacists, for example.  It also ignores the possibility that someone could potentially automate the creation of a large number of accounts that all follow or block certain people, such as following a spammer to make them seem legitimate or blocking a user who has an unfortunate political stance to skew any such algorithm like we've seen above.

{% pull ...we can think about implementing something that starts to look like PageRank... %}

What's our next step?  Well, if we can encourage a user to follow or block a few people as samples, we can use that information to give our analysis some context and perspective.  Specifically, we can think about implementing something that starts to look like [PageRank](https://en.wikipedia.org/wiki/PageRank)---which coincidentally saw its final patent expire in September 2019---in order to give a different meaning to each piece of data we get.

For example, if you follow me, there's a decent chance that you trust my judgment in what is or isn't interesting, at least to *some* extent.  So, if I block or follow someone, you might want to do the same.  If you have blocked me, you probably think my judgment is wrong, so you might assume you're going to disagree with my choice of who to follow and block.  And if you just see me floating through your timeline, you probably don't care what I think.

That's only one step, though, and here's where the PageRank idea comes in:  Now that you're relying on my judgment (whether through agreeing or disagreeing with me), we can extend that reliance to the people I follow or block, trusting (or mistrusting) them slightly less, because you're not directly connected.  And then repeat to the people *they* follow/block, and so on.

{% pull ...probably as good as we're going to get...|left %}

I'm not going to pretend that this is a complete solution, because this still has the problem of automating personal judgment.  But as a first pass, it's probably as good as we're going to get with just the block/follow numbers.

This nicely solves the problems of a tight community of terrible people or a "bot farm" trying to legitimize spammers, because those groups are going to be isolated from the main group (either completely ignored or blocked), so popularity in their circles won't artificially inflate the profiles of destructive people.

### In a Matter of Speaking...

If we want to take this idea a step further, we could also analyze actual posts from users for language, trying to pick out [sentiment](https://en.wikipedia.org/wiki/Sentiment_analysis)---especially in replies to other people---and terminology that might cause friction.

We could treat older block/follow messages as less interesting as newer messages, so that users don't find themselves permanently shunned because of some bad judgment in the past if they get better over time.  Similarly, users who post frequently can be treated from users who only post rarely.

There are probably other aspects of behavior I'm missing, but this would be some low-hanging fruit.

## Just Because We Can...

Like I mentioned earlier, pre-judging people based on simple metrics is a weapon, in that it's a tool to harm or control someone.  You would be entirely justified in feeling that it's unethical to let software make these choices for us entirely.  I don't really disagree with that sentiment, either, and consider this more of a "computer-aided management" idea than something to be imposed on every user.

{% pull ...as networks like Scuttlebutt grow, we're going to see an increasing number of disruptive users show up... %}

However, as networks like Scuttlebutt grow, we're going to see an increasing number of disruptive users show up, whether they're planning to deliberately disrupt the network ("trolls"), thinking they've found a gullible market ("spammers"), or just trying to rebuild a community that was rightly kicked off another platform ("bigots").

While experienced users can easily find and block these creeps as they show up, new users are going to be overwhelmed by the magnitude of work involved in making the network not seem terrible and just leave.  So, while automatically blocking people isn't ideal, giving a new user the *opportunity* to do so has the potential to improve the on-boarding process and make the network more welcoming for everybody.

## Code

If you want to play, you can find my sample code in my [Little Scuttlers](https://github.com/jcolag/LittleScuttlers) repository.  Eventually, my plan is to return to my [**zoea**](https://github.com/jcolag/zoea) project, taking what I've been learning working on [**Uxuyu**](https://github.com/jcolag/Uxuyu) to create a Scuttlebutt client with a clear on-boarding process and the sort of community curation tools described here.

We deserve it...

#### <i class="far fa-handshake"></i>

* * *

**Credits**:  The header image is [Group of people in the sun](https://skitterphoto.com/photos/4612/group-of-people-in-the-sun) by [Peter Heeling](https://skitterphoto.com/photographers/7/peter-heeling), made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
