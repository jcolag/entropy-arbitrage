---
layout: post
title: The Parler Problem
date: 2021-01-17 07:38:23-0400
categories:
tags: [socialmedia]
summary: An attempt to understand why right-wing social media fails
thumbnail: /blog/assets/136733958_d19086fe20_o.png
offset: -22%
update: 2019-12-20-social-media.md
proofed: true
---

![Free speech](/blog/assets/136733958_d19086fe20_o.png "Free speech")

When I started **Entropy Arbitrage**, the one post I had (mostly) ready to go for a long time was [Social and Anti-Social Media]({% post_url 2019-12-20-social-media %}), mostly beating up on the major social media sites for their participation in "outrage feedback loops."  That is, they refuse to moderate fascists and bigots, because fascists and bigots reliably make everyone (including themselves) angry and/or afraid.  Anger and fear are easy emotions to provoke and maintain the attention of our "lizard brains," while also wearing down our critical thinking.  With attention focused and little skepticism, we're more likely to pay attention to advertising.  And advertising brings money in to fund the site.

The year 2021 has brought a different question to attention, though:  What happens when those social media sites actually *start* doing their jobs and moderate away violent rhetoric?

## Background

If you're coming to this post much later or from some alien planet, fascist Americans [pushed their way](https://www.commondreams.org/news/2021/01/06/pictures-pro-trump-mob-storms-us-capitol-building) into the United States Capitol after it was suggested by Donald Trump.  Many of them wore t-shirts about the civil war they thought they were sparking, and many had weapons and restraints that prove they were planning to take hostages and at least threaten to kill people.

