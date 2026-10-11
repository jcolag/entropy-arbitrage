---
layout: post
title: Stack Overflow Survey Results
date: 2026-10-11 07:51:12-0400
categories:
tags: [rant, stack-overflow]
labels: [artificial-intelligence, free-culture]
summary: Another Free Culture establishment spins its self-inflicted decline as triumph
thumbnail: /blog/assets/Human-grinder.png
offset: -26%
description: Everybody still taking the survey agrees, you say...?
spell: k_fBbb Lemmy borderColor fillColor GqcPhw Lupton
proofed: true
---

<script src="/blog/assets/chart.js"></script>

* Ignore for ToC
{:toc}

{% cw The more that I have thought about this post, the more it feels conceptually incomplete, something missing that I can't identify.  The analysis (and the laugh at an expense of a company going to seed) still feels worthwhile---otherwise I'd let the post sit for a few more weeks---but I have the sense that the numbers tell me something else.  If it seems somewhat aimless, then, I may end up returning to finish the topic when I figure that direction out. %}

![A (painted) profile view of a person fed into a meat grinder, with pink pixelated extrusions coming out the front](/blog/assets/Human-grinder.png "Fair Use")

Longtime readers might recall that, late last spring, I had a brief and somewhat grim [laugh at Stack Overflow 2025 Developer Survey]({% post_url 2025-06-08-ai-wish-list %}#abandon-hype-all-ye-who-enter-here).  In particular, I don't recall the specific questions, but it seemed to have a specific agenda looking to nudge the results.  Imagine some more professional version of this.

- Do you use generative AI in programming?
- How much do you use generative AI in programming?
- How much do you enjoy using generative AI for programming? [Quite a bit] [Tons] [I love it more than my family]
- Do you vibe-code?
- How much vibe-coding do you do?
- How much do you enjoy vibe-coding? [Quite a bit] [Tons] [I love it more than my family]
- Which of the following benefits do you expect to see from generative AI in programming over the next year?  Select at least three.

Again, I exaggerate a bit, but I (along with many others) came away with the impression of sloppy repeated questions, possibly in hopes of rigging the results, and an assumption that everybody loves LLMs, and we only need to know the degree for precision.

As such, when the announcement came out for the 2026 survey, I dutifully ignored it.  For about a decade, the survey felt worth participating in, because it attracted a wide group of developers, and so the results gave a useful-if-incomplete view of the industry.  But if they primarily care about giving the impression of a groundswell of affection for LLMs, then it seems absurd to lend respectability to it.  And so, after deleting the announcement, I forgot about it.

## Today

Fast-forward a couple of months, and they have officially released the [2026 Survey results](https://survey.stackoverflow.co/2026?lid=ygol0r1ztb33), and...it seems incredibly silly.  For example, let's start at the top.  In every year that I can recall, the results start with an overview of the breadth of respondents, including gender, age, experience, type of educational background, and more.  This year?

> More than 30K technologists from 169 countries have shared their thoughts with us, and now it’s time to share everything we’ve learned with you.

Also, thirty-one thousand---thirty thousand, nine hundred three, if precision matters---technologists sounds low to me, reminding me that I saw a [quick post on Lemmy](https://lemmy.ml/post/53289907)[^k_fBbb] showing that Stack Overflow's question traffic has declined precipitously since a spike during the COVID-19 lockdowns.  We'll return to this later.

[^k_fBbb]:  If you haven't had reason to check it out, [Lemmy](https://join-lemmy.org/) runs on ActivityPub---the same communications protocol that Mastodon and company use---but has more the shape of Reddit.

Anyway, what do they admit to asking, this year?  While they apparently asked a hundred three questions, they let us know about only the following results.

### Smile

About a third of participants have low job satisfaction.  They sneak AI in here, without indicating how it impacted the results.

It seems weird, with all the high-profile layoffs, that they don't mention anything about anybody who might consider themselves unemployed or under-employed, and whether that has any correlation with job satisfaction.

### Gig Economy

Freelance and self-employed workers have jumped from four to over ten percent.

They frame this as "finding freedom"---exactly like Amazon, Uber, and so forth claim that their ~~employees~~ *independent contractors* do what they do for freedom, presumably the freedom to get under-paid with no security---and not begging for scraps as the global economy tanks from over-investing in LLMs.  Notably, despite not substantiating their claim, they do take pains to quote the current Stack Overflow CEO claiming that this shift comes from agents making everybody a CEO or some nonsense.  His opinion apparently trumps the experience of the survey participants, calling into question why you'd even run the survey if you trust this guy's instincts so much.

Meanwhile, despite these extreme conclusions, they literally only show results for the number of people at companies.  *That* tells them everything that they need to know about freedom, I guess.

### Won't Somebody Think of the AIs

People love AI, they assert.  Gosh, I wonder if that has anything to do with all the people who *don't* love LLMs angrily walking away from the survey last year...

People trust AI if they can verify the results.  Maybe weird---not to get too personal---but in my own life, I simplify "trust after I have confirmed everything myself" to *not trusting*.  Apparently, the fine folks at Stack Overflow see a big difference between those two situations.

People want AI to cite its sources...for what it fabricates, I guess.  Presumably, this feeds into the trust-but-verify tripe.

### Languages

Most people use Python...for AI.  Somehow, this matters, I guess, even though LLM people keep telling us that they don't even look at the code.

Most developers work in SQL, JavaScript, and HTML/CSS.  {% emoji exploding head %}  Gosh again.  Do you think that these results have anything to do with the fact that you can't build most web apps without an interactive web page and a database?  As in, maybe SQL, JavaScript, and HTML/CSS get a lot of attention, because you can't get much accomplished on the web without them.

They also throw a bone to Python and "any shell script."  Look, I haven't spoken to *every* developer, but I assure you that nobody who cares about this survey sees the different shells[^Wz6Hhw] as interchangeable.  Hell, if you go to Stack Overflow to ask a question about a shell script, then you *probably* specifically came to ask about the differences between shells.

[^Wz6Hhw]:  For the Windows-only people reading along, think of the difference between the default MS-DOS-style command prompt (`cmd`) and PowerShell as analogous to what I mean, there.  They look similar and have similar ways of interacting with them, but they diverge wildly after some superficial examples.  Nobody with experience would lump the two together in the same programming category.  The UNIX-style world---such as Linux, Mac, and so forth---has *dozens* of such shells that a person could use, and some (like PowerShell) have narrow purposes.

These sections disappoint me the most, by the way.  In the past, they largely made the technology questions the meat of the survey.  They'd ask what people used recently, what they hope/plan to use in the upcoming year, and what they hope/plan to never touch again.  When I say that it gave a good look at the industry, I mean questions along those lines, seeing where "my peers" planned on putting their attention.

### World-Conquerors

Almost nobody uses LLMs to replace third-party libraries and tools.  This feels like it warrants a lot more depth.  If you want to push the idea that ~~thirty thousand hangers-on~~ *developers in general* love AI so much, then why don't they use it to replace pesky vendors?  And if it doesn't happen, then surely we'd all want to know the reasons.

We then get echoes of last year's shenanigans with seeming repetition to lead the witness, except that this time, it flops.

- Even these pro-LLM people search for answers on the Internet.
- They also talk to colleagues, with "ask an LLM" not even among the approaches to finding answers, again, for a largely pro-LLM group.
- "Nearly two-thirds of developers rely less on Stack Overflow for straightforward questions due to AI, with 29% asking fewer questions overall."

Note that "due to AI" feels like it does a lot of work in that last one.  Does it mean that those developers---who previous questions seem to suggest do *not* actually ask LLMs their small questions---direct their questions to the LLM of their choice, meaning that they lied on the other two entries, or that the LLM-written content on Stack Overflow and the LLM-guided destruction of search engines driven them away from asking questions there?

### Context

Developers can't get the context of projects, tautologically, because they don't have it.  Seriously, they dress their assertion up by dividing it into not completely provided, in someone's head, outdated, and so forth, but they all mean that they don't have the context because they don't have the context.

Developers *sometimes* get the context for a task after finishing it.  I don't even know how to respond to this.  How do you consider a task complete without knowing the context?

Note the picture that this paints of the industry, that disinterested developers hand off tasks that they don't understand to LLMs---maybe believing that it makes them feel like CEOs---and then check later to find out how it connects to the rest of the world.  No wonder two-thirds of them report satisfaction with their jobs:  They get paid to copy and paste between windows.

### Back to AI

Less than a third say that "the accuracy of AI answers is important to the adoption or expansion of AI tool use."  If only someone had painstakingly explained this every time we got another sales pitch for this garbage.  Oh, everybody explained that, and the companies ignored us because "adoption and expansion of AI tool use" seemed more important to them?  Gotcha.

### Back to Context, for Some Reason

They revisit where people get context---people who apparently don't do that, remember---and we find out that they look at code and documentation.  Wow.  Thanks for clearing that up, Stack Overflow.

### In a Hole

I should note that each of their "insights" has a *Dig Deeper* link, which shows exactly the same data with no actual further depth.  At the bottom of the results, they have links to what may or still may not represent the specific questions, which often don't provide any more detail and don't provide any path to their headlines.

They also apparently buried some insights that seem important, like "only 23% of respondents have used security tools in the past year."  Or maybe they saw it as only coincidental to the fact that "Security and privacy issues caused 24% of teams valuable time in the last year."  Or maybe whoever wrote this dozed off, because I can't parse that latter factoid beyond seeing a similar percentage of people with a security problem.

And again, notice that they don't supply demographic information *anywhere*.  We keep hearing that the burden of AI usage falls on women.  We keep hearing that LLMs have resulted in cutting back entry-level positions.  You would think, then, that Stack Overflow might find it interesting to compare the existing studies to their loyal fans.

## Yesteryear

Anyway, by the time that I got to the bottom of the page, I still wondered about the "thirty thousand technologists," so I took them up on their offer to look at prior years.  And...I love this.  The link to the 2025 survey goes to the *2026* survey, the same page.  Links to the surveys for 2021--2024 all return Not Found (404) errors.  Now the weird phrasing, the strange omissions, and so forth maybe start to make sense:  Did a human participate in this analysis at all?  Maybe they let ChatGPT extrude this while they all imagined themselves as CEOs.

Anyway, the link to [all surveys](https://survey.stackoverflow.co/) *does* work, though as I write this, the page still doesn't include the 2026 results, making this a pretty liberal definition of "all."  And yeah, I think that I had a right to feel suspicious about that initial introduction.

{% chart L8ee5n|A chart showing the Stack Overflow survey respondent numbers by year; it ramps up steadily from 2011 to 2018, plateaus or dips until 2023, and declines from there|463|{
  type: 'line',
  data: {
    datasets: [
      {
        label: 'Stack Overflow Survey Participation',
        data: [
          2532,
          6244,
          10000,
          7500,
          26086,
          56033,
          84000,
          100000,
          90000,
          65000,
          80000,
          70000,
          90000,
          65437,
          49000,
          30903
        ],
        fill: true,
        borderColor: '#49281b',
        fillColor: '#49281b20',
        tension: 0.1,
      },
    ],
    labels: Array.from(Array(16).keys().map((y) => y + 2011)),
  },
  options: {
    responsive: true,
  }
} %}

They got *2015* levels of participation, this year, not 2017--2024 levels.  And I can't help noticing the similar angle of decline now to the site's rise to prominence fifteen years ago.  Combine that chart with the number of questions per year, and you could get the impression that Stack Overflow might only exist as static mirrors of the content by 2030 or so.  It looks like even the [core community has started to panic](https://meta.stackoverflow.com/questions/438596/stack-overflow-is-becoming-a-ghost-town-now-what), with usage data that reflects the survey participation data.  If we see the participation drop to around ten thousand developers next year, we'll know, I suppose.

Anyway, ignoring that their results represent an even narrower slice of the industry than it has since the survey's earliest days---their numbers haven't dropped to four digits, yet, but the number of developers has increased dramatically since 2011---this also shows the loss of the demographic questions, as well as questions about what technologies people look forward to learning or retiring, the pieces that actually give you some insight into the industry.

It doesn't look like they care about any of that anymore, and I wonder how much that has to do with not wanting to burst their AI bubble.  If you give a pro-AI survey and not only do most people ignore you, but the people who do respond all come from a similar cohort, then *maybe* that says something about the direction of the industry that you'd rather not have people worrying about.

## Something Overflowed

Or maybe they've turned Stack Overflow into a community for a Certain Type of Guy, as social media sometimes likes to interrogate.

I point this out, because so much of modern Stack Overflow looks like a parody of its prime.  Years ago, they eliminated what I'd consider the most usable job board out there, and after years of watching every other job board get far worse without that anchor, they tried to bring it back, but as nothing more than a specialized Indeed search.  Years ago, they ditched their "Developer Story," really a different résumé view, and now after demonstrating that you can't trust them to keep exactly this sort of thing running, and with a declining user-base, they have brought the Developer Story back as if that'll fix everything.

They have fired moderators who asked for more transparency.  While complaining that LLMs have eroded their community, they launched a chatbot.  I could probably dig up another dozen self-inflicted wounds without much trouble.

## One of Many

It seems notable that Stack Overflow seems to have pioneered the playbook, here, of an organization positioning itself as a pillar of Free Culture (or Free *Insert-Your-Specific-Cultural-Thing-Here*) choosing to publicly destroy itself in a way that harms as many bystanders as it can.  Honestly, I probably wouldn't bring this survey up if the story didn't remind me of Linux, Debian, Fedora, and KDE all trying to find ways to accept LLM-generated "contributions," Creative Commons[^GqcPhw] and the FSF refusing to stand up for LLMs plagiarizing the work of their license-users (while refusing to engage with their Jeffrey Epstein connections), the OSI rushing to accept licenses specific to LLMs as Open Source (while refusing to engage with their election tampering), and so forth.

[^GqcPhw]:  It looks like Creative Commons even still wants to push their "what if artists *asked* giant abusive corporations to act nicer" Signals framework...

And it also seems like Stack Overflow shows that this strategy doesn't work, at least of they expect their actions to expand or strengthen the Free Culture and adjacent movements...

* * *

**Credits**:  The header image is [Human grinder](https://betterimagesofai.org/images?artist=DeborahLupton&title=Humangrinder) by Deborah Lupton, made available under the terms of the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) license.
