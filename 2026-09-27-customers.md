---
layout: post
title: Customers and Righteousness
date: 2026-09-27 12:00:12-0400
categories:
tags: [free-culture, rant, terminology]
labels: [advice, career]
summary: Noodling about what it takes to get things right
thumbnail: /blog/assets/20240928-merchant.png
offset: -14%
description: A quick post on common (not quite) wisdom, and why I might care.
spell: scrollbars lvYNjk Hairic Lilred rTpVbj
proofed: true
---

* Ignore for ToC
{:toc}

As a quick "programming note," this post goes out late, *not* because it came together at the last minute---in fact, as I tried to figure out if I had anything to post, I stumbled across this old draft already written[^Na1qGl] that indirectly talked about other things that I've had on my mind---but because the Nor'Easter has apparently knocked out Internet everywhere, somehow, despite all the alleged preparations they've announced over the past week.

[^Na1qGl]:  I believe that I originally wrote it as a response to somebody on late, lamented Cohost.  I did, however, take advantage of the delay by adding the final section trying to bring this into focus.

Anyway, when the old comment surfaced, it occurred to me that I actually did want to tease out the old wisdom that "the customer is always right."  Anybody who has dealt with an actual, live customer knows that this rarely holds true, because "right" requires understanding business priorities and constraints.

![A D&D-style depiction of a sword-wielder shopping for supplies](/blog/assets/20240928-merchant.png "Can you explain the difference between the rope coiled horizontally and the rope coiled vertically again...?")

However, I'd add a bit more nuance.

## Background

The axiom comes primarily from retail, and notably does *not* actually refer to imagining customers as some sort of omniscient creatures whose every utterance we should document and follow.  Rather, the slogan requires representatives of the company to prioritize customer satisfaction.

Already, this short-circuits most of my post, but that never stopped me before...

In fact, this idea became toxic over the decades since the {% wiki Marshall Field %} days---and notably, people question whether Field or any of his peers ever used that phrasing---because other industries beyond retail picked it up and tried to take it literally.  Customers say something that defies reality.  Bosses call customers "always right."  Workers stop trusting customers and bosses.  Hilarity (bad solutions) ensue.  Organizations replace customer support with chatbots that can far more readily write Python code that adheres to an iambic tetrameter meter or lie about refunds than solve any customer's problem.

I exaggerate some, here, but we've all heard the advice of "firing" customers who have significant problems.  That partly comes from the assumption that companies have *so many* customers that telling a few to go away won't affect the bottom line.  But it also directly falls out of the strain that pretending that customers can't make a mistake puts on an organization, and the rejection of the (wrong) idea.

In other words, hear the words (from now on) as "make the customer happy," and the problem goes away.  That said, I could go further.  I mean, if I couldn't, why would I have this post, right?

## Problems

Customers actually do reliably get something right:  They, better than anybody else, understand the problems that they face.

When a retail customer tells you that the garment feels uncomfortable[^8AmIbO], you don't know better.  When a diner tells you that food tastes off, you don't know better.  And (among others) when a user with poor vision tells you that your website doesn't work with their screen reader, guess what...

[^8AmIbO]:  Let's ignore that, especially in retail, some people will lie to get refunds through.  It not only convolutes the post's idea to no benefit, but it also opens the far more difficult topic of the ethics of cheating a corporation built on exploiting labor...

Problems arise when we take the next step.  The customer thinks that suggesting solutions will save everybody some time.  They definitely don't believe that the person talking to them cares, probably correctly.  They *might* care about the workload involved in helping them.  But in any version, customers will often suspect that appropriating a solution that they saw used somewhere else or quickly making something up that would probably fix the part of the problem that they can see will get them a solution faster.

Let's take my favorite example[^rTpVbj] from my career.

[^rTpVbj]:  I streamlined/adapted some details, since I don't recall whether I got permission to talk about the incident.  It probably doesn't matter much, given how long ago it happened, but you all know that I don't like accidentally outing somebody's role in any incident.

