---
layout: post
title: Software as a Haunting (SaaH?)
date: 2023-08-06 07:06:12-0400
categories:
tags: [philosophy, programming, rant]
summary: Rolling a possibly useful metaphor around.
thumbnail: /blog/assets/black-and-white-house-window-building-chateau-old-1264128-pxhere-com-pdf-js.png
offset: -40%
teaser: While I don't become a spiritualist, I do try to make a serious case for thinking of code as ghost-like, and what that might mean in general.
spell: SaaH Grabiński Szary pokój mana heritor hauntings PxHere
proofed: true
---

* Ignore for ToC
{:toc}

As many readers probably know, I like to think of different interesting ways to explain things---particularly software-----to people.  It probably comes from the days when I had a day job *and* taught both graduate computer science classes and adult education computer classes, where each of those contexts differs dramatically in terms of background, interest, and patience.

![An old, run-down house with a "haunted" look to it, with JavaScript code pushing through the structure](/blog/assets/black-and-white-house-window-building-chateau-old-1264128-pxhere-com-pdf-js.png "Would the property values rise or sink, I wonder, if we changed the code to Oberon or Leda...")

Often, I don't talk about it much, because it would take extreme education to get me up to speed on the proper metaphor before I could sensibly present it to someone else.  For example, to me, programming strongly resembles anthropology, in that (among other disciplines) we study how people can best make use of artifacts and how our predecessors worked with and understood problems.  We call those ideas "user experience" and "debugging," but they run at least parallel to anthropological ideas.  Or we can talk about programming as storytelling, or any number of other fields.

Today, though, I want to talk about something maybe odder, the idea of software as *haunting*.  Let's go bust some ghosts.

## Wait, What Now?

To clarify, I don't mean that code has any supernatural aspects to it, but neither do I mean the title as "clickbait," suggesting something completely absurd to get people to read my post.  Or to put it another way that people won't find as wild, but also fails to capture the nuance that I'll get into:  Software probably comes as close as a real artifact can to overlapping with the idea of having mischievous ghosts infesting your space.

And no, I don't even mean "sometimes code does things that you don't expect and that seems extremely weird."

...Bear with me.  We need to cover some ground, to get from here to there.

## The Polish Poe

For the majority of people (presumably) not already acquainted, I'd like to introduce you to [Stefan Grabiński](https://en.wikipedia.org/wiki/Stefan_Grabi%C5%84ski), a once-popular-in-Europe writer often referred to as either The Polish Poe or The Polish Lovecraft---as in [Edgar Allen](https://en.wikipedia.org/wiki/Edgar_Allan_Poe) or [Howard Phillips](https://en.wikipedia.org/wiki/Howard_Phillips_Lovecraft)---which might give you some idea of his niche.

I forget where I discovered him, maybe through some Polish colleague in a discussion of interesting authors, maybe some other means.  It probably doesn't matter, other than if someone led me to his work, that person at least deserves my acknowledging that.  I feel comfortable talking about his work, here, because his work should have fallen into the public domain in Poland in 2008, though I won't quote any here, since I don't know of a Free Culture translation.

At any rate, among Grabiński's more interesting ideas---particularly in stories such as *Szary pokój*/*The Gray Room*---he sometimes suggests that what we think of as a ghost actually comes from a sort of (presumably psychic or spiritual) echo or imprint of a prior inhabitant of the space.  This works on a literary level, I think, because it only barely exaggerates how we function in the real world.  We often keep objects around past their usefulness, if its imperfections trigger happy memories, and we might want to get rid of a useful thing if those same imperfections trigger unpleasant memories.

And by the same token, we *create* our own ghosts as we live, wearing down an edge of a table that we frequently lean on.  Or, in other cases, we might spend time deliberately altering something to work better for our purposes, and this connection nicely bridges us from memory to haunting.  After all, how else can we describe a "haunted" space than that, no matter what you'd prefer, you can't use a space or object without feeling the presence of this absent person?

While Grabiński gives this a clear supernatural bend, you can see how he gets there fairly quickly.  If a nicked book spine can remind you of a lost family member, and remodeling by a prior resident of one's home redirects their actions to cope with an odd shape, then---at least in a horror story---we can extrapolate that trend to the idea of an imbued presence that takes specific actions, too.  But as I said, we don't really need the supernatural angle.

