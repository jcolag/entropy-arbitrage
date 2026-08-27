---
layout: post
title: Maxwell Smart's Demon
date: 2026-08-23 10:35:12-0400
categories:
tags: [artificial-intelligence, harm]
labels: [rant]
summary: Bad fences make strange bedfellows (or something)
thumbnail: /blog/assets/diablillo.png
offset: -37%
description: Please defend against the right attackers when defending.
spell: PZnrSV Iocaine Lucha
proofed: true
---

* Ignore for ToC
{:toc}

As you might have guessed by this going out so late in (for me) the morning, most of the idea for this post struck me late yesterday.  As such, I hope that you'll indulge any sloppy structure more than you ordinarily might.

In any case, whenever I need to have a conversation about keeping something secure from some outside force, I try to emphasize the need to evaluate every potential solution against its false positive and false negative errors.  For an approachable example that everybody probably understands, if I lock my door, it doesn't actually *matter* that it protects me against people off the street trying to walk in, because that happens so rarely.

![A snarling, anthropomorphic canine creature in front of a fiery background, with four empty eyes and only tufts of horn-like fur protruding from bumpy skin](/blog/assets/diablillo.png "Would you believe three Newton imps in a trench coat walking Cerberus...?")

Instead, I care about comparing the number of times that the lock actually saved me trouble against two other numbers, and their respective importance.

- How often I need to unlock the door for a legitimate visitor, including myself, if I manage to lock myself out.
- How often someone who I want to keep out can find their way in, maybe even because they have a copy of the key.

The example seems instructive, because if you give it some thought, then you'll notice that, for every household, those three situations have a different likelihood and presents a different threat.  Probably anybody who has lived next to a bar has had someone sufficiently impaired that they tried nearby doors, maybe dangerous, maybe not, but definitely concerning.  Most people have probably had situations where answering the door for someone felt inconvenient and/or locked themselves out.  And people who have dealt with domestic violence especially need to worry about who has keys and could have made duplicates.  Not all of us deal with all those situations, and certainly not to the same degree, which means that each of us needs to weigh them differently.

False positives identify a problem unnecessarily.  False negatives miss a problem that you needed to catch.

The same holds for your spam filters:  Compare the amount of spam that it protects you from to the number of legitimate messages that it blocks *and* the amount of spam that you still see.  The same reasoning applies to any rule-based system, really, and that causes problems.

## Politics

As a digression, it seems worth pointing out that many, maybe even *most*, legitimate political arguments come from ignoring one flaw in favor of the other.

For example, every news outlet and every politician, these days, wants to talk about immigration.  And everybody frames it in *exactly* the same way, despite opposing each other vehemently.  "We want the good people to get through, *but* we need to limit access to keep out the bad people."  You hear that on the far-right.  You hear that pretty much everywhere except among the "we could actually get rid of borders and let people travel at least as conveniently as money and products" crowd[^8A-F3z].

[^8A-F3z]:  I count myself among them, fully aware that I completely ignore the false negative errors in my idea of letting people live wherever they damned well like.

And while the far-right differs from everybody else in that they *also* have racism and ethnonationalism at the heart of their proposals, most disagreements come from seeing false positives or negatives as having substantially different weights.  The more progressive you go, the more they worry about accidentally excluding someone who deserves to live in their country, a false positive.  The more conservative you go, the more *they* worry about accidentally admitting an immigrant who goes on to do something terrible when they could've stopped it, a false negative.

Public assistance?  False positives mean that a needy person goes hungry because they didn't *appear* sufficiently needy, the more progressive worry, whereas false negatives mean that somebody who can afford to pay the bills manages to get help, the more conservative worry.  Civil liberties?  Conservative thought worries that a guilty party will go free "on a technicality," whereas progressive thought worries that we'll punish an innocent party through forced confessions, planted evidence, and the like.  You can even see things lining up that way when it comes to the rights of transgender folks, with conservatives wondering what *might* happen if we let transgender people play sports or pee or whatever, and progressives trying to play down the numbers while also (finally) pointing out the threat that this also poses to ever cisgender person[^6-tdSi] who doesn't conform to the gender binary in a particular observer's head.

[^6-tdSi]:  Don't take your eyes off the pain inflicted on transgender and non-binary folks, here, but also, don't think for a minute that the far-right actually cares what happens to them.  Instead, they want to use these laws to police their idea of gender norms.