Many years ago, a customer asked my employer's sales team (not trusting support) if we could provide them with the option to change the size of the text displayed on the screen in the software.  Oddly, they specified changing the size of *specific* text, not everything at once.

At a meeting, because something felt wrong, I said something like *we could, but that makes no sense*.  We used native desktop software, back then, but the same would apply to a web application.  It took a couple of exchanges, where they suggested even weirder solutions like scrollbars to *move* text on the screen, but we eventually got the whole story.

Somebody in the pipeline (which involved multiple companies, so I never actually found out how this happened) released a version of our software to this customer site translated to German[^lvYNjk]---translations to German can run about a third longer than the English equivalent---and did such a lousy job of the translation, with so little testing, that the labels for input boxes would stretch underneath those input boxes.

[^lvYNjk]:  Only at this point in the story did I find out that the customers worked in Germany, by the way...

Once we heard that back-story, we all (probably except for the translator) got to share a laugh, because their inane requests focused on recycling ideas that they had seen before, disrupting as little of their conceptual model of the application as they could.  They tried to write a solution and present it to us, in other words.  Because none of them wrote software, though, they couldn't see that those solutions would actually make much more of a mess and take much more time than a bunch of other possibilities.

- Getting more concise translations.
- Letting the labels wrap to the next line.
- Giving the labels more horizontal space.
- Changing the layout of the offending screen for certain translations.

Of *those* solutions, we could hack out any of them except for better translations in the same couple of hours as their scrollbar idea, complete with testing, and it would make *every* customer's work better, rather than patching the single problem for one case and hoping that we never need to do it again.

## Some Quick Overall Thoughts

What I kind of got out of that looks like this.

Customers usually know when you have things wrong, because it affects them directly.  In fact, when I started out on software, we didn't talk about the correctness of customers, but rather that every complaint that we receive represents at least a hundred people who decided that they didn't care enough about the problem to raise it.

Customers don't---*can't*---know the right solution, because they don't and shouldn't have the technical, business, and financial information to work that out.

Some customers do cost too much to chase their money.  Even though you can figure out which customers fall into this category with minimal arithmetic (money in minus time-times-wages out), nobody in charge ever wants to do that calculation, apparently believing that salaries secretly don't break down into hourly wages.

Customers know that costing too much will get them ignored or cut off, so they'll try to make themselves cheaper by proposing solutions that, again, won't work, but they don't know that.  You can probably think of it more as a plea for someone to ask them more about the problem than someone else did, instead of a serious suggestion.

## Why Today

As mentioned, I originally wrote this as a response to somebody's post on Cohost, meaning that I probably wrote it sometime between January 2023 and September 2024[^BEaxW8], twenty-one months ending (yikes) two years ago.  That raises the question of why I would sit on the draft for at least two years.  What spurred its resurrection?

[^BEaxW8]:  Technically, I posted there from mid-December 2022 until the first of October, but the odds that it came up in those sixteen days seems low enough to not simplify the assumptions a bit.

First, as admitted at the top, I did want to continue my streak of Sunday posts, and this seemed fairly complete.  It runs fairly short for a post around here, but (I assume that) nobody comes here *because* I tend to write three-to-five thousand words at a clip.

