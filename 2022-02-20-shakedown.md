---
layout: post
title: The World's Slowest, Dumbest Botnet ⚠️
date: 2022-02-20 06:50:02-0400
categories:
tags: [rant, copyleft, license]
summary: The shakedown (apparently) sweeping the globe
thumbnail: /blog/assets/2166476315_9b2f8cd945_o.png
offset: -25%
proofed: true
---

I don't know if there's an actual way for anyone but me to see it when it happens, other than monitoring every single page on a website.  However, particularly keen-eyed readers *might* have noticed that I updated the header image for my post on [**Star Trek**](/blog/tag/startrek)'s [*The Apple*]({% post_url 2020-09-10-apple %}).

![Three bristlebots](/blog/assets/2166476315_9b2f8cd945_o.png "Fluor-i-date!")

Since there's a story behind that choice, I figured that it might make a worthwhile post to give a mild warning to anybody else who might work regularly with Free Culture (and similar) works.

## Background

Over the past few years, I've been hearing about the spread of a "copyleft shakedown," most recently from the [attempt to extort money from Cory Doctorow](https://pluralistic.net/2022/01/31/heel-turn/#pixsy).  The short version is that there's a group of people who rely on what I would argue are misinterpretations or misreadings of older/obsolete Creative Commons licenses as the basis for scamming people who use Creative Commons works.

In Doctorow's case, it was someone looking for money, which is dangerous and obnoxious, since the idea in bogus legal threats is always to demand payment that's merely less than it would cost just to show up to defend against a lawsuit.

## The Request

As befits my lesser cultural weight, though, the shakedown that I received was goofier and maybe generalizable to some grand conspiracy.  Specifically, rather than a fake invoice, I got an e-mail that I'll paraphrase, since I'm obviously not going to ask permission to republish it.

 > Hi, we noticed that you are using our design/image on your website, [here]({% post_url 2020-09-10-apple %}).  Unfortunately, the attribution link is not correct.  It should be <https://example.com>, based on the requirements on [the Flickr <i class="fab fa-flickr"></i> page](https://www.flickr.com/photos/156555495@N04/38643510282).
 >
 > Thanks in advance.

That's a real link to my post, a fake link for the web shop, and a real link for the image's Flickr page, in case anybody happens to be visiting Vietnam and wants to replace the original picture more precisely.

Three things immediately caught my attention about this request.

 * The license does *not* actually compel me to link to the creator.  I'm obliged to link to where the creator supplies the image, subject to the creator's approval---to prevent aggregators from getting incidental credit---but that doesn't include a useless page on a purse shop website or whatever they want me to point to.
 * The phrase "design/image"---actually used in the real e-mail, and not something that I invented as a quick joke---screams that this isn't discussed in good faith, because someone legitimately concerned with their credit would clearly know if it's a photograph or not.
 * While I do routinely link to creator websites when I can find them, there is *no* chance that I completely flubbed the URL with an entirely unrelated e-commerce site.

Let's dig into each of these.

### License Terms

We're talking about [Creative Commons Attribution 2.0](https://creativecommons.org/licenses/by/2.0/legalcode), where section 4b outlines the requirements as the following, which I have reformatted for easier reading.

 > If you distribute, publicly display, publicly perform, or publicly digitally perform the Work or any Derivative Works or Collective Works, You must keep intact...
 >
 > all copyright notices for the Work and give the Original Author credit reasonable to the medium or means You are utilizing by conveying the name (or pseudonym if applicable) of the Original Author if supplied;
 >
 > the title of the Work if supplied;
 >
 > to the extent reasonably practicable, the Uniform Resource Identifier, if any, that Licensor specifies to be associated with the Work, unless such URI does not refer to the copyright notice or licensing information for the Work...

The rest is about derivative works, so that last item is what we care about, here:  I'm required to include the address that the creator associates with the work, **unless** the page isn't about the licensed work.

In other words, we're already off to a bad start, trying to lawyer their way around a license that they don't quite understand.  That's not all, though.  There's another aspect to this, which I'll get to, later.

### Uh, Phrasing...?

Like I said, the entire enterprise is suspicious, simply because it's obvious that the person meticulously tracking my use of their work can't be bothered to identify the work by anything other than a Flickr URL.  "Design/image" all but screams using an automated, unmonitored tool to search the web for a bunch of URLs or images, for the purpose of trapping small publishers.

