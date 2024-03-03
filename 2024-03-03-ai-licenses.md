---
layout: post
title: The Rise and (Likely) Fall of Anti-AI Licenses
date: 2024-03-03 07:22:12-0500
categories:
tags: [art, harm, rant, technology]
summary: Public licensing based on intended use seems prone to failure.
thumbnail: /blog/assets/40466252685_3701e77720_o.png
offset: -25%
teaser: Despite disliking the state of AI, I want to push back against the proliferation of anti-AI clauses in public licenses.
spell: Butterick je suis une protéine ser Ecole polytechnique
proofed: true
---

![People milling around and talking, behind a projected glass screen that obscures them](/blog/assets/40466252685_3701e77720_o.png "Something about the light fixtures and air vent delights me, for some reason...")

Over the last year or so, I've started to groan at the drum-beat of social media posts that feel like such a waste of effort, especially since they all seem to read as if the various users copied-and-pasted them from some original post with some tweaks.  In other words, you could replace them all with the same post.

 > When will [either Creative Commons or the Free Software Foundation] publish a license that disallows everybody from stealing my ultra-valuable work {% emoji peacock %} and using it to train Large Language Models?

Either this, or they ask what license they can use to prevent the Internet from using their work in training sets.  At first, I tried to reply coherently, but soon realized that the people posting didn't really have any interest in the answers.  And more to the point, I don't have the time to respond to everybody out there with a bad idea.

As such, I'll write this post once, and either consider my piece said or point people to the page.  You readers can also feel free to use it how you please, as you presumably already understand by the license posted at the bottom of the page.

In any case, I have a handful of reasons---even though I similarly [dislike the direction of the AI market]({% post_url 2024-02-25-ai-doom %})---why I reject the idea of an anti-AI licensing regime.

## Flawed Premise

Let's get the core idea out of the way, first.  "You can use this code for anything you want *as long as you don't work in a field that I don't like*" pretty much expresses the opposite of the spirit of any public license.

I contend that this disconnect explains why the so-called [ethical licenses]({% post_url 2020-03-29-copyleft %}) haven't really gone anywhere, despite a solid effort trying to push them.  Those, similarly, try to share with "everyone" except those who the author doesn't approve of, and such a license leads directly into a messy analysis of whether you would qualify to use that bit of software, because *none of us* knows everything that we support.

