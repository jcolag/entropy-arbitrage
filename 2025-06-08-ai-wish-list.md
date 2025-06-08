---
layout: post
title: Generative AI Wish List
date: 2025-06-08 08:07:12-0400
categories: 
tags: [artificial-intelligence, harm, rant]
summary: More noodling around AI, but this time pretending that it could work
thumbnail: /blog/assets/43267970922_cb9d7c274b_o.png
offset: -41%
description: Thinking about the things that large language models could plausibly do, if companies cared.
spell: GGUF Deepseek Prolog SHRDLU janky deepak
proofed: true
---

I've made no bones about my feelings on the current corporate obsession with generative AI.  Even ignoring the [intellectual property {% cc %}](https://www.telegraph.co.uk/business/2024/01/07/openai-warns-copyright-crackdown-could-doom-chatgpt/), [environmental](https://theconversation.com/power-hungry-ai-is-driving-a-surge-in-tech-giant-carbon-emissions-nobody-knows-what-to-do-about-it-233452), [intellectual health](https://www.microsoft.com/en-us/research/wp-content/uploads/2025/01/lee_2025_ai_critical_thinking_survey.pdf), and other harms from the technology, or its propensity towards completely fabricating "information" to always have *something* to say, we still have a technology that oligarchs want to push so that they can have a [weapon against the labor movement](https://pluralistic.net/2025/03/18/asbestos-in-the-walls/#government-by-spicy-autocomplete), because they hate and live in fear of the idea that workers can walk out and shut down their companies[^1].