### An Added Something

Some readers might note that the supernatural form of this idea already protrudes into our world, in various ways.

In some Melanesian and Polynesian cultures, they have had the idea of [mana](https://en.wikipedia.org/wiki/Mana_%28Oceanian_cultures%29), a spiritual energy ebbing and flowing through everything, making it better.  Some believe that you can place mana into an object, making it more powerful, in some way.

That brings us to the broader idea of enchantments of objects, and we see this *today* in fantasy role-playing games, where a character might have a "+3 sword," a sword that, for magical reasons...does better sword-things.

And many horror stories use a similar idea, often suggesting that ghosts manifest the unresolved traumas faced by the deceased, used---at least in *good* horror stories that will stick with you---as a metaphor for the trauma processed by the living.

I didn't have anywhere to go with that, but figured that I should mention, on the chance that someone had a use for that sort of connection.

## Code as Intention (and Emotion)

I associate this idea with code, because programming revolves *almost* entirely around three things:

We have **intention**, because we want the code to do something.  I've talked about this before, in the context of even the best [AI not replacing programmers]({% post_url 2021-07-18-copilot %}), because someone will always need to figure out how to solve a problem and explain that solution---to varying degrees of granularity---to the compiler or AI.

Then, we have **personal imperfections**, where the developers took shortcuts or otherwise had some quirky idea of how things should work.  The colors that don't *quite* match, the form fields that appear in what feels like the wrong order, the odd phrasing of directions, formatting that only acknowledges the existence of one country, and many more small issues build up to give software the imprint of everyone who has worked on it.  And that doesn't even get to the deliberate "[Easter eggs](https://en.wikipedia.org/wiki/Easter_egg_%28media%29)" inserted into software by developers, for various reasons.

And finally, we have **trauma**, because shortly after we start, we start chasing bugs down and struggling to fix increasingly obscure problems, until either we (somehow) finish or determine that the cost to run down the remaining bugs will overwhelm the value provided by eliminating them.  When you write code, particularly code for other people, you mostly work in a state where you either feel frustrated that you haven't gotten something working *or* move on to the next broken thing.

Even more than most art, I would hazard to suggest, software embodies (at least some aspects of) the intentions and emotional states of its creators.  Sure, I exaggerate the suffering aspects of the job for symbolic and comedic purposes, but you can probably see why I might associate these two ideas.

## Maps and Territories, Too?

To push this a bit further, let's talk a bit about another now-obscure author from Poland, [Alfred Korzybski](https://en.wikipedia.org/wiki/Alfred_Korzybski).

While obscure today, Korzybski once had *massive* influence on today's world.  You probably don't know his name, but you've heard his work echoed when people [mistake the map for the territory](https://en.wikipedia.org/wiki/Map%E2%80%93territory_relation), forgetting that abstractions leave out important issues.  Or you might remember me (or someone else) talking about [avoiding forms of the verb *to be*, for greater clarity]({% post_url 2022-12-04-specificity %}).  You might recognize the references dropped to him in the works of Heinlein, van Vogt, Wilson, Hubbard, and more.  His work helped determine which Nazi war criminals could reasonably stand trial, and (less seemly, through Hubbard) it influenced aspects of [Scientology](https://en.wikipedia.org/wiki/Scientology).

In any case, his first book, [**Manhood of Humanity**](https://www.gutenberg.org/ebooks/25457), presents some ideas that come off as oddball, but have some decent points within those ideas.  In particular, the book tries to make the case that it doesn't help us to think of humans as precisely like other animals, because we definitely differ, nor does it help us to think of ourselves as completely different, since we definitely share a lot with the rest of life on Earth.  He tries to thread this needle as follows.

 > The plants have a very definite and well known function---the transformation of solar energy into organic chemical energy. They are a class of life which appropriates one kind of energy, converts it into another kind and stores it up; in that sense they are a kind of storage battery for the solar energy; and so I define the plants as the chemistry-binding class of life.
 >
 > The animals use the highly dynamic products of the chemistry-binding class---the plants---as food, and those products---the results of plant-transformation---undergo in animals a further transformation into yet higher forms; and the animals are correspondingly a more dynamic class of life; their energy is kinetic; they have a remarkable freedom and power which the plants do not possess---I mean the freedom and faculty to move about in space; and so I define animals as the space-binding class of life.
 >
 > And now what shall we say of human beings? What is to be our definition of Man? Like the animals, human beings do indeed possess the space-binding capacity but, over and above that, human beings possess a most remarkable capacity which is entirely peculiar to them---I mean the capacity to summarize, digest and appropriate the labors and experiences of the past; I mean the capacity to use the fruits of past labors and experiences as intellectual or spiritual capital for developments in the present; I mean the capacity to employ as instruments of increasing power the accumulated achievements of the all-precious lives of the past generations spent in trial and error, trial and success; I mean the capacity of human beings to conduct their lives in the ever-increasing light of inherited wisdom; I mean the capacity in virtue of which man is at once the heritor of the by-gone ages and the trustee of posterity. And because humanity is just this magnificent natural agency by which the past lives in the present and the present for the future, I define humanity, in the universal tongue of mathematics and mechanics, to be the time-binding class of life.

I apologize for his various 1910s-isms, including using the word "manhood" to mean maturity.  In all that, even though it only makes sense with the background, we only really care about one term in there:  *Time-binding*.

Korzybski has the thesis that, where religious people have an inclination to see some sort of divine spark that sets us apart from the rest of life on Earth, we should *probably* see our ability and willingness to *write*, communicating and organizing across broad stretches of time, instead.  If I can oversimplify the quoted passage, I might summarize it as something like "plants make food, animals make homes, and humans (in addition to homes) make civilizations," where civilization arises from multiple generations sharing the same stories.

I want to call this idea out, because it underscores one of the otherwise-unspoken premises of this discussion, that communication has power.  And we don't always keep that power under control, like we should.

## Pulling This Together

In software, then, we have artifacts which hold the imprint of every personality involved in its creation, and those imprints influence and push the people who work with those artifacts.  Beyond the fact that software can accomplish things without human input, if desired, those bits of personality follow along distribution lines and either help or hinder users.

We have, in other words, our hauntings.  The presences that come along with software make an end-user's work more difficult or less, concealed under a more unified presentation, in a way that resembles a hypothetical normal-looking house that happens to have presences left over from prior inhabitants.

## Who Cares, Though?

You raise a good question, headings.

### Thank---

Nope.  No, we will *not* do that.

We might care for a couple of reasons, depending on what tasks we have in front of us.

First, this echoes something that I've written about before, that [all our work embodies values]({% post_url 2020-10-18-stories %}), and we can either choose those values or allow society and our unconscious biases to choose them for us.  As programmers, then, we have an obligation to consider what we bring to projects, in terms of intent and emotion.  If we'll end projects by haunting our users anyway, then we can at least make them benevolent hauntings, more like European [household deities](https://en.wikipedia.org/wiki/Household_deity) than poltergeists.

Likewise, making software "professional" often involves a long process of tracking down and exterminating those idiosyncrasies, to replace them with---in effect---the ghost of the corporation that owns and sells the software.  In that context, the software needs to "speak" with a single voice, not many distinctive voices.

Then, and maybe more usefully in the longer term, this might serve as an entry point into the software industry for someone.  I don't know what that would look like, but could we plausibly pitch programming---particularly debugging, a distinctly unglamorous part of a project, today---with the tropes of a ghost-hunting show?  Could we model certain discussions about these idiosyncratic aspects of presentation after séances, trying to determine what they "want" and what they have to tell us?  The latter implies communicating with communication, which seems like an odd twist on Korzybski's time-binding.

I don't think that I have more than this on the topic, so it'd interest me greatly to hear what other people have to say, here.  Does this come close to holding water as a metaphor?  Does it resonate with you?  What crackpot metaphors for programming have *you* spent the last few years of your life sitting on?

* * *

**Credits**:  The header image is based on [Untitled](https://pxhere.com/en/photo/1264128), by an uncredited PxHere photographer who made it available under the terms of the [Creative Commons CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/) and the [message handler](https://github.com/mozilla/pdf.js/blob/master/src/shared/message_handler.js) from the PDF Reader in JavaScript by the [Mozilla Corporation](https://wiki.mozilla.org/Github), released under the terms of the [Apache 2.0](https://apache.org/licenses/LICENSE-2.0) license, formatted using [Carbon](https://carbon.now.sh/).
