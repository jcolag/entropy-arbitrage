---
layout: post
title: Five Years of Entropy Arbitrage
date: 2024-12-08 09:21:05-0500
categories:
tags: [blog, celebration, meta]
summary: Reflections on the first five years of running the blog
thumbnail: /blog/assets/5122978902_81d43e375c_o.png
offset: -15%
description: I consider how this project has gone so far, and where it might go.
update: [
  2019-12-08-greetings.md
]
spell: libre Homestuck Trekkies Webmentions proselint Andromedae letsfix SaaH
proofed: true
---

* Ignore for ToC
{:toc}

Late this past summer, I noticed that the fifth anniversary of [my first blog post]({% post_url 2019-12-08-greetings %}) happened to land on a Sunday, making this post as good a time as any to look back at the blog's architecture, how my opinions on posts have changed, and so forth.  Bear with some navel-gazing, as I talk about some decisions behind the blog, how things have changed, how I expect them to change, and so forth.  Also, it seems worth celebrating the little milestones, too.

![A fifth birthday party](/blog/assets/5122978902_81d43e375c_o.png "I don't actually do birthdays, other than as a pretext to make a big deal about friends, but...")

Funny enough, it looks like Cory Doctorow's [Pluralistic had its five-year anniversary](https://pluralistic.net/) yesterday, completely unrelated.  He ran a post on his favorite of the header images that he put together.  Congratulates to him, too, then.

We'll start with the literal blog itself, the code that powers everything.

## Software