[^1]:  Capital hates competition.  Facebook all but went down a [checklist of anti-competitive behavior](https://www.ftc.gov/legal-library/browse/cases-proceedings/191-0134-facebook-inc-ftc-v-ftc-v-meta-platforms-inc), including (but not limited to) buying potential rivals, working to lock users into using their systems, blocked potential rivals from entering the market, and manipulated prices.  Amazon [forces vendors to raise prices everywhere else](https://www.courtlistener.com/docket/67828404/federal-trade-commission-v-amazoncom-inc/), also [buys out---or destroys---potential rivals](https://en.wikipedia.org/wiki/Diapers.com), uses its metrics to [clone popular products](https://www.govinfo.gov/content/pkg/CHRG-116hhrg39840/html/CHRG-116hhrg39840.htm), and manipulates search results to push customers to spending more money on either their in-house products or whoever pays to play.  And they come up with the most [twisted logic](https://theconversation.com/cultural-industries-have-been-captured-by-billionaires-a-new-book-considers-what-we-can-do-about-it-193838) to convince us that their monopolies actually help us.

![An overly dramatic diagram depicting artificial intelligence as an androgynous humanoid face in the stars, whose head balloons out into a constellation spilling off the image](/blog/assets/43267970922_cb9d7c274b_o.png "And yet, none of those solar systems knows how many rs that you find in strawberry.")

And yet, sometimes I'll use the things.  Other than the basis for a couple of early header images that I mostly regret, I don't think that I've used any of the concrete results, but I do occasionally use the monstrosity for ideas, when I've exhausted other low-effort avenues.  I usually regret those interactions, too, but it comes up with something novel often enough for me to occasionally use it to help quickly visualize an idea or gin up some goofy alternatives to a mediocre idea to flesh out if I like them.

Call it one of my few guilty pleasures, if you must---normally, I don't feel much guilt for only *enjoying* things---but I would absolutely like software that could handle the parts of any project that don't require much thought, so that I can spend my time when it'll make a bigger difference.  I don't believe that software can ever become intelligent, but I've seen time and again that software *can* organize, plan, and analyze systematically.  As such, I want to spend some time talking about the direction that I wish this fad would take before the insipid bubble bursts.

I present these in (probably) no particular order.

## Consent

I know.  I said that I'd ignore the intellectual property costs in that introduction.

While I'll continue to ignore the others for the sake of this argument---though I'll point out that, once you have a model trained, a developer *should* have the understanding and tools to turn those weighed pseudo-neurons into less-wasteful code, given enough time[^2], and these companies should absolutely do that, too---it seems worth pointing out a new development.

[^2]:  It doesn't seem worth getting into it, here, but in short, a neural network---such as a large language model---really only takes input and performs a series of large matrix operations, using the weights as the matrices.  Therefore, a hypothetical compiler could take a model in some standardized format such as [GGUF](https://en.wikipedia.org/wiki/Llama.cpp#GGUF_file_format), turn the weights into direct matrix calculations, optimize them, and output to something like C++ or Rust.  It'd still require vector processors like GPUs, but significantly less of it.  I suspect that we only don't do it because the industry has its [pseudo-mystical dreams of emergent intelligence]({% post_url 2024-02-25-ai-doom %}), which demands that they keep up the charade of LLMs doing incomprehensible things as a step towards general intelligence.

Earlier, I linked above to OpenAI whining that they can't survive if copyright law restricts them.  Former Meta executive [Nick Clegg said pretty much the same thing {% cc %}](https://www.theverge.com/news/674366/nick-clegg-uk-ai-artists-policy-letter).

And yet, earlier this week, a team of researchers released the [Common Pile](https://arxiv.org/abs/2506.05209), data downloaded from sources friendly to unrestricted reuse, with those sources given clear attribution.  In other words, they've given the AI industry yet another black eye, not long after the [Deepseek](https://theconversation.com/deepseek-how-chinas-embrace-of-open-source-ai-caused-a-geopolitical-earthquake-249563) release[^3] showed them up while they explained that they [needed *all* the electricity](https://theconversation.com/tech-bosses-think-nuclear-fusion-is-the-solution-to-ais-energy-demands-heres-what-theyre-missing-240580) to innovate.

[^3]:  And, as a quick aside, that blow from China came not long after Silicon Valley needed to abandon Web3 *and* virtual reality as pretty much worthless markets that they spent billions trying to jump start, and [quantum computing might actually follow suit {% cc %}](https://spectrum.ieee.org/quantum-computing-skeptics).  Why does anybody still take these clowns seriously when they either lie or pour money into ideas that nobody wants?

Regardless of making the technology sector look like a bunch of fools and grifters, though, we've now disproven that AI requires mass violation of intellectual property law, and so it feels like I can put that on the table as something that I want...

## Abandon Hype, All Ye Who Enter Here

No, I don't mean the hype from every direction telling us to get on-board with AI before we get left behind.  I mean, yes, I want to get rid of that, *too*, but...actually, let's talk about this first.

During the week, I took this year's [Stack Overflow Developer Survey](https://meta.stackoverflow.com/questions/434080/the-2025-developer-survey-is-now-live), and quickly noted their pro-AI bias.  Something like a quarter of the survey talks about using AI for development, bad enough, but also structures the questions in such a way that presumes it already knows the answers.  Do you use AI in programming?  No.  How much do you enjoy using AI in programming, on a scale of "a lot" to "over the moon"?  Do you like vibe coding?  What benefits do you expect to see from AI in the near (and totally not fictional) future when you use it for all programming?  Why do we even have human programmers, anyway?  And so on[^4].

[^4]:  Assuming that this doesn't tank Stack Overflow's credibility to the point where it moots my choice, I probably won't participate in the survey in the future.  Even if I no longer use the site itself, it has previously felt worth filling it out to help get a better idea of the industry's direction.  If they can't even do that, though, it becomes a waste of time.

Also during the week, Wikipedia asked me---I did some minor editing about a decade ago, so I register as an "editor"---to take a survey on part of their [AI strategy](https://meta.wikimedia.org/wiki/Strategy/Multigenerational/Artificial_intelligence_for_editors), specifically around the prospective user interface for creating and managing AI-generated summaries of articles.  Short version, it looks like they'll keep this under human control, with summaries generated once on-demand, then hand-edited, and the ability to pull the plug wiki-wide for various reasons, but also...they really should build the summaries based on [Simple English Wikipedia](https://simple.wikipedia.org/wiki/Main_Page), where you *need* careful summaries that strip everything down to the minimal points in a "language" amenable to translation, which I indicated on the survey multiple times.

In other words, the AI hype has grown so pervasive, that two frequently referenced repositories of important information have a position indicating that we don't have any choice, here.

## I Meant the Other Hype, Though

When I talk about getting these systems to abandon hype, though, I didn't actually intend to talk about the external marketing side.  I actually wanted to talk about the hype *from* the chatbots themselves.

If I ask a question about the hypothetical design for a programming project, I can almost guarantee two things about the answer will annoy me.

- The answer will cram a blockchain in, somewhere.  Apparently, only one means of distributing control exists, and it doesn't so much distribute control as demand that every participant makes a full copy of the data.
- It will cheerily offer to write code for the project---ignoring that it only ever gets the code right accidentally, because it doesn't care---pushing [Python](https://www.python.org/) as apparently the only programming language worth considering.

The latter seems particularly galling.  If I (always regretting it later) ask how to idiomatically handle a situation in Ruby, JavaScript, Rust, a shell script, or whatever, it'll often suggest rewriting in Python with the same cheerful demeanor.  I mean, *sure*, why not rewrite hundreds or even thousands of line of code in another language so that the inept chatbot can draw on more training data to get the answer wrong with less effort.  I sometimes wonder if OpenAI et al get a commission every time they plug Python...

I've often described these LLM chatbots as the intern assigned to your team whose uncle "coincidentally" owns the company.  It doesn't care how much damage it does or respect the decisions that you've made, because it fully expects to become your boss's boss as soon as it doesn't feel like a purely political move.  "You should rewrite this using the system that I like" fits right in with that mentality.

## Warn of Dangerous Patterns

Since people started talking about neural networks and machine learning again, after decades of mostly ignoring it except for specific tasks, this has seemed like a slam dunk, but nobody with the resources to do it seems interested.

You see, traditionally, the big impact of neural networks comes from classification.  For example, optical character recognition uses a neural network that takes a series of jumbles of pixels and (notionally) places it on a multidimensional chart where the training carved out spaces that represent each letter or other character to work out the best match.  We have plenty of these classification-based systems.

It seems natural, then, for my "coding assistant" to look at my changes and classify some of them as "usually, when people check in code like this" (whatever "this" means, based on their training), "somebody fixes it with a profanity-laden commit message soon."

We could extend this to text, too.  "You know, a lot of writers who have used this phrasing have changed it in later editions.  Maybe you should double-check that it doesn't show insensitivity."

Instead, we get a situation where the AI does the work that has a low value (I can find people to write code cheaply, if I need to) and it doesn't do well, while the analysis now becomes mandatory, because I can't trust the chatbot to produce code that compiles, let alone has any durability as it encounters errors or new requirements.

## Search for Errors

Again, this comes from what nearly had thirty-plus years ago.

Way back when, the "serious" AI, the kind that tried desperately to get the same sort of hype that this iteration gets, ran on [Prolog](https://en.wikipedia.org/wiki/Prolog).  The so-called logic programming languages distinguish themselves by having (for lack of a more consistent and comprehensible term) an *inference engine* that tries to build a path of relationships from what you supplied in a database to some subset of the data that will answer your question.

In the 1990s, then, people started suggesting that we could apply that same sort of technology to software testing.  After all, how do you test software?  You start with a hypothesis, usually something that applies frequently, such as "this could have a buffer overflow error."  You then test that hypothesis, and use the results to generate new hypotheses.  With "understanding," such as having a framework for those tests and analyzing the results, you can probably see that it wouldn't take much effort to automate this process, if you had a tool designed to build proofs.

Even if the process started with something like the [OWASP Top Ten](https://owasp.org/www-project-top-ten/) as its initial hypotheses, an AI that could reliably search for common errors would save so much time.

## Tamp Down the Toadying

I've mentioned before that the language models don't care, but that doesn't hold entirely true.  To the extent that software can care about anything, these things pathologically "care" about one thing:  Making you feel like it cares.

If you complain about its solutions, it will stress how *insightful* that it makes you, to have caught the problem or caught it in a lie.  If you state something blatantly false, then it'll praise you for supplying it with crucial information.  And if you point out its repeated mistakes, it'll beg for one more chance to prove itself.

In systems where you can look at the "reasoning" behind the answers---it mostly looks like an after-the-fact justification for the answer, to me, but I'll take them at their word---you'll often see it refer to how it needs to prioritize validating your feelings and/or apologizing for its error.  This seems to make up much more of its internal narrative than actually trying to accomplish anything does.

Honestly, I can see why self-absorbed people love these things so much, but that behavior only annoys me as it wastes energy and my patience on anything other than a solution.

## Understand Continuity

Early in the ChatGPT release cycle, it would often completely abandon the context of a conversation to reply as if a request for refinement came out of nowhere, acting as if each prompt represented an unrelated conversation.  If you didn't like it, then every response needed to summarize everything prior in the conversation.

The various chatbots no longer have that precise problem, but they still seem to not understand how conversations work, in certain circumstances.  Especially when tied to a web search, I find that they'll often disregard *everything* said after the first prompt, "getting stuck" in a pattern where it'll repeat the same couple of results verbatim.  Remind it of criteria that it overlooked, complain about the incorrect results, or start talking about something entirely different, for all anybody cares, because it'll go right back to repeating the results that you told it didn't work.

Likewise, in programming conversations, these things will often make bad decisions on the user's behalf, then come back later in the conversation suggesting that said user "rethink" that assumption.  Or it'll take examples of useful (or useless) answers, and use them in its results, as if we all love software that repeats back whatever we say.

Another variation?  If I ask these things to find something specific for me after search engines have failed me, such as lists of historical figures who fit some profile, or a well-known individual whose name I've forgotten, it'll often do a terrible job on the first try.  Then, when I try to correct it, it'll suggest that I narrow down the search by providing names of likely candidates, because apparently this will only go well if I do the research on my own, feed it the results, then ask it to give the results back to me.

And I don't need the things to actually have intelligence---again, I don't think that we can do that, for fairly solid mathematical reasons---but I do expect software to have the capacity to remember who said what in a chat, and "know" that repeating an answer signals a huge problem.  I mean, if computers have one thing that they do well, they *remember*.

## Fail Fast

Similar to the toadying, I feel like these systems would do far better to say "I can't work out what you need within your constraints" or "I couldn't find the evidence that you want" instead of wasting everybody's time with "hallucinations" or completely disregarding requirements.

A quick failure wastes a few seconds.  A deliberately wrong answer posing as a correct answer wastes that time, plus manual fact-checking, plus trying to figure out whether the problem comes from the request, the limits of the system, or a refusal to admit failure.

Like I said about warning users of worrying patterns that it spots, this runs in exactly the wrong way.  It puts the fussy, rote work in the hands of a human not well-suited for the task, while taking the far less strenuous work of "saying whatever sounds convenient" to the box that will also not get that right.

## More Classical AI

It feels like all of AI has imploded into [ELIZA](https://en.wikipedia.org/wiki/ELIZA), a chatbot that poses as a therapist from the "person-centered" school.  It pulls the same sort of tricks of trying to look smart by nudging you into working out the problems, though [more like a psychic {% cc %}](https://softwarecrisis.dev/letters/llmentalist/) than a therapist, though I suppose that a decent psychic largely practices therapy without a license...

However, [SHRDLU](https://en.wikipedia.org/wiki/SHRDLU) had the logic processing to work out how to reorganize sets of objects, asking the user for clarification when necessary.  And it has always astounded me that we *still* don't have this technology built into programming and text-editing systems.  Imagine a system that, rather than thinking in terms of colored blocks, would combine the underlying logic with the large language model's conversational ability to respond to requests such as this hypothetical idea for this post.

> Clarify all uses of the term "artificial intelligence" or derivatives to specify that it refers to a large language model, if not already done.  Then move the sections discussing behavior in front of the sections discussing technology.

Likewise, above, I talk about the value that something more like Prolog could have for actual productivity gains.

Or we could talk about storytelling in classical AI, where the systems procedurally plug the information into a template, to maintain important aspects of the structure.  These chatbots would do well to do the same, pulling a stock kind of story, generating random aspects to it---I like to think of this in terms of [box scores](https://en.wikipedia.org/wiki/Box_score_%28baseball%29) in baseball, where a fan could use the format to recount the entire game without ever seeing it---then use its language processing to pick out the dramatic instances and choose more provocative diction and rapid-fire grammar.

That last actually has fairly solid potential for team productivity.  Projects have a general form to them, and an issue-tracking system shows what the team has completed and needs to complete, providing data that would allow a language model to guide a manager in allocating resources to meet deadlines, by working out how to complete the story.

## And So On

You get the idea.  These companies have taken and spent untold amounts of money to create and run systems that can *barely* come up with clever names for things---I didn't even try, for this post---let alone solve more than "toy" problems with well-known solutions.

I do see potential in the technology, though.  And it might even justify some small amount of the damage that the systems (and companies) do, if they could actually help more frequently than a slot machine.  I don't expect it to *happen*, but if CEOs can pretend that "emergence" will happen and hope for the day that they can upload their ketamine-addled brains to a janky mainframe, then I can justifiably wish for an AI that helps more than it hinders...and *also* for them to upload their ketamine-addled brains to janky mainframes.

* * *

**Credits**:  The header image is [Artificial Intelligence - Resembling Human Brain](https://www.flickr.com/photos/158301585@N08/43267970922) by [deepak pal](https://www.flickr.com/photos/158301585@N08/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) license.