Seriously, you might *want* to oppose slavery, child labor, open-pit mining, and the mining of conflict minerals, but [manufacturers turn an indifferent eye to their supply chains](https://journalistsresource.org/economics/conflict-minerals-responsible-sourcing-3tg/), meaning that buying the computer in front of you *right now* might have violated human rights treaties.  Do you *really* qualify to use that code, then...?

More broadly, though, if they change the technology or the terms *used* for the specific technology, does the hypothetical anti-AI license still apply?  Or could an organization point an AI to their servers, then use your code or art for something completely unrelated, and then claim that they didn't actually feed your work into the training set?  Bad actors delight in finding loopholes in contracts and licenses, after all.

You'll note that I have a similar objection to non-commercial licenses, that large media companies routinely structure themselves to deny the profitability of something, so they don't have a huge leap to structuring a single project---that earns them a ton of money---as a non-commercial endeavor.  In the same way, it doesn't seem difficult to structure a project so that it only doesn't shovel your work into an AI while you look at it, but a *different* project indirectly does so by coasting through vague wording...

## Attacking the Wrong Issue

In addition to the problems with the premise, the idea that you'll share the code with anybody, provided that they don't use it in training data also **misses the point**, by substituting a field of research for problematic behavior.  If you find yourself supporting a license with an anti-AI clause, you'd probably feel guilty if a young person asked you why they can't use your work for their science fair project or personal explorations.

In other words, I don't think that "you"---the hypothetical person agitating for license updates---actually care about the field about artificial intelligence in general or large language models in particular.  Instead, you care that **billion-dollar companies** want to turn a profit on your work without compensating you.

Making "AI" an issue instead of "big-corporate abuse" means that academics and hobbyists can't legally train a language model on your code or art, even if they would otherwise happily comply with the license.  If you slap on a license that forbids usage in AI experiments, you'll harm the curious kids, who might want to avoid offending an artist who they respect, but not the enormous corporations.  Why?  Well, we need another heading for that...

## Copyright?  Never Heard of Her...

If you take nothing else from this post, make sure to understand this:  The enormous companies slurping up all content available on the Internet **do not care about copyright**.

The GPL and Creative Commons Share-Alike licenses *already require* licensing derivative works under the same terms, as compensation for using the work.  All Creative Commons licenses (except for CC0) already require attributing the creator of an underlying work.  The companies in question already don't do those things.

In fact, OpenAI refuses to follow copyright law *at all*, even arguing in court that they [need to indiscriminately slurp up copyrighted works](https://www.theguardian.com/technology/2024/jan/08/ai-tools-chatgpt-copyrighted-material-openai).  Likewise, Apartheid Clyde himself says that [the Singularity will solve the problem](https://www.techdirt.com/2023/11/30/elon-says-copyright-ai-lawsuits-dont-matter-because-digital-god-will-arrive-before-theyre-decided/) by outgrowing our petty human problems.

In other words, they believe something between that they don't need to care about copyright, because everything they do falls under [Fair Use doctrine](https://en.wikipedia.org/wiki/Fair_use), and that their religion demands that they violate copyright in order to manifest their libertarian god.  And because of that position, adding a clause to your license that says, "hey, if you train AIs, leave me out of it," has no meaning to them.

Let me repeat:  They already violate Free Culture licenses.  They don't attribute the use of Creative Commons works.  They don't require that their users share the bits of code from copyleft-licensed sources under the same license, or even warn users that they may need to do so.  The *specifics* of the license don't matter to them at all.

### Enforcement

By the way, I should point out that licenses don't ever *prevent* anything.  A public license tells the public what you will *let* them do with your work, without requiring a private license.  CC BY-NC-SA or whatever doesn't exactly erect a force field around your work that gives a little zap to anybody who tries to make money off it.

No, you prevent people from using your work by taking them to court to enforce your copyright, or at least threatening to do so.

Do you plan to sue OpenAI, Google, Microsoft, and whoever else has a popular model?  Can you prove that you have standing?  Do you have compelling evidence that they have financially harmed you?  If not, then your license won't help you anyway, no matter what it says.

## The Bubble

I've already talked about this sort of thing on the blog, but licenses tend to inherently lag behind the times.

For example, the [FSF has never cared about anything unless Stallman personally cared about it]({% post_url 2021-05-09-fsf %}) on his personal computer, and they've recently proven that he matters to them more than their community.  That behavior prevents the organization from keeping up with the times.  As a key example, consider the [AGPL](https://www.gnu.org/licenses/agpl-3.0.en.html), which they have kept isolated from the "real" GPL for *seventeen years*, as if "the web fad" will blow over any day, now.  Likewise, Creative Commons refuses to engage with the problems and confusion caused by their continued support of the noncommerical licenses.

Meanwhile, as opposed to the web, the AI field---with its [Frosty the Snowman ethos]({% post_url 2024-02-25-ai-doom %}), aforementioned religious fervor, almost total lack of a single viable product, and [promises that haven't changed in nearly seventy years](https://theconversation.com/weve-been-here-before-ai-promised-humanlike-machines-in-1958-222700)---[looks a lot like an economic bubble](https://pluralistic.net/2023/12/19/bubblenomics/#pop).  By the time these organizations release their shiny new licenses that will forbid hobbyists from playing with their works while not impacting the big companies at all, big companies may have already fled the AI market, precisely as everyone fled [Web3](https://en.wikipedia.org/wiki/Web3) when nobody cared, then the NFT market when it collapsed, and as they may need to [flee the quantum computing market <i class="fas fa-copyright"></i>](https://spectrum.ieee.org/quantum-computing-skeptics).

If you don't believe that we have a market bubble, consider OpenAI's assertion (mentioned above) that they can't survive if people enforce copyright.  Or maybe consider their insistence that "emergence" will give them real products, rather than any process that they have in mind.  If you don't like those, then try the claim that they [can't survive without nuclear fusion <i class="fas fa-copyright"></i>](https://www.reuters.com/technology/openai-ceo-altman-says-davos-future-ai-depends-energy-breakthrough-2024-01-16/) breakthroughs.  When someone tells you that, before they pay you back as an investor or debtor, they only need widespread changes or exceptions to the law, an amazing product to fall into their lap, and different laws of physics, they...don't actually plan to give you your money back.  And when someone says that to many investors, you have a bubble.  You probably also have fraud, but I probably don't get to judge those things.

## What Do We Do, Then...?

Look, I get it.  The language-model people feel constantly *exhausting*, pretending that their systems produce valuable art.  And their disinterest in copyright law will make a mess of a lot of things.  But asking organizations that don't care to add restrictions to a license that the companies already don't read won't solve the problem.

What might solve the problems, then?  Well, I don't have a comprehensive plan, but I have some vague thoughts that might help the next person point to something better.

### Let It Wither Away

Consider waiting for the AI-bubble to burst.  As mentioned, without a constant supply of investor money, they can't afford to pay the power bills without somebody inventing a working fusion reactor for them.  They can't operate unless courts consistently allow them to ignore copyright.  And even if they get cheap electricity and free rein over copyright law, then they still need investors (and you) to believe that their language games will accidentally become actual intelligences, at some point, worth more than twenty bucks per month to access.

...Or consider hastening the bursting, by making it clear that we don't see a serious future in these technologies.  We don't fear them or see them as saviors.  We see the Markov process that makes the neural network look like it can do work.

Hastening might involve walking away from products and services as companies force their AI products into them, so that they can't claim that everybody uses the product.  That will take actual work.

### Enforce Copyright Law

Some people have started thinking about this.  Matthew Butterick and many open source authors have [lawsuits against GitHub <i class="fas fa-copyright"></i>](https://githubcopilotlitigation.com/) ongoing for Copilots clear use of GPL-licensed code without proper marking.  Several high-profile [media outlets have sued OpenAI <i class="fab fa-creative-commons-nc"></i>](https://www.commondreams.org/news/the-intercept-open-ai) for violating their rights under the [DMCA](https://en.wikipedia.org/wiki/Digital_Millennium_Copyright_Act).

Individual authors also tried to sue as a group, but apparently [misunderstood copyright so grossly](https://www.techdirt.com/2024/02/15/as-predicted-judge-dismisses-nearly-all-of-sarah-silverman-michael-chabon-and-other-authors-lawsuits-against-openai/) that the judge threw out most claims.  I imagine that they assumed that the big names involved would gather enough media attention to shame OpenAI into making some concession, but their utter ineptitude---and their inability to keep the story in the news---makes it more sad than anything else.

Despite the authors, though, I do see a legitimate path to forcing the purveyors of AI products to at least credit the work that they use.  As I mentioned in my [rundown of GitHub Copilot]({% post_url 2021-11-03-copilot2 %}), all these systems can reproduce the text of any public license, if you request it.  And that can only happen if its training data includes plenty of examples of those licenses, as you'd find packaged along with works under those licenses, meaning that anything that it produces adapts those works without following---or warning the users to follow---the terms of the license(s).

#### Caveat

I should point out that taking this route consistently could cause more problems than it solves.  By normalizing copyright lawsuits, we strengthen the precedents for other copyright lawsuits, including undermining Fair Use doctrine, by corporations wanting to suppress expression of various sorts.  I don't believe that anybody reading this wants that.

### Enforce Antitrust Law

This seems shakier, maybe, but as I mentioned at the top, it doesn't feel like a serious position to object specifically to training neural networks, when the problems seem to actually come from large corporations insisting that they can do whatever they please.  And in all honesty, at this time, we really only have one company of significance in this market, OpenAI.  Sure, Google has a system that so few people care about that it [secretly pays media outlets to use it <i class="fas fa-copyright"></i>](https://www.engadget.com/google-is-reportedly-paying-publishers-thousands-of-dollars-to-use-its-ai-to-write-stories-215943624.html).  And Facebook fell on its face when someone leaked Llama, and now wants to build an even bigger language model.  Behind closed doors, assume that Apple and Amazon also waste money on this, too.

For most people, though, you only have OpenAI, someone (like Microsoft) who sits on top of OpenAI, or a much smaller model that you run on commodity hardware for yourself.  And that seems like a monopoly, and maybe something that we should do something about, to increase competition in the space.  Let the companies fight it out---burning investment money in the process, to call back to the issue of waiting things out---rather than giving them opportunity after opportunity to present a united front.

#### Caveat

Note that this route would require the cooperation of consumer-protection bureaus, but many of them do seem receptive, these days, to actually trying to protect consumers, so we shouldn't dismiss it as impossible.

### Stop Taking AI Seriously

Finally, and this seems like the most approachable solution that touches the rest, we could stop taking people seriously when they use AI-generated content.  I've mentioned before that [AI can produce decent placeholder work]({% post_url 2024-01-21-paid-ai %}), but you need to hand that off to someone with enough context and interest to get something that makes sense.  If you don't pass it through someone who cares, then you publish the equivalent of [lorem ipsum](https://en.wikipedia.org/wiki/Lorem_ipsum) or a test image.

And I feel like we need to start treating the purveyors of AI-generated "work" as if they did exactly that.  Too often, people focus on correctable details.  It feels tempting to react to the *flaw*, rather than the process.  Currently, we often take offense if ChatGPT provides false information.  We complain when someone shows a hand with the wrong number of fingers.  Or we laugh that someone used a French translation of [soy protein](https://en.wikipedia.org/wiki/Soy_protein) that declares *je suis une protéine*.

When we do that, though, we have it wrong.  The technical details don't matter.  In theory, chatbots *could* fact-check their output.  With enough training, image generators *could* get anatomical features straight.  And given enough context, automated translation *could* distinguish the legume that we call soy from the first-person singular, present-tense form of [*ser*](https://en.wiktionary.org/wiki/ser#Verb_14).  Complaining about those errors plays into the narrative of the people who want you to invest in AI.  It suggests that they only need more investment to finally replace those pesky employees.

Instead, rather than complain about the technical errors or laugh at the corporation that didn't bother to double-check their product, we should *instead* think twice about interacting with the people behind it.  After all, if they didn't care enough to have a person do the work, if they didn't bother to have a person *check* the work, and if they didn't think that their product needed art suited for it, then do you really think that they treated the rest of their work differently?  Their use of AI serves as a signal of their view of the relationship, not a distinct moral failing.  They believe that nobody cares about quality, and so producing garbage cheaply will serve them well.

And it *will* serve them well, until people start shunning them for not doing the work to produce things that make sense, that show a care for the end result.  I don't mean shunning them by expressing outrage at the "creepy AI images on food-delivery websites" stories that show up every few months.  I mean refusing to engage with the entire AI economy, from the providers down to the articles about bad uses.

### Better Licenses, Too, Maybe

Despite my not seeing a use in new licenses that will ban the use of code or art in training neural networks, I've said since almost the start of this blog that [we need a better licensing regime]({% post_url 2020-03-29-copyleft %}).  I don't know if the copyleft license that I fantasized about four years ago would fix any of these problems, but I do know that a license that carried clear instructions for compliance and a comfortable path for enforcement would certainly make the situation less fractious.

For example, I think a lot of how the aforementioned AGPL tries to handle this.  Section 13 says that, *if* you have users accessing the software across a network, and *if* you modified the software, then (and only then) you must offer those users an opportunity to receive the modified source code.  And---returning to the short-sightedness of these agencies---we could probably all think of a dozen ways that you could grossly violate the spirit of the license while complying with its letter.

And...it doesn't need to do it that way.  It could think about code as data, or the ability to reconstruct the code, or any number of ideas that would make this less prone to abuse.

## You Get the Idea...

I could go on, but I've already probably hammered the point into the ground, by now:  Fighting AI projects with copyright won't actually stop any of these companies, and while failing, it distracts from far more important problems with the overall movement.

* * *

**Credits**:  The header image is [Symposium Cisco Ecole Polytechnique 9-10 April 2018 Artificial Intelligence & Cybersecurity](https://www.flickr.com/photos/117994717@N06/40466252685) by [Ecole polytechnique](https://www.flickr.com/photos/117994717@N06/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/) license.