We could go on, here, but you probably see the point.  At least when you don't have authoritarian weirdos wasting everybody's time, most of politics involves compromising to find the tradeoffs between false positives and false negatives that everybody can live with.

## Further Afield

The same holds for a variety of non-security issues, too, as you can probably guess.  If you have a rule about which television shows you'll watch, what events you'll attend, what you'll eat, and so forth, then you'll inevitably miss out on something that you would enjoy, and you'll inevitably still suffer through something that you hate.

You can't *eliminate* these problems.  They represent errors, after all, and every significant system of rules inevitably has errors.  Like the political situation, you can only find the tradeoffs that you can accept.

You can go in the other direction, though, and *increase* both kinds of errors.  Whenever an organization institutes security policies so that people see leadership as "doing something" about a breach, that almost always costs every innocent person, while simultaneously providing plenty of holes for danger to slip through.

This dynamic becomes most visible in politics.  Every attempt to curtail sex trafficking has no effect on the actual trafficking, but *does* put sex workers in danger as they get driven off platforms that allow them to vet customers.  Every attempt to protect children from abuse online fails to protect anybody, while exposing everybody else's information to attackers.  The same happens in other areas, but when the local supermarket fouls up its security, it doesn't make global news.

## The Bots, to Everyone's Chagrin

OK, now that I have introduced the idea of this going horribly wrong, let's talk about generative AI again.

I know.  Don't panic.  I (probably) won't turn this post to ranting again about AI.  But I did raise this issue because of the ways in which people often treat chatbots and their scrapers.  In fact, you might find this post wagging an accusatory finger at *you*, not the "get on board or get left behind" crowd...largely because I've said everything that I want to say about the latter.

Most specifically, I want to talk about people who run websites wanting to protect their website from corporate scrapers, and then go on to ignore the false positive and false negative errors to such a degree that they work better *for* scrapers.

Today, this involves two pieces.

### The Return of Hash-Cash

Thirty-odd years ago, unsolicited advertising e-mail (spam) had become *such* a problem, that several people independently invented proof-of-work systems---yes, similar to how cryptocurrencies "mine" their next blocks---where the recipient would refuse to accept your e-mail unless you wasted a fixed amount of electricity solving busy-work math problems, in order to prove that you *really* wanted to send them something.

And this solved everybody's problem, and now you never see---

OK, no.  Everybody laughed this out of the room, because if widely adopted, it would force the entire world to burn fuel, because a handful of people can't live with even *noticing* an e-mail about the kid of some foreign official in a collapsing regime needing to borrow your bank account to smuggle their embezzled millions out of their country.

No, seriously.  I can't find solid information, because the decentralized nature of e-mail works against convenient counting, and upstream spam filters make that worse, but several websites provide estimates in the hundreds of billions of e-mails sent per day.  Let's waste some of our own energy and indulge {% wiki dead internet theory %} for a moment, and declare ninety percent of that spam of the sort that the sender wouldn't see it worth spending anything to make sure it got through.  We can call the remainder fifty billion messages, for a nice round number.

Let's pick some arbitrary numbers, here, to follow this through.  Imagine, for example, that we decide that we want people who send us e-mail to spend one tenth of one (US) cent.  Checking my electric company's website, it looks like my electricity costs $0.0452 plus $0.073372 (delivery plus fuel) per kilowatt-hour during "Super Off-Peak" hours[^PZnrSV], more or less overnight.

[^PZnrSV]:  Thirty years ago, we didn't have rates during different parts of the day, because the companies had no way of knowing *when* you used electricity, so the same analysis wouldn't have worked when people tried to propose these ideas.

I use the cheapest rate for two reasons.  First, if we wanted to stop abusive automated systems, they'd run at the cheapest times.  Second, the numbers happen to work out conveniently, because the price per kilowatt-hour comes to $0.118572, a hair over our target of a tenth of a cent.  That probably doesn't mean anything to anybody, so let's put that into context.  Again searching through a handful of websites, it looks like a typical modern CPU might run at around fifty watts, meaning that we need to assign enough work to keep the CPU occupied for *twenty hours*[^HuC3pk].

[^HuC3pk]:  Apologies who read the original version of this, where I somehow divided one thousand by fifty, and got two as the quotient.