As a result, after four years of saying that Donald Trump is such a special case that his platform to undermine democracy and incite violence couldn't be muted or else we'd lose those tweets from the historical record, Facebook finally grew a spine and [suspended him](https://www.voanews.com/usa/facebook-suspends-trumps-account-wake-us-capitol-violence), followed by [Twitter](https://www.commondreams.org/news/2021/01/08/after-inciting-deadly-invasion-us-capitol-twitter-permanently-suspends).  Those actions---only semi-reasonable when taken *after* the damage had been done, and they've been warned forever---cascaded into bans of violent rhetoric and the people who spew it across most major social media platforms.

That cascade more or less ended with Amazon realizing that [hosting Parler was a huge liability](https://www.techdirt.com/articles/20210111/09253546032/slope-gets-more-slippery-as-you-expect-content-moderation-to-happen-infrastructure-layer.shtml) and kicking them off their cloud computing platform.

## Déjà Vu All Over Again

What spurred my interest in the story is partly that Peter Sunde of the Pirate Bay gave an interview mocking Parler for not being able to stay online.  But partly, it's that we keep coming through this cycle, and none of the sites can be bothered to learn from their predecessors.  It's always...

 * Fascists get themselves banned from popular social media sites, usually by repeatedly advocating for violence in clear violation of the site's terms of service.
 * Fascist politicians wring their hands about "free speech," ignoring the bills they try to pass allowing people to literally [murder protesters](https://www.commondreams.org/news/2020/11/19/utah-lawmakers-accused-seeking-legalize-drivers-running-over-street-protesters), the attempts to [ban certain kinds of protests](https://en.wikipedia.org/wiki/Flag_Desecration_Amendment), the actual laws [de-platforming genuinely vulnerable people](https://www.commondreams.org/views/2018/03/08/stop-sestafosta-dont-let-congress-censor-internet), and the fact that inciting violence is *never* protected speech.
 * Some wealthy right-wing techie says "we'll show them by holding an [anti-prom](https://en.wikipedia.org/wiki/Anti-prom)."  Or "we'll have social media without moderation," rather.  Same difference, really.
 * It turns out that [nobody really wants to be on the new site](https://www.techdirt.com/articles/20200717/15234244920/trumpian-loudmouths-apparently-losing-interest-parler-with-no-one-to-play-victim-to.shtml), because the value of social media is the size of the "market," interaction design, and the millions of dollars spent on reliability engineering, so the site sheds users over time.
 * The people who stay on the new site are the most radicalized, and further radicalize each other, eventually openly advocating and planning violence, which brings legal scrutiny, because---again---inciting violence is never protected speech.
 * The new site gets de-platformed for being too big a legal and financial liability to all their vendors, because it turns out that it's hard to sell to the majority of customers, when you support the people who'd like to murder or otherwise disenfranchise them...

There's an added twist, this time around, that progressives are *also* lining up to [complain about tech companies de-platforming Donald Trump](https://www.commondreams.org/news/2021/01/13/kicking-trump-social-media-wont-save-democracy-say-antitrust-experts), arguing that it's unfair to leave the call to remove him down to human judgment.  But strangely, none of the people framing it this way complained that he was *not* removed the first time he said something that violated their terms of service as would (and does) happen to any powerless user and none of them are interested to connecting this to times when ordinary, non-authoritarian people have been harmed in the past, as cited above.

<iframe
  src="https://archive.org/embed/after-the-capitol-riot-social-media-wrestle-with-the-aftermath-of-blocking-president-trump-source"
  frameborder="0"
  scrolling="no"
  allowfullscreen
  width="740"
  height="416"
>
</iframe>

I mean, I agree that we shouldn't be relying on authoritarian dictatorships---which, at heart, is what a corporation is, unless it's specifically engineered *not* to be---but this isn't the context where that argument is useful, because [it's a necessary step](https://theconversation.com/does-deplatforming-work-to-curb-hate-speech-and-calls-for-violence-3-experts-in-online-communications-weigh-in-153177) to stopping the violence.  When you remove an online meeting place for bad people, only the most dedicated people search out the new meeting place, giving an opportunity to "deprogram" the people conned into the cult.  But the fact that de-platforming doesn't deprogram by itself doesn't make de-platforming bad.

So nobody really learns anything, I guess.

Other than *that*, though, we've seen this most of this entire cycle with Gab, [Minds]({% post_url 2020-02-01-minds %}), Voat, 8Chan, [ZeroNet]({% post_url 2020-02-22-zeronet %}), and others, and none of the sites have been relevant after their figurative fifteen minutes of fame.  All the "Twitter-killers" that we've seen are basically irrelevant to most people, except as evidence to arrest people for planning terrorist attacks.

## But Wait, There's More...

There's *another* twist, though:  Parler apparently had [terrible security and amateur coding](https://ediscoverytoday.com/2021/01/13/parlers-free-speech-may-have-been-a-little-too-free-cybersecurity-trends/), allowing pseudonymous activist @donk_enby to download the majority of the public contents of the site *with* geolocation data.

The short version is that every post was just given the next number as its ID.  So, if you want everything, you ask for post #1 and start increasing that number until the responses start coming back empty.  Because of that, you don't need to care about who was involved in any particular conversation; you just want that next number.

To be clear, you really never see this.  Twitter seems to use a modified timestamp for its post IDs, but it's modified enough (and there are some safeguards in place) to prevent scraping the entire site.  About the only place where you *might* see it is on small-scale e-commerce sites for order numbers, especially for shops that don't maintain an order history, because that order number is then meaningless.

## If You Order Now...

So, we have some basic facts, here, to put together.

 * Conservatives do this often.
 * Every attempt has been a flop.
 * Most of the sites quickly run afoul of the most basic publishing laws.
 * They aren't diligent enough to protect their users.

That combines to tell me that these aren't serious projects meant to enable a thriving community of conservatives, or even serious projects meant to give QAnon someplace to drain into after being flushed by everyone else.  Instead, they seem to be somewhere between a grift to scrape up advertising (or subscription) money from terrorist-wannabes---mercenary magazines used to play this role, back when I was a kid---and a bluff hoping to get back access to the much larger communities that the major social media sites have cultivated, by claiming that [the grapes are probably](https://en.wikipedia.org/wiki/The_Fox_and_the_Grapes) [too sour to eat](https://www.voanews.com/2020-usa-votes/trump-says-he-will-not-attend-bidens-inauguration).

Oh, and there's an entire *separate* discussion to be had (in theory, at least) about how these sites never cooperate with what already exists in their space, but they always insist on relying on infrastructure that someone else owns, even though they know that's going to cause trouble in the future.  That's another sign that this isn't meant to stand on its own.  They want Amazon's servers, Twitter's audience, and Apple's name, but they don't want oversight from any of those organizations.  It's like how, when right-wing extremists talk about building their own, isolated community, they always move somewhere like New Hampshire with working utilities and functioning government, rather than somewhere like [Bir Tawil](https://en.wikipedia.org/wiki/Bir_Tawil) that they could prove their ways work.

Because of that disinterest in being what they claim, however, they shine a great spotlight on what a social network or other community system should actually be:  You only have a community when people (inside and outside) are safe and there's sufficient moderating force to *ensure* everybody's safety.  You only have a community when you're willing to work with others, instead of trying to re-invent everything from scratch and deny the legitimacy of everybody else's rules.

* * *

**Credits**:  The header image is [Winter arguing with Summer about which is the best season](https://www.flickr.com/photos/56832361@N00/136733958) by [Karen](https://www.flickr.com/photos/56832361@N00/), released under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
