---
layout: post
title: Payment Processing
date: 2025-07-27 08:02:12-0400
categories:
tags: [harm, lets-fix, project]
summary: Thinking about how we might create an independent payment processor
thumbnail: /blog/assets/27983878461_3450381f31_o.png
description: Roughing out a federated payment processor that can resist censorship, but lacks a huge piece.
spell: ons sequenceDiagram endmermaid mh defederation defederating
proofed: true
---

* Ignore for ToC
{:toc}

This post might not go anywhere, but the recent incident of [Itch.io "de-indexing" adult content](https://itch.io/updates/update-on-nsfw-content)---due to pressure from the credit card processors, themselves under pressure from some "religious" group that believes that their religion demands imposing their personal views on everyone else---reminded me that we go through this frequently, where some artistic subculture gets cut off from its fans, because some oligarch decided that the work reminds them of pornography in some way.  And because of that, I have started thinking about the possibility of some alternate payment regime.

![A pile of coins](/blog/assets/27983878461_3450381f31_o.png "We want a system more convenient than this, but equally flexible")

I should probably point out that, in some ways, this probably doesn't look like my fight.  You probably won't find me selling not-safe-for-work projects, and I don't really engage with them, unless I have some other purpose for it, such as wanting to highlight it for the [Free Culture Book Club](/blog/tag/book-club).  However...

1. *People*.  We should all support and at least try to protect people, and at least stop trying to find the division that makes things not our problem.
2. I see adult material, people representing gender and sexual minorities, and sex workers as the social backbone of the Internet in many ways, and so if you make the Internet useless to them, then everything else starts fading away, too.

At this point, I only really intend to do some of the broad thinking about this, because I don't know that the resources exist to fill this out.  But if somebody can fill in those blank spaces and, especially, if people want to collaborate, I'll do what I can to help get this off the ground.

## Disregarded

I should note that, while these come across as popular "solutions" to this sort of problem, I have a handful of ideas for directions to avoid.

First, cryptocurrencies seem out of the question.  Even their most zealous boosters don't actually use them as money.  As I once wrote, the design [revolves around waste]({% post_url 2021-05-16-crypto %}) to simulate the physical effort involved in mining precious metals, and so both has a nasty environmental footprint *and* serves to make the rich richer.  And because they designed the entire system to reject the "bloated" modern economy, they constantly find themselves needing fancy new innovations such as "escrow" or "insurance."

Similarly, but for different reasons, I immediately write off community currencies.  I have always loved the idea, but if we can't guarantee that a vendor can pay their bills with hypothetical "Sim-ally-ons," then it doesn't make much sense to pay them in it.

Then, going off to find yet another platform that hasn't needed to cave to these demands to keep their company in business...works in the most literal sense, but really only kicks the can down the road, until somebody pressures Mastercard to harass the next site that everybody moves to.

Finally, I think that actually handling money goes right off the table.  The regulatory hurdles make that too difficult to get moving without involving all the same oligarchs who have caused these problems.

## My Core Idea

After taking a few days to roll this problem around in my head, I ended up with the following broad architecture to manage the transaction.

### Overall Process

Overall, the payment processor looks like a managerial layer.  I envision a transaction that looks something like this.

- On the vendor's website or equivalent, the customer creates an order.
- The vendor's website connects to the payment processor to issue an invoice to the customer for the appropriate amount.
- On receiving the invoice, the customer leaves the payment processor for whichever person-to-person payment service this processor supports.
- The customer returns to the payment processor, specifying their transaction number for the payment processor to independently confirm succeeded, and had the proper amount and recipient.
- The vendor now has an obligation to deliver.

Actually, maybe a diagram with more detail would make that clearer, including all four parties.

{% mermaid %}
sequenceDiagram
  Customer->>Vendor: Place Order
  Vendor->>Processor: Request Invoice
  Processor->>Customer: Send Invoice
  Customer->>Bank: Send Payment to Vendor
  Bank->>Vendor: Complete Payment
  Bank->>Customer: Receipt with Transaction ID
  Customer->>Processor: Report Transaction ID
  Processor->>Bank: Does Transaction Match?
  Bank->>Processor: Yes/No
  Processor->>Vendor: Order Complete (or not)
  Vendor->>Customer: Deliver (or not)
{% endmermaid %}

It places a slight burden on the customer, but it also puts them in control of the transaction, and verifies that they have held up their end of the bargain.  And, again, limiting this to no more than coordinating the parties prevents this from becoming a [Money Services Business](https://en.wikipedia.org/wiki/Money_services_business) that then requires a pile of [Money Transmitter](https://en.wikipedia.org/wiki/Money_transmitter) Licenses.

### Choke-Points

I should add one more twist to the above process, because the concern about pressuring organizations into complying with the whims of oligarchs doesn't go away if this only creates a new organization or company.  As such, we would probably want to decentralize it.

Imagine something like Mastodon, maybe even using ActivityPub, sending end-to-end encrypted messages between the customer and vendor.  Now, pressure campaigns look like moderation.  Your faux-religious fanatic can scream all they like about adult content, but federating provides an extra layer of insulation from such censorship.

Specifically, a central distribution site such as Itch.io, in this scenario, doesn't necessarily have a single payment processor, but rather a cluster of small processors all on the same network, so they don't generally need to worry about social pressure.  You could try to pressure the independent processors---the aspect outlined in this post---but they would get managed by the equivalent of local Mastodon moderators, who might respond politely and might tell you where you can get off, so probably wouldn't defect on average, and those who would probably already don't allow such things on their platform.  You can try to pressure the underlying money handler, but they don't know anything about this big website or the payment processor, since they don't interact.

{% mermaid %}
flowchart TD
  v1[Vendor] --> sf[Store-front]
  v2[Vendor] --> sf
  v3[Vendor] --> sf
  sf --> p1[Processor]
  sf --> p2[Processor]
  sf --> p3[Processor]
  p1 --> c1[Customer]
  p2 --> c2[Customer]
  p3 --> c3[Customer]
  p1 --> c4[Customer]
  p2 --> c5[Customer]
  p3 --> c6[Customer]
  c1 --> mh[Money Handler]
  c2 --> mh
  c3 --> mh
{% endmermaid %}

As far as the money handler knows, they only have individuals sending each other money.  As far as the centralized store knows, the majority of payment processors don't care what they sell.

In other words, the infrastructure places a "storytelling layer" on top of personal transactions, which directs the participants to make things work as if the system handled it, but little more than that.

This doesn't insulate sales from the law, I don't think, because a sting operation could always make a purchase and use that as evidence against the vendor.  But this avoids creating any central target; law enforcement would need to investigate each suspect individually, rather than raiding a company.  And they need a reason to investigate, rather than asking a company to avoid certain legal classes of material.

### Encryption, Too

Note that, with end-to-end encryption in the software, the payment processor might not even know what kinds of transactions go through.  They only need to see where money goes, not why.

Likewise, going back to the broad process, the invoice could include a "token"---some encrypted data that the customer uses in their payment to connect it to their order---which also prevents the money transfer platform from knowing anything about the transaction beyond the amount, sender, and recipient.

Ideally, I'd like it if customers had some way of shielding their identities from vendors, too, but I suspect that none of the transfer platforms would allow that.

## Big Problem

OK, now that I have provided a rough outline of what I want to build, we can get to the core issue, the thing that it needs to get working.  And I see a huge gap, here:  This system requires some way of transferring money that has all the following criteria.

- Uses real money, not cryptocurrency or some random scrip.
- Issues a unique identifier for every transaction.
- Allows a third party to ask if that unique identifier equates to a transaction that conforms to the agreement.

Ideally, it would also have a low enough barrier to entry for both the instance operators and customers that making a purchase doesn't become an ordeal.  Regardless of that, though, the third criteria on the list feels like the problem.  Without the ability to hit an API endpoint to ask "did transaction-A send amount-B from entity-C to entity-D at time-E?"---which shouldn't violate any privacy concerns, because only the two entities and their agents would have all five pieces of information, and then would only return true or false, not additional details---then this can't separate out the (rare) dishonest claims.  If I can claim that I sent money that I actually kept, or that I failed to receive money, then this sort of system would actually make payments *less* useful than vendors hanging out a Venmo/Zelle/Stripe/whatever shingle and waiting for prospective customers to take the risk, because it adds a layer that might disagree with the payment transfer infrastructure.

Yes, most transfer systems allow you to give a third party read-only access to your account for auditing purposes, but...would you trust the equivalent of a local Mastodon moderator---or possibly multiple operators across multiple instances, depending on the specific design---with access to all your transactions under the pretext of validating a single purchase?  And yes, "we should encrypt that," but with an open protocol, how do you know *when* the interface encrypted the data?  Your particular instance could run different software, to broaden the resilience of the ecosystem, but now you need to trust so many more unpaid, unregulated volunteers to get this right.

### Other Questions

While the above feels like it represents the biggest obstacle to this sort of project, I also have more nebulous concerns about keeping such an enterprise running.

For example, how does this fund itself?  For the existing Fediverse, I think that we have already seen that you *can* expect volunteers to host and moderate your instances for you, but you shouldn't.  As an instance grows, it no longer costs three bucks per month---already out of range for many people---to run the server, and moderation takes up more time and more of an emotional toll.  And that space traditionally only needs to moderate polite conversation getting heated, not money.

We might imagine taking a cue from the existing payment processors, requiring some payment for participation, whether a flat rate or based on the amount spent/received through the system, but people will use that as an excuse to jump back on the next platform that claims queer-friendliness until Mastercard asks them to stop or the company wants to go public.

Then, I wonder how this would look---if it can present itself at all---to a larger platform like Itch.  Can a site use an API on some instance and/or implement something like ActivityPub and allow their participants to take payments?  Or does the federated architecture mean that it makes more sense for every vendor to set up their own store, with all the added burden that entails, and a unified retailer ends up looking like [Threads](https://en.wikipedia.org/wiki/Threads_%28social_network%29), a possible vector for getting people interested, but too big and dangerous to actually work with?

And speaking of actually working with entities, what about defederation?  On some levels, it seems entirely appropriate for each instance to have their own philosophies of what they will and will not allow on their platforms.  If I ran an instance, I might have a legal obligation to block the sale of what we now call "abuse material" of various sorts, plus a personal inclination to block art not released under a Free Culture license.  Some reactionary group might want to block queer content.  You might want to block guns.  That all makes some sense.  Different communities want their resources used to support different things, even though we might not all agree on the specifics, and might even think that each other's choices do harm, but we generally respect that.

What happens, though, when the differences become so extreme that instances begin defederating from each other?  On the existing Fediverse, defederation means that messages stop going through, a sanction against an instance in hopes of convincing it to improve its behavior, while also protecting your own instance against their bad behavior.  But when you have money at stake and possibly in transit when somebody makes the decision to cut ties, somebody needs to figure out how to make that work.

Even without defederation, sometimes sites vanish.  An administrator might run out of money or interest.  Somebody using the instance might have committed a significant enough crime that law enforcement shut the entire thing down for forensic purposes.  Or the server might have had some technical problem, like the hard drive running out of space.  If somebody started a purchase, and then one party drops off the Internet, how do you recover that?

You can at least mitigate, if not completely solve, all these problems, but they each involve trade-offs better made by a group.

## Incompleteness

Like I said, this feels like a *necessary* project, going forward, but I lack the resources to pull it off.  And I mean that both in the sense of having the time and energy to put the thing together *and* lacking that critical service that would make this work.

If, however, this project appeals to you, and especially if you have one of those missing pieces---time, energy, awareness of a service that provides the magic validation API---then absolutely...

- Get in contact through the usual means so that we can try to formulate a plan, *or*
- Take anything from this post that resonates with you and run with it without me.

Seriously, I'd rather see the project happen than have someone worried that they needed to leave me out for reasons ranging from perceived access to disinclination.  As such, I'll try to make myself available to whoever wants me involved and happily stay clear of anybody who doesn't...

* * *

**Credits**:  The header image is [money](https://www.flickr.com/photos/119931838@N08/27983878461) by [Piotr](https://www.flickr.com/photos/fruitsailor/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license.