OK, now that we have that context, go back to the number of e-mails, and multiply this by fifty billion.  If we (as a society) took this idea seriously, then we would want to waste fifty million dollars and a trillion CPU-hours per day, more than eighteen billion dollars and three hundred sixty trillion CPU-hours annually.  And note that this goes to waste, helping nobody beyond proving that you actually want to send the e-mail.

Oh, and for further context, fifty billion kilowatt-hours, or fifty terawatt-hours, would put this e-mail verification scheme alone between the {% wiki List_of_countries_by_electricity_consumption|annual power consumption %} in the neighborhood of Singapore, Portugal, Qatar, Greece, Romania, Oman, Hungary, Hong Kong, Morocco, Belarus, New Zealand, or Denmark, which use sixty down to forty terawatt-hours each.

I promised to make this about AI scrapers, though, so let's bring [Anubis](https://github.com/techaroHQ/anubis) into the conversation, a proof-of-work system that people shove in front of their websites, in hopes that the AI scrapers would walk away.  I haven't looked into how it measures how much it makes you pay, but it imposes a *global cost*, the burning of energy, to stop the AI from burning energy to train LLMs.  A quick search didn't turn up any numbers in this area, actually, which I hope helps explain why I went through the e-mail version of this problem so thoroughly.

Oh, and by the way, the person/people behind Anubis had [AI generate the cat-girl mascot](https://github.com/TecharoHQ/anubis/issues/33#issuecomment-2741845002), "considering" a change after it caught on, and they have [embraced vibe-coding](https://github.com/TecharoHQ/anubis/blob/main/AGENTS.md).  They also *charge*, if you find the AI-generated mascot objectionable.  It seems unfair to call them shady without investigating beyond that, but before I tie this into the actual point of this post, it does seem worth noting that the alleged anti-AI solution loves AI, but will happily charge you (real) money to waste everybody else's (hypothetical) money so that you can feel like you have stymied the AI companies.

Oh, and they quietly [admit at least one scraper used for AI training](https://github.com/TecharoHQ/anubis/blob/9c2f300518a1614740798d845182dad18aa3e529/data/bots/ai-robots-txt.yaml#L4), under the theory that it'll reduce traffic over the longer term.

However, let's ignore the rest of this.  Ignore the waste, the AI-boosting, and the shady business model for a moment.  Have we evaluated the solution against its false positive and false negative errors?  I doubt it.

Consider that, sometimes, Anubis breaks and [locks normal users out](https://discourse.haskell.org/t/is-the-anubis-bot-checker-in-gitlab-broken/14521), not to mention blocking more conventional bots, such as search engine spiders and archive systems.  That seems like a *lot* of false positive errors.  And that doesn't even count the people who can't afford to waste an unknown amount of electricity to prove that they should have the right to read some text.

Meanwhile, do you know who has no worries about burning money and loves a good story about automating tasks?  Yes, the [AI companies already light money on fire {% cc %}](https://isaiprofitable.com/) with smiles on their faces.  Hooking up a JavaScript runtime---or using a "headless" browser to scrape---wouldn't cost them much at all in comparison, and "our rogue AI found a way around the AI-blocker" only gives them more fodder for marketing.  Like the false positives, that seems like a *lot* of false negatives, or at least the potential for them, even before we remember the part where they let one scraper through *because AI companies use it*.

In fact, Anubis seems to carry so many errors that it almost seems like this does the *opposite* of stopping AI scrapers for the benefit of humans.

### Reading Is Fundamental

I don't have a long background on this one, so let's get right into it.  The idea for this post---though I've wanted to talk about Anubis since it launched---actually comes from the recent media attention on anti-AI fonts.  Specifically, [Ghost](https://www.mixfont.com/ghost-font), [Decoy](https://www.mixfont.com/experiments/decoy-font), [Shield](https://shieldfont.org/), and probably a bunch that I have never heard of, all claim that, if you render your page in their font, then humans can read it (with some difficulty), but bots can't.  This follows on work from past decades of fonts designed to stymie optical character recognition (OCR) scanning.

And so we have a bunch of news sites breathlessly telling us that you can use this font to stop scrapers from getting at your work.

Yeah, you can probably tell where I want to go with this.  We have *all* false positive and false negative errors, here.

Let's imagine that I use one of those fonts for the blog.  What happens?

First, every reader now has a higher cognitive load to read what I have written, and some people won't have the visual acuity or ability to focus to get through a full sentence.  They (the fonts) openly make work less accessible, by making it more difficult to read every letter, relying on average vision and visual processing to dodge criticism, assuming that the designers thought about accessibility at all.

And by the way, each of us has transient disabilities.  If you need to pay attention to the stove or a child, then you can't focus on text on a screen.  Maybe your screen cracks, making it difficult to read under the cracks.  Maybe the back-light dies, or you have too much sunlight in the room, making it harder to see the screen.  Looking at it through that lens especially, that seems like an enormous number of false positive errors, doesn't it?

Meanwhile, what does a scraper see?  It sees HTML.  Unlike you and me, who have colors and fonts, using my own website as an example, a scraper "looks" at something like this.

```HTML
<h1 class="title">John Colagioia</h1>
```

No matter how you dress it up in the style sheets, the bot always sees exactly the same HTML.  It will *notice* that the page uses a font, such as where the blog pages include lines like the following.

```HTML
<link rel="preload" as="font" href="/blog/assets/Vollkorn-Bold.ttf" type="font/ttf" crossorigin="anonymous">
```

Noticing that I use the font, though, certainly **does not mean** that the bot would render the text in that font, then run OCR so that it can get the wrong answer slower.  In other words, like Anubis, these fonts have a hundred-percent false negative error rate for websites.

Would you reduce the false negatives by printing everything out?  Sure.  How many AI scrapers have shown up at your door, though?

What about images with no `alt` text?  Congratulations, you have found a way to make your site *even less* accessible to humans.  You have also made it impossible to see in text-based browsers, with bandwidth problems, and a bunch of other scenarios.

## If Not Those, Then What

If you actually need to keep AI scrapers away from your material, I only see one class of solution actually working:  Trapping them.

Tools such as [Nepenthes](https://zadzmo.org/code/nepenthes/) and [Iocaine](https://iocaine.madhouse-project.org/) spin up a lightweight server that simulates an infinite maze of pages.  It dynamically generates every page, keeping them small, and sending them as slowly as possible to whatever made the request.  Working that way feeds the scraper as much garbage as it'll wait for, while also slowing it down and preserving the server's bandwidth.

If properly optimized---and I have no doubt that those two projects have done so---it wouldn't keep the scrapers off your server entirely, but it presumably *only* traps the scrapers since you don't present the link to the trap as clickable, and it doesn't affect many normal readers.  Unlike the other solutions, it takes work to set up, *but* has few false positive or false negative errors, as we would prefer.

I don't (yet?) need to worry about scrapers hammering my site, but if I did, I would take that approach, though I don't know if I'd land on either of the examples.

## Agents and Demons

In 1867, {% wiki James Clerk Maxwell %} suggested a thought experiment where a "finite being" could---if you'll pardon the anachronism---play {% wiki Pong %} with the molecules in a container, separating the high-energy particles from the low-energy particles, thereby violating the laws of thermodynamics suggesting that heat (high energy) will infiltrate cooler areas over time, homogenizing the temperature.

This misunderstands thermodynamics greatly, because thermodynamics applies to closed systems, and "guy opening and closing a door" expands the system beyond the container.  But "Maxwell's demon," as Kelvin would later call it, serves well as not only the thought experiment that helps students understand what a "closed system" means, but also as a metaphor for all work that involves separating one kind of thing from another.  Going back to the political discussion, you can think of the criminal justice system as aspiring to serve as Maxwell's demon, separating the law-abiding people from the law-violating people.

In an ideal world, such ideas might even work perfectly, eventually.  But we don't live in an ideal world, we live in a world seemingly {% wiki Get_Smart|crafted by Mel Brooks and Buck Henry -%}, where the demon always reports back that it *missed it by that much*.  And in that light, Anubis and the anti-AI fonts "work" exactly like the show's Cone of Silence, making it difficult for the intended participants to have a conversation, while providing plenty of room for attackers to jump in.

* * *

**Credits**:  The header image crops [Imp](https://web.archive.org/web/20161007130614/http://ramonlucha.com/) by Ramon Lucha, made available under the terms of the [Creative Commons Attribution 4.0 International](http://creativecommons.org/licenses/by/4.0/) license.