Five years ago, I made the choice to build **Entropy Arbitrage** using [Jekyll](https://jekyllrb.com/), primarily because other static site generators struck me as either too fussy or too unstable in my assessments.  For example, [Gatsby](https://www.gatsbyjs.com/) seemed like a great idea---before the website became an extended advertisement for Netlify, I mean---but in practice, needing to constantly rebuild the data-translation layer instead of having the generator software do that work for me made all my experiments miserable.  [Hugo](https://gohugo.io/) seemed fine, but when they say "fastest," they mean fastest at building pages, not anything that I would actually care about like writing, deployment, or even page-load time.  If you've tried them or others, and they worked for you, accept my congratulations, because I didn't have the patience, whether in setting up a workflow or modifying the style to reflect my original single-page website.

By contrast, I ruled out "real" blog software immediately, meanwhile, because I didn't want to spend my time upgrading and patching software to keep everything secure.  To insert spam or malware into a blog post, here, somebody needs to either gain access to my server to edit the pages or compromise me.  In the former case, the attacker needs to persist, too, since each post should revert any changes that somebody makes to the HTML.

For the most part, I don't regret those decisions.  Through messing around with CSS and plugging into Ruby's infrastructure, I'll admit that some enhancements have taken a *long* time, but I have them.  The lack of security concerns also pleases me, and I have features in my static HTML that I think stack up well against much fancier systems, with a few more in the planning stages.

### Comedic Timing

However, I do feel like this setup has one serious flaw:  I need to make myself available to publish every blog post.  If I used a full blogging platform, then I could schedule all my [developer diary](/blog/tag/dev-journal) and other regular/weekly posts at standard times when I finish writing them, and let the software do the work for me.  Under such a system, I could pre-write weeks of posts and go on a vacation from the Internet, if I wanted.

Instead, if I sleep late, then a morning post goes out late.  If I go out to dinner, an evening post needs to go out before or after.  And if I lose Internet access or get sick, then I have no idea when the post will go out.  I could even forget---and probably have forgotten, considering that I schedule an alarm every morning to remind me---that a post needs to go out.  None of this constitutes a *crisis*, but it does limit me a bit.

Sure, I could probably set up scripts to rebuild and publish the site on the same schedule that my reminders chime to remind me to send out a post, but that feels like too much work, especially when most readers would probably understand if a post went out late.

## Content

Five years ago, I outlined where I thought that the posts might go, slightly abridged, here.

 > - Updates on my (free/libre) projects;
 > - Technical notes, when I learn something handy;
 > - Consolidated versions of my Quora answers on common topics...;
 > - Narrative versions of some of my lecture notes...;
 > - Broad thoughts on the direction of the software industry and maybe free culture;
 > - How things go when I attempt to learn something new;
 > - From time to time, I may point to and discuss a free/libre project that I happen to actually use and like;
 > - The occasional recipe, since I cook a lot;
 > - Notes on things I don't think I've seen other people talk about in any detail; and
 > - Rarely, I might discuss a conventional product or media franchise...worth highlighting in some way.

I find it interesting how that has panned out.

- The [developer diary](/blog/tag/dev-journal) started as weekly updates specifically on [**Bicker**](https://github.com/jcolag/Bicker), then expanded to other projects.
- [Tech tips](/blog/tag/tech-tips) posts still occasionally show up, but more rarely than I expected.  I don't know whether that comes from my not experimenting enough or not realizing that these things warrant documentation.
- [Compiled Quora answers](/blog/tag/quora) have definitely appeared, though less frequently than I expected, mostly because I use them as filler when I want a Sunday post and don't have anything else in the pipe.
- The lecture notes haven't happened, yet, because I've had other ideas for how I might present that information and need time to solidify them.
- I've posted often on the software industry *and* the Free Culture movement.
- The desire to post about my learning projects ended up exposing how infrequently I engage in them, despite the best intentions.
- Other than [Linux]({% post_url 2024-02-18-linux %}) and [Mastodon]({% post_url 2024-10-20-most-mastodon %}) in broad strokes, I've failed to talk about Free Software projects that I use.
- Informal recipes have become an irregular part of the developer diary posts.
- I don't really know what I meant by "notes on things I don't think I've seen other people talk about in any detail."  Maybe I meant current events, which I have *occasionally* dug into, but also maybe not.
- Finally, I've mostly avoided talking about conventional products and media, other than [*Star Trek*](/blog/tag/star-trek), in any depth.  The [monthly newsletter](https://buymeacoffee/jcolag) gets a list of media that I've watched, read, and (occasionally) listened to---originally a part of my new year posts---but not much more than that.

That suggests some possible changes in direction to either rectify those gaps or abandon the ideas.  I'll need to think about the categories in the future.

## Schedule

It probably surprises me most that the blog has turned into a fairly strict regimen.  In my first post, I even outright said that I'd *definitely* publish "on an irregular schedule," even though I liked the *idea* of doing this consistently.  And I actually do prefer the regular cadence, even if it sometimes means that I need to scramble when I've fallen behind on things.  Take this post, for example, where I took this to the eleventh hour, last night, then realized that I should add more when I woke up, leading to this going out so late...

While I always envisioned the [social media roundup](/blog/tag/link-dump) posts as weekly, since they function in an almost procedural manner, I originally imagined that the developer diary posts would go out only when I worked on some specific interesting project, the [Free Culture Book Club](/blog/tag/book-club) would happen whenever I discovered some new and interesting project, and---as I've probably mentioned before---assumed that the [Real Life in *Star Trek*](/blog/tag/star-trek) posts would peter out after probably [*Shades of Gray*]({% post_url 2023-04-20-shades-gray %}).

Instead, each of those types of posts have their own five-year anniversaries coming up in the new year, with only one gap among them, depending on how you count[^1].  Developer diary posts have served to keep me accountable, if only to myself, so they became almost a ritual on my part.  I've found many more Free Culture works (even by the narrower definition that I use for the blog posts) than I would have imagined.  And I now mostly expect the *Star Trek* posts to last at least eight more years if I last that long.

[^1]:  In late 2023, I misunderstood the situation for the **Homestuck** reader software, and so spent three Free Culture Book Club posts on a not-at-all-Free project, soon replacing the contents of the posts with an apology to anybody who I might have misled.  While I did get those posts out on time, since I retracted the contents, I can't realistically count them, so I consider that a gap.

We could look at the existing categories in somewhat more detail, though.

### Miscellaneous Sundays

These posts have remained irregular, since they tend to take the largest amount of original writing and usually a time-sensitive reason for raising the issue.  They also tend to---like this post---run long, which absorbs unlimited time, and the time-sensitivity generally means that I usually can't break the post up over a couple of weeks.  Regardless, I've used the occasion to publish nine short stories, a couple of dozen pieces on politics, about a dozen posts recycling the aforementioned material from Quora, a seven-post series on attempting to change careers to software engineering, and much more.

In a lot of ways, I think of the Sunday posts---like this one---the "real" blog, the posts where nobody (frequently including me) knows what we'll get.  If you really wanted consistent topics, you'd go read some corporate blog, where consistency gives advertisers some reassurance that they can predict the demographics that they can lure in.  Around here, certain other days could give that kind of security, attracting software developers or Trekkies, but over Sunday-way, you might get anything from the Free Culture movement to abortion to translations of obscure fiction, not to mention plenty of anti-corporate jabs.

Given more hours in a day, I'd write a lot more for Sundays.  I want to write posts on how the far right pretends to care about (legitimate) men's issues as a lure for young men who feel lost, but by ignoring the origins of the problems---almost always sexism against women---they turn that energy into faux-solutions designed to make the problems worse.  Or posts about different ways that we might think about trust.  Or maybe looking at the fantasy genre and how we could overhaul the standard tropes into something that feels more fresh.

### Developer Diary Mondays

As I mentioned earlier, while I expected to only track work on specific projects, it quickly started to make more sense to get into everything that I worked on.  That encouraged me to look at more projects, and also to expand my definition of "development" to include little projects like cooking, social media account changes, and probably eventually sewing.

That said, the posts should probably include more code, when I talk about code.  I don't generally find the solutions interesting, since most solutions don't have particularly interesting aspects as much as the work that went into finding them, but the specificity might help somebody down the line.  And explaining "boring" solutions helps keep me accountable in ways that only digging into fun solutions can't.

### Tech Tip Wednesdays

While, again, I haven't published as many of these sorts of posts as I'd like, almost forty of them *have* gone out, covering a variety of topics from scripting to specific APIs and more.

Would I like to push out more tech tips?  Sure.  But that would mostly require me working through some new-to-me problem on a regular basis, and nobody can reliably make that happen.  Alternatively, I could change the criteria and write posts about some idea that I vaguely remember needing to learn about a long time ago, but you can already see where that starts to feel awkward.

### Star Trek Thursdays

This feature, as I mentioned earlier, suffered from scope-creep more than any other category of post, though I believe for good reasons.  My original vision for these posts began and ended with the cast from the original **Star Trek**, because I had the still-stated goal of responding to the people who insisted that **Discovery** went wrong by not showing us their wonderful society so that we could care about Burnham's plight.  I wanted to take the only analogues available at the time and pick at how they portray the Federation, no matter the results, because I had (almost) no idea what I'd find.

As I came to the end of the original show and started moving through the animated series, it dawned on me that I should extend the project through a couple of seasons of **The Next Generation**, considering that the show's origins and a writers' strike led to that era of the show borrowing a lot of material that---like **The Motion Picture**---they originally developed for the never-produced **Phase II** for at least some of the original cast.  After that, I thought, maybe I'd pick up the couple of episodes where an original cast member pokes their heads in (one such post will come out this Thursday as I write this, coincidentally) or gets referenced and wrap it up.

However, **TNG** hooked me, not at all by its quality, but by its stark contrast to the original show.  Where James Kirk might talk about how much progress the Federation has made in his lifetime, and how much work they have ahead of them, Jean-Luc Picard blusters about the perfection of humanity, even while they show us a culture that thrives on racism and sexism, and kids feel under constant pressure to conform or vanish.  Where Kirk regrets that he started his career as a "soldier" and feels embarrassed by the militaristic artifacts of those days, Picard wishes for a war to toughen up what he mostly sees as a decadent (but perfect) society.

Plus, I always suspect that, when people complain about **Discovery**, they mean it in contrast to Picard's myopic monologues set against stirring music, because so many fans think of **TNG** as the core of *Star Trek*, since they grew up with it[^2].  And so those episodes became a part of my project, too, and I now look forward to transitioning over to **Deep Space Nine** sometime next year, then probably (with far less enthusiasm) **Voyager**, keeping these posts going until around 2033, I think---at which point, I suppose that I'll need to decide whether to expand the project again---assuming that nobody disappears me to a black site for enhanced interrogation or the Internet collapses or something similarly grim...

[^2]:  At the risk of providing too much information about myself, I've probably mentioned that I almost literally grew up with the show, in that it nearly coincides with my teenage years.

Important to me, though, if I've contributed nothing more to the conversation, I hope that I've contributed the idea that we can look at the stories without worrying about identifying a "good" or "bad" episode, worrying about continuity, the franchise's reputation, or any of the traditional approaches to the franchise or any other franchise.  I take the stories as units that describe a fictional world, but---and I try to point to these along the way, for somebody else to pick up---we could also look at them as literary works that use casting, literary allusions, historical allusions, and more to give texture to the narrative, or we could look at it as a conversation where every episode responds to something.

### Social Media Roundup Fridays

I don't have much to say, here, that I haven't said before.  The "link dumps" largely exist so that you don't need to follow me on social media to see what I post, and they haven't changed much in structure or content since I started publishing them.

In fact, I can only think of one substantive change, that of removing links to Twitter and moving the "source" posts to Mastodon at the start of 2023.  At around the same time, I changed the already-published posts to point to [my Twitter archive](https://jcolag.github.io/twitter/) rather than {% x %}.

Oh, I suppose that I did make another change to the posts, at least behind the scenes.  Rather than schedule the tweets or toots manually and then compile the post for Friday by hand, soon after the move to Mastodon, I started creating the posts first, and using a script to schedule the posts through the Mastodon API.  That works *far* better, because it means that I only touch the text once, and the headlines and quotes also go through at least the partially automated parts of my proofreading process, weeding out the worst typos and unifying on modern American English in my presentation.

### Free Culture Book Club Saturdays

Finally, the other major project that the blog has engaged in, the Free Culture Book Club has highlighted well over a hundred Free Culture projects.  I count around a hundred twenty posts---or collection of posts referring to the same project---and some posts collect multiple small projects by the same author, if you want better numbers than that.

Of maybe more interest in showing off what Free Culture produces, we've had projects in nearly forty different forms, ranging from micro-fiction to albums to feature-length films.  We've also had action and introspection, realism and surrealism, ersatz versions of mainstream media franchises, wholly original concepts, and mundane slices of life.

Admittedly, I don't always have the energy or insight to give works a fair shake, but I love doing these.  While the Sunday posts feel like the core of the blog, the book club feels like it comes closest to filling a useful role in the world, drawing attention to a specific class of independent projects, making sure to indicate how to get involved with and support the project, and how we might use the project for other purposes.  Many people (especially creators who reach out) confuse the posts with a series of reviews, since my opinions do manifest more often than I'd like, but---at least in an ideal world---I see the posts as presenting projects so that you can tell *me* (and other readers) what you see in them, because I certainly miss a lot.  And maybe I can inspire a few people to take what you find in these projects and build something new, even---or especially?---when the original work has huge problems.

And by the way, I'd like to take the opportunity now to thank the people who *make* Free Culture works.  Sure, I have a bias, but the idea of people making art for other people to build on impresses me enough that I happily struggle to join them and occasionally contribute to the same collective body of work.

### The Week

I should mention that this sort of schedule, despite the surprising load, helps a lot when I feel "blocked."  The posts that require the most insight or inspiration---the tech tips and Sunday posts---need to happen, and for most of them, I can get away with writing them mechanically.  For example, I don't *need* to have something interesting to say about the projects that I worked on or the links that I post to Mastodon.  And at least the "front half" of most *Star Trek* posts reliably take forty-five minutes to watch the episode alongside the transcript, less when an episode frustrates me enough that I find a way to increase the playback speed.  I feel better about the posts when I can engage with the writing, and it presumably reads better, as well, but I can squeak by on those posts with less creativity when I feel drained.

Critically, though, those posts keep me in the habit of writing.  Even if I don't write something *good*, the regular cadence means that I need to get four posts out the door every week with *something*.  When I have a difficult post, that momentum often helps me at least get started.  I highly recommend it.

In a way, I've had to rediscover this idea.  In high school, I took a writing class---AP Language and Composition, if that provides any useful information for anybody---where the teacher had us write, every day, in class, longer papers over time, a randomly chosen topic every day.  He, and maybe the formal class structure for all I know, worked from the philosophy that, if we constantly wrote about arbitrary topics, it wouldn't phase us when we needed to write under pressure.

## Favorite Posts

While I don't want to belabor this in an already-long post, I did want to briefly mention at least a selection of my favorite posts.  I don't necessarily love the *writing*, but they all give some sense of how I'd like the blog to feel.

- [*Bank on It*]({% post_url 2023-03-19-banks %}):  One of my favorite stories of mine, I built on the events of the day to suggest the idea of super-villains creating destruction for the purpose of economic and political sabotage, which almost feels prescient, these days.
- [*Ernest Hemingway's Visit from Saint Nicholas*]({% post_url 2023-12-24-visit %}):  While I didn't write the story, but I find the clash of styles absolutely delightful, and the story's copyright expired.
- [*A Heritage-Based Reading Schedule*]({% post_url 2022-07-03-reading %}):  This post holds a special place in my heart, because I actually refer to it regularly.  Every month, I need to remind myself where I want to source the quotes for my lunchtime Mastodon posts, or what criteria that I want to use to select books to read and sometimes films to watch.
- The too-rare [Let's Fix](/blog/tag/letsfix) post:  I love the idea of taking either a famous media franchise or monopolistic corporation, figuring out the "central truth" that makes it useful, and designing a Free Culture replacement or working out how to force a company to behave.
- [*Real Life in Star Trek, The Defector*]({% post_url 2023-07-06-defector %}):  While not an important or particularly enjoyable episode, it spurred me to talk about the silly idea that we should all find Shakespeare relevant to understanding culture, nationalistic paranoia, the in-universe love of 1970s animation, and the sporadic possible self-awareness by the writers.
- [*Software as a Haunting (SaaH?)*]({% post_url 2023-08-06-code-haunting %}):  I propose an extreme way of thinking about software as something more interesting than an artificial tool.
- [*Superheroes and Race*]({% post_url 2021-03-07-super %}):  In response to the online outrage at the possibility of casting a Black performer to play Superman, I examined why the character makes a lot more sense in that context, due to both his origins and portrayal.
- [*Wanted --- Ethical Media Consumption*]({% post_url 2020-08-02-ethmedia %}):  Here, I talked about how I want a better framework for enjoying media responsibly, in a world where the funding might come from money laundering (and contributions from the military in exchange for script oversight), the director and star may have assaulted people, the studio may have scuttled the presence of gender and sexual minorities, and more.
- [*Why Care about Free Culture?*]({% post_url 2023-06-25-free-culture %}):  I talk about why I have latched onto Free Culture as a cause, and why I'd like it to matter to you, too.

That covers around one percent of the posts, but should help to illustrate the variety that I've gotten to play with.  And like I said, I like a lot of those posts more than others, despite their imperfections and---in some cases---their ages.  Mind you, I have a love-hate relationship with all my posts.  I wouldn't release a post if I didn't think that it *sufficed* and had something about it worth reading.  But when I read it back, I mostly see the imperfections and gaps where I could stand to learn more.

As always, though, I mostly write these posts as a record, not as some showcase of perfection.

## Audience

First, I want to point out one of my favorite images that comes from running analytics, [Matomo](https://matomo.org/), specifically.  I realize that people use VPNs that can account for some of this, but I love seeing where my audience comes from, and the breadth.

![A world map, with most countries shaded in light blue, representing visitors to the blog from that nation](/blog/assets/audience-map-2024-opt.svg "Apparently, I need to talk about middle-Africa more...")

Again, not every visit actually comes from where the analytics claim.  But assuming that the majority works out, then over five years, the blog has probably seen visitors from everywhere but middle-Africa, and that pleases me.  I'd hate to load that map and see that my audience probably looks suspiciously like me[^3].

[^3]:  If you ever wanted to know, whatever my *actual* audience, I generally have two imaginary readers in mind when I write most posts, both younger people.  One looks a lot like I did as a kid, privileged without realizing it, thinking that he already knows how the world works, and needing somebody to point him in a better direction than learning for the sake of learning, with an understanding that things only matter because people matter.  The other, I see as a mixed-race, non-binary kid who more than anything else needs somebody to show that the world can and should do better, and that anybody trying to sell them on despair has an agenda.  I probably don't always succeed in connecting with them if they show up at all and love that other people connect with the posts, but when I think about writing a post as sitting down and looking a small group in the eye, I see those imaginary eyes.

I can't give you overall numbers, because somebody in Iowa seems to have let a script run amok for a while starting in early 2023, skewing numbers by at least a couple-dozen thousand visits that I can quickly identify, plus I regularly see archiving efforts scrape through every page.  But I *can* tell you that, recently, the blog has seen around seven hundred visitors every month, of the people who don't block the script or read through the RSS feed.

Why do I have analytics at all?  I set it up, because posts that get more attention should *probably* get some extra attention from me, double-checking that I didn't get anything wrong or type something incoherent.  When I suddenly see people looking at some older post---and I can only really see that with analytics---I generally (but not always) re-read it myself.  But watching the map light up over the course of a month from the United States, through Europe, and then skip its way on a nearly straight line across Asia to island-hop to Australia and New Zealand also definitely amuses me.

### Community

Before I get uncomfortably analytical, I do want to thank everybody who has contacted me over the years about something on the blog...except for the weirdos who want me to [plant their AI-generated "content marketing" slop]({% post_url 2024-02-11-sure %}) on my personal blog after not having read anything that I've written past the headline, I mean.  OK, and the couple of spammers that came through, and the one bigot who took umbrage at my [support of Asian Americans in media]({% post_url 2021-03-21-asian %}); them, I also don't thank.  I didn't always have the time to reply to you in a reasonable amount of time, but I always appreciate the constructive input or feedback.

Yet here, I can't help feeling like I've gotten things particularly wrong, or don't quite understand what "right" looks like.

### The Debate over Comments

You see, when I launched the blog, I broke with the trend at the time by including a commenting system.  While many insisted that commenting only attracted spam, and that people should reply on social media, I wanted to not only test that hypothesis, but also make sure that any community that formed would remain free of big-corporate interests, such as a petulant billionaire buying an entire site to silence a bot that tracked his private jet.  And so I added the comments section to each page, and eventually added the Matrix room, not to mention the Webmentions that can bridge over from Mastodon.

I aspire to have that community, wherever it takes root, not only because I'd like to have more people talking about these issues to prevent me from talking to myself, but so that readers (who probably have shared interests, if you ended up here) can meet and follow each other, too.

### Minimal Response

And yet, in over twelve hundred posts, fewer than fifty of them have received comments.  That number includes the aforementioned bigoted screed and maybe two spam messages[^4].  I'd call most of the remainder extremely insightful or helpful, which makes me want more.

[^4]:  I don't know whether to feel extremely lucky or extremely isolated that spambots don't see posting here as worth the trouble.  Sure, I deleted the couple of attempts pretty quickly, but that doesn't stop them anywhere else...

Now, it doesn't *hurt* me that almost nobody comments.  I write the blog because I *need* to write (the majority of) the posts, or because I might as well document my work, and my imagined audience---see the footnotes for details---might not exist yet.  As such, the lack of comments won't stop me from writing or publishing.

However, I would like more interaction.  While some posts directly fit the description more than others, I think of the posts as the start of a conversation.  You shouldn't feel obliged to contribute to the conversation, but you should feel welcome to do so, subject to not acting like a jerk and realizing that I need a public license to show your comment on the site.  I especially use the Free Culture Book Club as an example, using the term "book club" to suggest that we get together on Saturday mornings (or whenever you get around to the post) to chat about the work.

Granted, I've gotten far worse at commenting on blogs, myself.  Years ago, I became a regular commenter on a number of blogs, if only as a show of respect to writers who I enjoyed even when I didn't find a particular post interesting---and in hopes of encouraging more people to comment---but it ended up feeling performative and counter-productive, especially when I couldn't think of useful things to say on a regular basis.  Add in my shift to using an RSS feed reader over time, and commenting has felt more like a chore, because I need to click out of my reader to get to the comment area, maybe let the page sit for a few hours if I'd rather not send an immediate reply for various reasons, and I end up not commenting on other people's work nearly as often as I probably should, so getting what I give sounds like poetic license and completely appropriate.

Still, I'd rather the space feel welcoming, and the "hit rate" for comments suggests that I've failed at that.  People have mentioned that the password box implied that you need an account, so I've made it clearer that you only need a name, along with a pop-up that explains why you might set a password.  Along the way, I have also "softened" the requirements with explanations of why I ask those things of you.

I'll need to think more about it.  If anybody has ways that might improve things, get in touch.

### Surprise Guests

I should note that the blog has received a couple of exceptional comments, specifically on Free Culture Book Club posts from the *creators* of the projects covered, doing us all the favor of clarifying aspects that I might have missed or filling in some background that we wouldn't have otherwise known.

One or two have also reached out on social media or e-mail, in some cases becoming a longer conversation where I've gotten to know them, but the public comment makes it available to everyone, without my needing to relay it second-hand.

## Changes and Improvements

In addition to the aforementioned shift in the workflow for Social Media Roundup posts, I've made a couple of changes that I *believe* help.

The automated proofreading, I think, makes the biggest impact.  I generally have enough confidence in my writing and typing that I don't often check my work.  Growing up more pretentious than I should probably admit, at a time when the culture shifted away from formal language, I worked fairly hard at getting spelling and grammar right the first time.  But especially in an all-digital, always-online environment, I can get distracted and miss things.

Therefore, current blog posts go through a scripted gauntlet of checks, including [LanguageTool](https://languagetool.org/), [proselint](http://proselint.com/), [write-good](https://github.com/btford/write-good), and [Alex](https://alexjs.com/), to warn me of spelling, grammar, style, and sensitivity issues.  [Vale](https://vale.sh/) had a place on the list for a while, too, but it gave too many false positives and almost no new information.

Problems still slip through, because I can always make a mistake, but this process at least gets me past the worst problems.

Likewise, as I discussed in my post on [specificity in language]({% post_url 2022-12-04-specificity %}), I've worked to reduce my usage of forms of the verb *to be* in writing, because using the same word for identity, analogy, subset, existence, ambience, passive voice, status, and more feels confusing once I started thinking about it.  While I've tried not to take this to a pathological extent, the reduction has led me to eliminate passive voice entirely, I think, while also making it clearer what I mean; we can take a quick look at some examples of the clarity.

- People call me John.
- The Empire State Building stands 102 stories tall.
- The sky looks blue.
- I feel happy.

Occasionally, the grammar comes out sounding contrived as I try to work out how to best present the idea without the crutch, but I also think that I've gotten better at making it sound more natural.  Usually, this happens---and I should take that as a bigger lesson---because I have an urge to lazily swap in a more specific verb, whereas I actually need to reorganize the thought.  For example, in that appositive phrase in the last sentence, I considered "that should make a bigger lesson" as a drop-in replacement, but changing the subject provides a better selection of verbs.

Again, I don't want to go down the obsessive route, so I don't try to squeeze out every last use, but I do think that (when I get it right) it makes reading and probably translation far easier.

Oh, finally, I also let up on the pull-quotes.  While I like how they can help draw the reader back to a key passage, they can also feel intrusive and a *bit* pretentious to think that I know where I put the best ideas.

## The Future

I'd like to end this on some grand scheme for what I expect to do with the blog over the next five years, but in reality, the actual plan for the future looks a lot like *making* that plan, rather than executing it.

Like I said, I definitely want more posts about tools---particularly Free-licensed---that I appreciate.  I also definitely want to get into the habit of "learning in public," if only because it'll spur me to actually learn at least a couple of the things that I'd like to learn.  And I'd like to make this more of a community, where you might not even need me to spark a conversation.  But I need to consider how best to do those things, both in broad concept and actual implementation.

Some of those ideas will probably require software, while others "only" require a commitment.  And I don't necessarily know which fall where on that spectrum.  But I probably have five years before the next time that I'll feel tempted to do another retrospective like this, so we'll see how it goes.

Again, thanks so much to everybody for reading!  And I can only hope that you continue to think of the posts here as worth your time.

*- *

**Credits**:  The header image is [Stefan's fifth birthday school party](https://www.flickr.com/photos/35261188@N00/5122978902) by [Upsilon Andromedae](https://www.flickr.com/photos/upsand/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