Also, though, I have started paying closer attention to exactly this dynamic in Free Culture spaces.  For the most famous example at the moment, the Linux desktop environment [KDE](https://kde.org) has had a bad couple of weeks.

As I understand the events---as someone not involved in the community---it appears to have started with a technical dispute in their public communication channels, when somebody pointed out a potential decision's authoritarian-leaning consequences, and pointed out that the more-established person proposing it *happened* to have said a whole lot of authoritarian-leaning things on {% x %} over the years.  KDE's moderation responded by...banning the accuser and locking everyone out of the discussion.  When people continued to talk about it, then set the conversation to something that only moderators could see and cracked down on people talking about it.  Later, they announced that [they banned the offending party](https://raphus.social/@MaddieM4/117320340004129375) with no clarification as to *who* offended them.

In parallel to this, or maybe part of it (as I said, I don't travel much in those circles), deluged by LLM-generated pull requests, someone at KDE "tried to solve" the problem by proposing an LLM policy.  Like every other big organization, they went with the idea that we can't *not* use LLMs to generate code (for some reason), so contributors should only provide *good* LLM-generated code.  That went over about as well as you'd expect, so they took that debate private, too.

Bringing this into focus, the author of the proposed LLM policy couldn't keep his mouth shut and couldn't acknowledge that he made a choice out of step with the community that he serves.  Instead, I won't link to it, but he wrote a lengthy blog post summarizing these same events from his perspective[^VsBG0i], wherein "KDE developers" found themselves under siege by an unruly mob attacking them for toiling away making the world a better place through compromise.  He consistently reminds us that he doesn't recognize the names of the people complaining, which in his mind seems to mean that they don't matter.  The post largely ended with an assertion that we shouldn't see them as "tech bros," because Free Software certainly doesn't have such people---all the times that somebody has changed licenses or thrown in with huge corporations not relevant, I guess---and so we should extend all our empathy to these poor souls burning out because nobody supports them.

[^VsBG0i]:  I'd call it "spin," and it seems to have worked, since I saw plenty of people post it as a vindication of their faith in the project leadership.

If you find the post, I commented with my thoughts, which you can probably guess:  The post positions developers as some elite but also somehow-disadvantaged class, people who demand empathy that they refuse to extend to anybody else, by assuming that we users daring to have opinions harms them and disrupts their important work.  They *need* to move fast and (let LLMs) break things, at least things that other people rely on, for reasons that they can't make clear, but we should all already know anyway.  When something doesn't go their way, they cover up the conflict so that they can do whatever they please in private without public oversight.  In other words, the post tells exactly the tech bro story about how trust fund babies deserve to violate your privacy and enable genocide, because somebody called them nerds once at school or something, and that made them sad and deserving of our pity as they tell us whose messages we have permission to see, but it puts a kinder face on it than Sam Altman doing his weird Droopy Dog impression.

While I use KDE as my example, here, we see it everywhere in the Free Culture space.  I have written before (at length) about the Free Software Foundation narrowing their early licenses to only issues that Stallman personally cared about on his laptop.  You can see it in Creative Commons making sure that we all know that they see training an LLM with anybody's work as Fair Use, but refusing to engage on any LLM usage *other* than training, even though most of it probably violates copyright.  You can see it in all the projects rushing to get their "you can use LLMs as long as you think that it gave you good code" policies, knowing that it undermines the copyright status, the maintainability, and team cohesion of the project, on top of the environmental and other costs.  And you see it (as I hinted earlier) in every project that hears from a user living with some disability who explains that they can't use this or that feature, responding with "we'll put that on the backlog" to never think about again.

We see it elsewhere, too, I know, but I know the Free Culture space better, at this point, and we have more of a voice in fixing that.

All of these initiatives probably started with "the customer is always right" in their hearts---maybe using a different word than "customer," to avoid feeling like a business---took it too literally, and decided that you shouldn't really listen to customers, because they don't understand the constraints.  And because of that logic, they isolate themselves and act like they only have a responsibility to their own interests.

If we want to fix this, I that starts with getting back to the original point of the idea:  You want happy customers---whatever kind of person you have as a customer, because those of you reading here differ from KDE users, who differ from public license users, even if some of us might use all of those---not a debate with them on the merits.  When they have a problem, they *definitely* have a problem.  And if you want people to care about your work, then you need to help those people out with their problems.

* * *

**Credits**:  The header image is *20240928 merchant* by [Hairic Lilred](https://www.patreon.com/hairiclilred/about) (aka Enrico Rossetti), made available under the terms of the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) license.
