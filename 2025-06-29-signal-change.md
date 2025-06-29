---
layout: post
title: Crossing Signals
date: 2025-06-29 08:05:12-0400
categories: 
tags: [creative-commons, rant]
summary: Looking over the new Signals mess from Creative Commons
thumbnail: /blog/assets/CC-signals-2025-Social-Assets-2.png
description: Back to Free Culture work, trying to detangle Signals from, well, noise.
spell: permissioning
proofed: true
---

* Ignore for ToC
{:toc}

This week, Creative Commons tried---and I believe failed, though only time will tell---to launch their [Signals framework](https://creativecommons.org/ai-and-the-commons/cc-signals/), a fairly clumsy attempt to insert itself into the debate around sharing and AI, after disclaiming all responsibility in the matter.  And it has gotten almost universally panned on the Internet, except by AI-boosters who see it as "the community" finally giving them legitimacy.

![The presumed CC Signals logo, featuring all-lowercase black text over an oozing but symmetric design with four nodules, rendered in a gradient from hot pink to chartreuse](/blog/assets/CC-signals-2025-Social-Assets-2.png "This mess offends me far more than the actual framework...")

I wrote the original version of this post as a [GitHub discussion](https://github.com/creativecommons/cc-signals/discussions/52), to explain why I don't quite think that it'll *hurt*, but also can't imagine it helping.  Absolutely feel free to join that discussion, if you want to use my post there as a springboard or need to argue my points.

Here, I've added some background, fleshed out the arguments in more detail, and reorganized a couple of things to make them flow better as something that the general public could read.

{% cw As an off-the-cuff reaction to the project, I didn't spend the usual time only linking to Free Culture sources. %}

Let's start with trying to explain what they have.

## What the Heck

Some of you might remember that we have an AI bubble to contend with.

Companies spend untold piles of cash on data centers, as well as on trying to convince us that we have no other option than to use their trash.  They tell investors that what they have comes *so {% emoji pinching hand %} close* to so-called general AI, while telling we users that we need them to summarize endless e-mails, endless because people wrote them with AI to look like they put in more work.

While Creative Commons has, in the past, insisted (probably rightly, much as it hurts) that any machine-learning training would fall under the heading of Fair Use---alienating many artists at the time---they somehow decided now to wade in and try to...do something, or get involved, or whatever, alienating an entirely new cohort.

I skimmed through the Signals descriptions, and at least believe that understand the mechanics.  It wants to pair with the IETF's upcoming [AI Preferences](https://datatracker.ietf.org/wg/aipref/about/) extension to `robots.txt`, where you'll have the option to say something like this:

```
User-Agent: *
Content-Usage: ai=n
Allow: /
```

And that will, in an ideal world, tell scrapers to pound electrons.  Glass-half-full libertarian types to the end, Creative Commons asks what about content wardens---the rest of us call those "artists" or "creators"---who *love* big companies scraping their sites, and believe that they can help the companies see the light and become better Internet citizens.  If such people exist, then they can add more jargon to the `Content-Usage` string above.

Those add-ons say that (ideally) you should only scrape if you plan to credit the owner in some way, and maybe try to do something nice for the community or owner.  I call it silly, a minor exception to something that companies will already ignore, but other people got angry, seeing it as a betrayal and capitulation to the AI crowd.

While I don't buy that, at least no more than prior betrayals over the years, I do see this as a mess that doesn't go anywhere, and the following cleans up and expands on what I wrote in the aforementioned Discussion on GitHub.

## Signals Go Wrong

I've tried to wrap my head around what this *wants* to do, and came up empty.

Don't get me wrong, here.  Like Creative Commons seems to, I wish that we lived in a world where sprawling multinational corporations didn't see the Internet and its users as their property to monetize as they see fit.  And I get that Creative Commons, in its heart of hearts---[born in the fires of lawsuits]({% post_url 2025-05-18-copyright-thoughts %}#quick-history) threatening music sampling and Napster, while legislation and treaties threatened the public domain---doesn't like copyright or using it as a tool.  I also, as described above, understand that Signals means to sit downstream from a check that would ask AI scrapers to go away, such that people who don't want scraping at all can ignore the framework.

And yet, especially among the big companies, we've seen them argue that [they can't respect copyright](https://arstechnica.com/tech-policy/2025/03/openai-urges-trump-either-settle-ai-copyright-debate-or-lose-ai-race-to-china/) and [survive](https://www.niemanlab.org/reading/former-meta-exec-nick-clegg-says-asking-artists-for-use-permission-would-kill-the-ai-industry-in-this-country-overnight/), and by the way, [art has no actual value](https://futurism.com/meta-copyrighted-books-no-value), anyway.  And I can remember not that long ago when a major player in this space insisted that [this scraping constituted Fair Use](https://creativecommons.org/2023/02/17/fair-use-training-generative-ai/), really, so the infractions and arguments didn't matter.

### Size and Role Conflation

As a quick aside, in pushing these criticisms to Creative Commons, I tried to hammer the idea that they seem to want to dance around the issue semantically without actually solving a problem.

Most critically, and I've brought this up on the blog before, they like many others [blur the distinction between a student]({% post_url 2024-03-03-ai-licenses %}#flawed-premise) experimenting with training a language model and venture capital-fueled behemoth data centers pummelling websites and downloading anything that they can find, changing names and IP addresses to dodge around blocks.  But they differ dramatically, both in the damage that they do and the reaction that most of us have to them.  In reality, I doubt that anybody objects to a small-scale or productive use, such as optical character recognition or machine translation, but when it gets into reprocessing art into shallow remixes as a paid service, it starts to look significantly different.

In reality, we can oversimplify to four groups of AI scrapers.

- Huge, venture capital-funded growth-hackers, who want to sell you a subscription to plagiarism slop on tap.
- Huge, venture capital-funded growth-hackers, who want to sell a maybe-useful product[^1].
- Independent workers and students experimenting with slop production, because it looks fun.
- Independent workers and students building maybe-useful products.

[^1]:  Examples of useful neural network products include OCR, machine translation, error detection, and so forth.  They have a closed-form and help more than they harm.

While I realize that this distinction *partly* bakes itself into the `robots.txt` frame, where you can choose which remote computers you'll tolerate, I do want to point out that, really, only one group out of the four---the smallest number of entities on the board, though with the largest footprints---will offend most artists.  And honestly, when the AI bubble pops, we could plausibly shame the other three groups into complying with the directives and Signals.

### Bringing the Tone Police to a Gun Fight

My first big problem, then, stems from how Signals creates a system where we pretend that, rather than sprawling corporations exploiting everybody, we *actually* have a both-sides etiquette problem.  At its core, Signals seems to say that the same companies shoveling up everything that they can as undifferentiated "content" because, to them, it has no value, only do so because nobody has asked them nicely enough to stop[^2].

[^2]:  Technically, I agree, in that regulation reining them in so that they *can't* do it would say it nicely.

Moreover, the "solution" wants to put the burden on every creator---"starving artist," if you will---to ask politely for billion-dollar companies to maybe, if they have the opportunity and goodwill at some point along the way, maybe consider that a website's maintainer doesn't want to help them externalize their costs.

I didn't bring this to the Creative Commons Discussion, because it feels adversarial enough that they'd use it as an excuse to ignore my other points, but I should point out that conservatives and libertarians use exactly this argument to push back against disability rights.  Don't mandate accessibility in building codes or sue when a facility refuses to accommodate you, they insist, because that makes a spectacle of the situation and makes everyone grumpy.  Rather, the person who needs some extra help to get around should schedule an appointment with the owner and *ask* for that help every time, and give the owners the option to decline, if they don't have the energy.  And they should do it one-on-one, in private, so that other people who need the same help don't get any ideas about deserving the same respect as non-disabled customers or clients.

This feels similar, in saying that we shouldn't put legal or procedural obstacles in the paths of the big AI companies, because everybody who doesn't care for their behavior can wish for them to do better, and maybe that'll work.

### Victim Blaming

As long as I have the libertarian "let's make this a friendly conversation between prey and predator" idea on the table, I'll jump around the original version of this post a bit, because a lot of people have already suffered the damage from these companies, so "did you consider *just asking* Meta (or Perplexity, or OpenAI) to care about your work as more than a resource to exploit?" feels like victim-blaming, and maybe even shaming.

The problem doesn't come from artists forgetting to lock their doors, after all, because none of us should have the responsibility of defending ourselves from billion-dollar companies pouring money into data centers specifically to extract value from anybody who dares to post something online.  This goes further than suggesting that we all learn better negotiation tactics or self-defense, and suggests that we hold the responsibility for how those companies act with our work.  If you find your server ransacked by a bot, you really should've given the bot's owner an invitation to help you after inviting them in.

Now, maybe if Signals had come out two or three years ago, it'd feel more legitimate.  We wouldn't have artists who can identify their work plagiarized by the chatbots or executives rambling about how the rules shouldn't apply to them.  But at this point, it doesn't look like more than a weak attempt to capitalize on anti-AI anger while not actually doing anything that will slow down the companies.

Well, again, it looks like that *unless* the AI bubble bursts soon.  If we can wipe out the industry front-runners, then the rest of the pack won't have that precedent to point to as "fairness," and we could push them into behaving responsibly.  Until then, though, this puts all responsibility on artists and asks the companies to *consider* thinking about other people's feelings.

Actually, speaking of permissioning, maybe we should talk about that, next.

### Permission Framework

As an implementation standing alone, I don't see a problem with what Signals does, for reasons that I explained earlier.

It also actively refuses to actually accomplish anything, though.  We can try to compare it to `robots.txt`, in that it also technically "doesn't actually do anything" but organizations respect it, but that analogy doesn't work.  In the 1990s, we didn't have [Alta Vista](https://en.wikipedia.org/wiki/AltaVista) executives screaming about how, if we didn't let them index every page, then The Commies{% emoji trademark %} would win.  We didn't have [Jeeves](https://en.wikipedia.org/wiki/Ask.com) suggesting that websites have no value unless indexed by them.  And we certainly didn't watch them going to court to defend those inane arguments.

Having seen how these sorts of half-baked permission have often panned except for `robots.txt`, I'd say that, at best, these rules will only intimidate a couple of students into kicking in a couple of bucks to some organization claiming to represent "the ecosystem."  But it'll also scare away a bunch of younger folks who can't afford to contribute anywhere and don't want to offend anybody.

Most importantly, it'll have absolutely no effect on the wealthy creeps who already see the entire Internet as an exploitable resource [with no governance](https://www.eff.org/cyberspace-independence).  Generating all the traffic, they'll continue to gesture, wild-eyed, at China or Iran or Venezuela or Venus or wherever else, insisting that they need your data to win.

### Also, Ecosystem

By the way, I didn't include this question in my original post, but what the heck does this mean?

> ![A yellow-green icon with six black dots in a circle and a black four-pointed star to the upper-left](/blog/assets/The-Suite-of-CC-Signals_2-e1750710325526.png "No cutesy abbreviations?"){: style="height: 1em;" } **Ecosystem Contribution:** You must provide monetary or in-kind support back to the ecosystem from which you are benefiting, based on a good faith valuation taking into account your use of the assets and your financial means.

I mean, apart from the parts that get so watered down and qualified that they mean something different to every individual who reads it, and so mean nothing.  "Based on a good faith valuation taking into account your use of the assets and your financial means" could mean anything, but will **probably** mean something like a low value placed on *the assets* (as Meta has established), *the assets* allegedly representing only a vanishingly small part of the model, and none of these companies know how to turn a profit, so they really don't have anything to pay anything, either to the *content warden* or the *ecosystem*.

Really, though, I only care about the one word, here, maybe phrase.  What do they mean, "back to the ecosystem"?  Or more precisely, *what* ecosystem do they mean?  If, for example, a company tries to scarf down all of Wikipedia, can they plunk down a hundred bucks for a World Book subscription for their kid, and call that support for the encyclopedia ecosystem?  Could they kick in a few bucks to the [Tiddly Wiki](https://tiddlywiki.com/) developers as support for the wiki ecosystem?  Maybe they could edit Wikipedia by deleting the *Controversies* section of the page about their company, and then buy themselves a nice lunch.  Or---and here I need to take a cynical view of things---does Creative Commons want you to see *Signals* as the ecosystem and donate to them?

Honestly, if Creative Commons doesn't nail this down, every AI company will absolutely tell you that their work, even the scraping, supports the *AI ecosystem*, the only ecosystem that matters to them.

### Smaller, but Fixable Problems

After the above issues, we still have functional problems to deal with.

For example, consider the redundancy of asking for attribution for a second time.  But this time, rather than the legally binding, contractual *requirement* of attribution in exchange for use of the material, this version only requests a vague best effort, "based on the method, means, and context of your use," with no legal backing to it whatsoever.

It doesn't take much work to imagine a company deciding that their individual case (that looks like every other case) makes the best method of credit some obscure, onerous trek to convince the chatbot to acknowledge the contribution.  Anything more overt than that would, I can hear them argue, spoil the immersion in the conversation.

Similarly, if Signals would help at all, then the *credit+1* scheme---you can select attribution, plus one of direct contribution, ecosystem contribution, and openness---seems incredibly silly.  I can imagine that the people behind Signals might have a fear of proliferating edge-cases like the early modular Creative Commons licenses that I mentioned before.  But if a creator hasn't tried to use the `ai=n` directive to deny scraping somewhere upstream from Signals, it seems entirely sensible to ask the same organization for help keeping things sustainable *and* making the results open, especially when the requests get phrased to make them more aspirational than required.

Frankly, the idea that an independent artist posting material freely online can ever ask *too much* of a billion-dollar corporation exploiting their work seems laughable.

### The Big Problem

On top of everything else, to put it bluntly, Creative Commons has already trashed the reputation and probably uptake of their Signals initiative.  Especially with the "stop asking us, it's just Fair Use" approach that I mentioned above, as other people have pointed out, this comes off as saying that the future of Creative Commons lies in siding with billionaires who want to replace artists with software that lightly remixes existing art.

A project like [Common Voice](https://commonvoice.mozilla.org/) might use it, since it always existed primarily for training AI, and Mozilla increasingly seems to think that their future lies with AI rather than users, but they feel like a massive exception.

Even in the narrow cases that I've outlined where I can see Signals becoming useful, I'd bet that this roll-out has poisoned the idea so thoroughly---I see people across the Internet threatening to abandon Creative Commons *licenses* in their work over the terrible optics---that any real-world use of Signals will look more like a stigma than any attempt at participating in a "commons."

### My Recommendations to CC

If somebody at Creative Commons wanted to put me in charge of Signals---and I seriously doubt that they would ever consider such a thing---I'd take the following steps hoping to rehabilitate it.

First, the project needs to stop worrying about pleasing everybody and find somebody, even one specific person, to care about in all this, and figure out how to solve *their* problem first.  The entire enterprise, I notice, has a distinct lack of humanity to it, from dismissing artists, journalists, and others as "content stewards" and their work as "the assets," to dumping everything on the Internet with a figurative Mission Accomplished flag, to acting defensively to criticism in their implementation repository.

Then, it needs to focus on stopping the offenses, not teaching self-defense (or more accurately, table manners) to the victims.  Separate out the four groups of AI scrapers that I outline above, and target the scheme at curbing their behavior.  Likewise, Signals should focus on curbing bad corporate behavior in particular, not technologies, and certainly not buzzwords for technologies.  After all, we all know that "no AI scrapers" really means that every AI company *actually* runs their scrapers for some other reason, and sometimes the AI training team accesses the drive where they stockpile the data.

Or to summarize that last item, Signals should *never* assume that the people who keep repeating that the rules don't apply to them will somehow abide by requests that don't have legal backing behind them.

And finally, Creative Commons needs to accept that, maybe, when any AI chatbot can reproduce any license in full and [other famous texts](https://www.newscientist.com/article/2483352-metas-ai-memorised-books-verbatim-that-could-cost-it-billions/)---it takes more prodding than it once did, but I can still get most chatbots to autofill the GPL for me---that copyright and the licenses actually have at least some relevance, because the language models might not have the perpetual Fair Use claim (from low substantiality and effect on the market) that Creative Commons always wants to claim.

## Solutions

OK, I don't know what the correct solution looks like, but it probably doesn't look much like holding up a "Please Don't Mug Me" sign.  Where can we go from here, though?

At a bare minimum, we need to regulate corporate AI initiatives.  I need to note that, in the United States, it doesn't look like Congress has removed the ten-year ban on state-level AI regulation in the so-called [Big, Beautiful Bill](https://time.com/7297580/ai-moratorium-senate-big-beautiful-bill/), so you might want to call your representative to get them to work on that or prevent something similar from showing up in your country.  Notably, regulation needs to work so that it limits the irresponsible actions of the big companies without digging them a "moat" that prevents upstarts from attacking their business.  *That* will make them behave.

Alternatively, if anybody has a switch that they can flip to force the AI bubble to burst, that would also fix the problem.  We'd need to find a use for sprawling data centers and their servers, but I feel like we could manage.

Then, assuming that we ever did, we probably want to stop thinking of Creative Commons as anything like leadership in the Free Culture space.  Their refusal to define commercial activity for users of the non-commercial licenses, not to mention their continued support of mutually unintelligible bodies of work *created* by their pushing baseline and non-commercial licenses as equivalent options, probably should have tipped everybody off.  And if that didn't, maybe their seeing Fair Use around every corner might have suggested that they don't actually care that much.  And if none of those, their complete lack of solid opinions on almost any matter for twenty years certainly should've kept people from looking to them for useful advice.

I don't advocate for abandoning the (good) *licenses* yet, because nothing about them seems shaky other than the relative weakness of the share-alike clause, but certainly treating Creative Commons as some sort of guiding star seems more ill-advised than before.  They never struck me as useful, but this makes them look like careless clowns.

Importantly, though, the time may have come for Free Culture creators to start banding together.  We've already had too many "foundations" trying to direct this space---mostly by insisting on libertarian principles that serve to keep us apart, probably a post for another day---and not nearly enough creating and acting collectively.  As such, I don't see a replacement for Creative Commons doing any better...

* * *

**Credits**:  The header image is the [CC Signals logo](https://creativecommons.org/2025/06/25/introducing-cc-signals-a-new-social-contract-for-the-age-of-ai/) by Creative Commons, made available under the terms of the [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/deed.en) license.  You'll also see the Ecosystem Contribution icon from the [CC Signals Implementation](https://creativecommons.org/ai-and-the-commons/cc-signals/implementation/) page, made available under the same terms.
