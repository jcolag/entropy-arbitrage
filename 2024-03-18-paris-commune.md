---
layout: post
title: Developer Diary, Paris Commune
date: 2024-03-18 07:41:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Paris-Commune-barricade.png
offset: -15%
teaser: This week's projects include Notoboto, mostly.
spell: Notoboto sup Spoutible Bridgy Webmentions Fýlakas Onomáton Scuttlers Slackup
proofed: true
---

Today marks the 153<sup>rd</sup> anniversary of the [Paris Commune](https://en.wikipedia.org/wiki/Paris_Commune), a revolutionary government that took control of a lot of the city for more than two months.  People didn't look particularly kindly on them, often complaining that the uprising broke the peace of society.  And predictably, communist governments since have pointed to the failure of the commune as reasons to act in a totalitarian manner, particularly the Khmer Rouge.

![A barricade protecting the Paris Commune](/blog/assets/Paris-Commune-barricade.png "Do you hear the people---no?  Another different aborted revolution...?")

And on that downer, let's move onto the projects as quickly as we can.

## Social Media

While I haven't seen any evidence either way, I suspect that I may not get any use out of my [Post.News](https://post.news/@/jcolag) or [Spoutible](https://spoutible.com/jcolag) accounts for much longer.  Both sites have stopped sending out behind-the-scenes newsletters, *and* both seem to have absurd technical problems.  Post takes forever to...well, *post*, these days.  Spoutible usually won't show the main feed, and sometimes won't open the box to post, either.  Issues like that, especially combined with the silence, don't bode particularly well...not that I spend much time on either site, after posting my blog announcements.

Oh, and meanwhile, [Cohost](https://cohost.org/jcolag) announced that [they could run out of money as early as next month <i class="fas fa-copyright"></i>](https://cohost.org/staff/post/5023717-march-2024-financial), though they have no plans to shut down, yet.  But given that they see an acquisition as a viable and realistic alternative to shutting down, it may go down a bad road, soon, too.  **Update**:  Over a few days, [an outpouring of subscribers has put off their crisis <i class="fas fa-copyright"></i>](https://cohost.org/staff/post/5101727-end-of-week-financia) for a few months, which should remind each of us to *pay for* the independent work that we want to keep around.  As the [Hillel](https://en.wikipedia.org/wiki/Hillel_the_Elder) paraphrase goes, if not you, then who?

You'll notice that I still don't list Threads or Bluesky as places to contact me.  Both require mobile apps to sign up, and I absolutely will not do that until I have no other options for communication...

Anyway, we could soon see a scenario where I only post to [Mastodon](https://mastodon.social/@jcolag/) and [Diaspora](https://nota.404.mn/people/e4313920967a0136074b076893c08a76), which feels on-brand for me, but also saddens me that the "alternative social media" space may not last much longer, reconsolidating under precisely the two billionaires who controlled it a couple of years back, though with a stronger Fediverse stalking them.

As a side-note on this situation, I do need to point out how much I appreciate the Cohost team's transparency, here.  I've watched companies try to hide their financial dangers as long as possible, even missing payroll cycles and hoping that their employees wouldn't notice, before needing to shut the doors.  While announcements like this attract a lot of garbage people who want to see things fail, it also gives users enough insight to make reasonable decisions.

Anyway, in happier and more relevant-to-the-blog news, I'll have more about this in Wednesday's post, but over the weekend, I connected the blog to a small service---[Bridgy](https://brid.gy/)---that connects certain social media sites to the Indie Web.  In short, from now on, if you engage with my blog announcement posts on Mastodon, you *should* see the results on the blog post that the announcement refers to, slightly above the comment box on the page.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

I haven't had the time to clean up the code to commit it.  However, if you read my [first post on Indie Web technologies]({% post_url 2024-03-13-indieweb-1 %}), then you know that I put a lot of work into making the blog more "social," last week, as I saw the proprietary-but-independent social networks dry up, discussed above.

I'll roll the changes out "officially" in the coming days, and so you'll see some repetition in next week's post, but so far, pages now identify me as the author and owner with a social profile---if you look for the `h-card` microformat, you'll find it---and should display any Webmentions that people send based on my posts.

Alas, it *does* have a pretty serious downside:  It now takes an astonishingly long time to publish blog posts, long enough that I stopped the deployment *twice* for Thursday's post, thinking that it broke down, especially when my Internet connection also had problems.  I can see this becoming frustrating, if I can't speed this up or if no Webmentions actually come in for all the work.

Even so, as mentioned on Wednesday, I intend to keep pursuing the various Indie Web protocols.  While I realize that not everybody has the capacity to casually get involved on this sort of level---domain names cost money, even if cost nothing else did and took no time to set up---it would also please me greatly if conventional "social media" mostly went away entirely, replaced by personal websites with enough features for people to connect.  I'd also happily accept a scenario where a network like the Fediverse integrates the Indie Web protocols, but I realize that feels like more of a stretch.

## Library Updates

I needed to bump library versions for [**Bicker**](https://github.com/jcolag/Bicker), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), the [**Little Scuttlers**](https://github.com/jcolag/LittleScuttlers), the [**Renewal Database**](https://github.com/jcolag/RenewDB), [**Roku Wake**](https://github.com/jcolag/RokuWake), and [**Slackup**](https://github.com/jcolag/slackup).

## Next

I still have a couple of library updates left to clear out.  Then, I need to---as mentioned---clean up and commit the various changes to the blog, then deal with some of the nagging problems that the last few days have caused, and I should probably style the inbound Webmentions.  And I also need to get back to **Notoboto**, because I have some interesting ideas to play with, there.

Oh, and relevant to the Indie Web work, I *may* start a new (small) project, on top of everything else.  We'll have to see if I have time for that.

* * *

**Credits**:  The header image is [Barricade 18 March 1871](https://commons.wikimedia.org/wiki/File:Barricade18March1871.jpg) by an unknown photographer, long in the public domain due to an expired copyright.