It's not against the law to do this, of course.  But it certainly doesn't incline me to be cooperative.  If anything, behavior like this is only going to spur me to be more critical.

### Mea Culpa?  Maybe Not

While I absolutely do make occasional mistakes in attribution, they're never complete non sequiturs.  When I get a link wrong, it's invariably for using the URL from the image (or whatever it is) for the person, because I didn't copy the right link to the clipboard and didn't notice pasting the same thing twice.  It's not going to be because I arbitrarily replaced the correct URL with some gift shop that I've never heard of, for the simple reason that I don't keep e-commerce URLs in my clipboard.

This last piece particularly caught my interest *because* it's so improbable.  Therefore, I checked the Internet Archive's Wayback Machine, and found that the [photograph was originally posted](https://web.archive.org/web/20190118114327/https://www.flickr.com/photos/156555495@N04/38643510282/) with the same terms, but a *third* unrelated URL.

This brings up an interesting point:  Creative Commons licenses only provide permissions permanently.

 > ...Licensor hereby grants You a worldwide, royalty-free, non-exclusive, perpetual (for the duration of the applicable copyright) license to exercise the rights in the Work...

That was granted to me at the time that I *accepted* it, not today, or subject to periodic revisions.  Likewise, the terms that I accepted can't be retroactively revised.  The owner can't change my license to the GPL or a non-commercial license without my consent; they can only change the license for *future* users, and hope that none of them discover the earlier arrangements, which would still be valid.

It occurs to me that Flickr could use some work, here, too.  They show that the picture hasn't been updated since 2017, because they're not monitoring updates to the image *description*.  They should, because old versions of the text are highly relevant in cases like this, and probably others.

#### Exceptions

When I say that the license grant is permanent, I need to be clear that this ties back into the problem that Doctorow stumbled into:  The second edition of Creative Commons licenses (v2.x) included the right of the copyright-holder to terminate the license if the terms weren't met properly.  If I had gotten the *earlier* versions of credit wrong in some superficial way, they could have terminated my license and would probably have an argument that I need to accept the current version.

{% pull ...included the right of the copyright-holder to terminate the license %}

Even *that* is shaky, though, because "public licenses are forever."  For example, I have released several programming language interpreters under the GPL.  Years earlier, I released some of those into the public domain, because I (frankly) didn't value the work that went into those projects until later.  Despite my change of heart on licenses---something that I discussed in my [Licenses and Copyleft]({% post_url 2019-12-28-licenses %}) post, to some extent---I can't take back those prior announcements.  If someone finds them, they can use the software under those terms, as it existed at that time.

Likewise, if I find earlier citation requirements, it's my choice which terms to accept.

## 20/20 Hindsight

To be fair, I should have realized that this image would have been a problem as soon as I saw the page.  While it claims to use a standard license, it basically tries to write an ad hoc custom license that contradicts the standard in meaningful ways.  That is, I can't legitimately say "I hereby release this software under the GPL, but using it obliges you to e-mail me your tax returns from the last five years."  I can write a *new* license that has those terms, but I can't legally claim that it's the same license or use the issuing organization's name for it.

In other words, I *should* have looked at the attribution requirements and realized that the image wasn't released for reuse in good faith.  I was swayed by the great-looking Vietnamese statue.

## I Love It When a Scam Comes Together

It's reasonable to ask why any of this *matters*, since they're not trying to extort money, like other dishonest Creative Commons users do.  Even I started out considering updating the link for them, just out of politeness, before realizing that updating license terms isn't part of the license.  So, what's really going on, here?

{% pull ...a cheap, manual version of an SEO botnet|left %}

Based on the evidence available, my suspicion is that this is a cheap, manual version of an [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization) [botnet](https://en.wikipedia.org/wiki/Botnet):  The organization provides an assortment of content under a free license, convincing users to link from their websites to whatever site is of interest to them at the time, then asking to redirect those websites as new sites become important.  They're looking for "organic traffic" on demand.  For my company, I get spam almost daily offering quick boosts in search engine rankings, and this is probably part of how that business works.

And here's the problem:  If a site quietly accepts their change of URL, the requests are only going to get repeated as the fake-botnet acquires new clients.  Last week, it was quirky gifts.  This week, it's purses.  Next week, maybe it'll be a cryptocurrency scam or tourism under a repressive government.  I'm fairly certain that a free picture is *not* acceptable compensation for doing the work of goosing the search visibility of random companies.

## Trust

Interestingly, seeing how dishonest this entire setup is raises more questions than it actually answers.  As a simple example, if they're willfully misinterpreting the license, why would I trust that they actually own the underlying copyright to the picture?  And I certainly can't trust that they won't make a new request in six months; quite the contrary, I'd *guarantee* that they make these requests regularly.

{% pull ...never bothered to push back against the accusations that the GPL "infects" software... %}

That's not the only trust issue, either.  If this really is as widespread a scam as it appears, then the inevitable result is going to be to undermine faith in Creative Commons and Free Culture.  I hope that Creative Commons and similar organizations are working to stabilize and maintain that trust, rather than leaving it to creators to assure everybody that we're not going to turn short stories, photographs, and blog posts into extortion rackets.

For an example of handling this badly, the [Free Software Foundation]({% post_url 2021-05-09-fsf %}), among *many* other bad decisions over the years, never bothered to push back against the accusations that the GPL "infects" software---secretly planning to spread to other products, like a virus or cancer, depending on the speaker---not even to spin that as a *good* thing, creating a community.  As a result, they've watched their licenses get eclipsed by "open source" licenses that have no teeth and put all the sharing burdens on the generous people.  You can find *individuals* defending the license, but the FSF has far more important things to do with their time, apparently.

## Anyway...

As you might guess, I didn't update the link.  However, I also didn't want to be associated with their pseudo-botnet, so I replaced the header image with a Vietnamese lion-head statue.  The lion iconography isn't *quite* as striking as its dragon counterpart, but I'll live.  After making that decision, I replied to the e-mail explaining my decision, to head off wasting my time with "second notice" e-mails.

For anybody encountering this scam and looking for a response template, I laid out most of the argument that we've already been through.  This is what I landed on, which obviously repeats or summarizes some comments above.

 > My apologies, ⬛⬛⬛⬛⬛, but the Creative Commons Attribution license does not require a link to the copyright holder.  I always do so out of courtesy, however, even when works are in the public domain.  The link to the work itself is required, but obviously cannot be to a page that doesn't contain the work, or else attribution becomes a useless exercise.  In fact, the license states that the licensor has some choice over the link "unless such URI does not refer to the copyright notice or licensing information for the Work," and a blanket license statement for some works that doesn't even specify the terms of the license is clearly not appropriate, here.
 >
 > In addition, the creator citation was accurate *when I published the post*, and has since been changed, itself changed at least once prior since the original upload to ⬛⬛⬛⬛⬛, when it pointed to ⬛⬛⬛⬛⬛.⬛⬛⬛.  The license terms (including the required attribution) are granted permanently at the time that the license was *accepted*, not retroactively updated at the whim of the issuer.  The text of the license explains that the grant was "perpetual (for the duration of the applicable copyright)."
 >
 > That all said, I prefer not to be a "bad citizen" (and I assume that you wouldn't want to be, either) so I'll replace the image this evening with a photograph released by someone more interested in sharing their work than trying to strong-arm people to drive SEO.  Thank you so much for bringing the issue to my attention.  I always appreciate the feedback, not to mention the insight into how people think about Creative Commons licenses.

The part that I'm hesitant about is the reference to driving SEO.  It's almost certainly accurate, and I drop it in there so that they have a chance to push back on whatever dolt recommended these tactics to them.  However, it's still unnecessarily confrontational---in the sense that it probably invites a boring response about {% sfx sniff %} small business owners struggling to get by---even after removing the parts suggesting bad citizenship and/or dishonesty.

That assumes, of course, that there's a real person on the other side of that e-mail account.  It could easily be automated.

Anyway, if anybody comes after you in this way, I would suggest reporting them to whoever hosts the image, for lying about the license.  I don't know how seriously that Flickr is going to take a single report, but if they get dozens of complaints explaining that the user is claiming to release their work under one license but trying to enforce other terms, that's more likely to get their attention, at least convincing them to prevent those users from showing up in search results.

Probably the most important thing to realize, here, is that the people doing this have probably not actually read the entire license.  Some sleazy consultant probably bullied them into setting this up, and they think that they're doing a public service while struggling on a marketplace like Fiverr by selling cheap "organic SEO links."  If they ever ask for money, though, all bets are off...

* * *

**Credits**:  The header image is [Bristlebot version II](https://www.flickr.com/photos/21649179@N00/2166476315) by [fdecomite](https://www.flickr.com/photos/21649179@N00/2166476315), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.
