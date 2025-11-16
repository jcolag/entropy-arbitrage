---
layout: post
title: Free Culture, Structure and Mechanisms
date: 2025-11-16 07:34:12-0500
categories:
tags: [education, free-culture, history]
summary: Part four of a fairly deep dive into Free Culture as a concept.
thumbnail: /blog/assets/117878252_3c00463c07_o.png
description: Finally explaining Free Culture from the ground up, this time how it works mechanically
update: [
  2025-09-21-define-free-culture-1.md,
  2025-10-05-free-culture-philosophy.md,
  2025-10-26-define-free-culture-history.md
]
spell: Nethack un-licenses Copyheart WTFPL Unlicense vp Fer RVpFtV gevRYv hXjXTw Rustad Tölva
proofed: true
---

* Ignore for ToC
{:toc}

As I mentioned increasingly far back, somebody reached out to me asking a question that took me off guard.

![A logo representing Free Culture, featuring a sketch of three definitely generic modular brick toys stacked as a corner](/blog/assets/117878252_3c00463c07_o.png "I considered an alternate logo for this post, but I still don't hate this so much...")

To wit.

> What's Free Culture?

And sure enough, looking back on almost six years of this blog, it looks like I somehow never touched on that.  This embarrassed me quite a bit, since I often try not to sink into jargon.  I *have* talked about [the movement and its failings]({% post_url 2024-06-02-free-culture-movement %}) and [why I care so much]({% post_url 2023-06-25-free-culture %}) about the idea, not to mention spending every Saturday morning trying to strong-arm you into checking out some project via the [Free Culture Book Club](/blog/tag/book-club), yes.  But it doesn't look like I've ever defined the idea or how I see it.

## Recap

I kicked off that process of defining the idea about a month ago with something of an [elevator pitch for Free Culture]({% post_url 2025-09-21-define-free-culture-1 %}), defining the idea in terms of a slight variation on the four freedoms generally associated with the Free Software movement.

- The freedom to experience the work as you wish, without restriction
- The freedom to study the work, and to create derivative works that say what you want
- The freedom to redistribute copies so you can help others
- The freedom to distribute copies of your modified versions to others without restriction

I also talked a bit about why this might matter to us, especially in an age of constant media consolidation.  After that, I tried to use historical quotes about art and cooperation to outline a modern [philosophy of Free Culture]({% post_url 2025-10-05-free-culture-philosophy %}) not reliant on opposition to copyright or other individualistic, libertarian positions that uphold tropes like abusive lone geniuses.  I summarized the results with this minimal statement.

> Humans need to create and share, creating culture; Free Culture sees this as an inalienable right.

This oversimplifies away the idea that we make art to connect with others---our inspirations, our peers/audience, and those who we ultimately inspire---because everybody has something to contribute to the culture, but for less than a hundred characters, it probably passes muster.

Last time, I tried to outline the [history of Culture Freedom]({% post_url 2025-10-26-define-free-culture-history %}) from what we now call fan-fiction, to fights over copyright, to the movements that set up the mechanisms by which we can ensure that at least *our* parts of the culture remain free.

This time through, I want to talk a bit about those mechanisms.

## Another Angle on Free Culture

Before, I described Free Culture as the collection of works that---affirmatively or passively---grant you the four freedoms to enjoy, modify, copy, and distribute them.  And that idea mostly works, if we ignore our connections with others.  I also, less directly, suggested that we could also see Free Culture as the collection of philosophical ideas that drive us to create and collaborating, creating works that fit into that category.  That seems closer, but could also describe any number of other things.  But we could also see Free Culture as the processes and mechanisms that enable and safeguard those freedoms.

In fact, you'll notice that the four freedoms have an element of enforcement built into them, in the ways that certain freedoms only make sense if we have established some other requirement.  Let's take at that in practice.

### The Four Freedoms, Revisited

The freedom to experience the work as you wish without restriction, in effect, requires (among other things) that creators and distributors not use digital rights management, and on the contrary, provide enough "source material" that a given consumer could alter the work for use in another context.  If somebody needs your help to read your blog post in Braille, to watch your film on a custom [mechanical television](https://en.wikipedia.org/wiki/Mechanical_television), hang a copy of your painting in their basement, or listen to your music on a hacked tractor, then they don't really have the freedom to do so.  You don't need to do the work for everybody who has different needs, but you can't put in any artificial impediments to prevent them from doing what they need to do, and should provide any "source forms" that people might need to make[^6IpmEE] a version that works for them.

[^6IpmEE]:  Or engage someone with the skills to do the work for them, if they can't or don't find it valuable to do the work for themselves.

The freedom to study the work, and to create derivative works that say what you want, similarly requires upholding that first freedom[^fSoPq4] and its requirements, because if a person can't access it and modify the form, then they can't modify the content, either.  And it also requires a commitment to not trying to control the message, since everybody needs to have the ability to change the message.

[^fSoPq4]:  Yes, the Free Software people number them zero-to-three, because we generally make computers start counting at zero.  And how many people has that little inside joke recruited to the cause, recently...?

The freedom to redistribute copies, likewise, requires freely granting others the right to make and pass along copies, even though copyright gives you the broad latitude in enforcing control over who can make and distribute those copies.  Arguably, it also requires the first two freedoms, because if you can't experience the work on your terms, or if you can't study the work, then you can't copy in any more than the most superficial sense.

And the freedom to distribute copies of your modified versions to others, requires upholding the second and third freedoms.  If you don't have permission to modify things, or if you don't have permission to distribute them, then you can't distribute your modified versions.

The fourth freedom requires the second and third.  The third freedom requires the first and second.  The second freedom requires the first.  And the first freedom has some natural requirements.

## Licenses

That gives us some sense of what we want and need, but how do we make it work?

Don't worry, because I won't actually try, but I think that we could potentially make the argument that *public licenses* will end up ranking as one of the most important recent innovations.

Taking a step back, though, legally speaking, licenses provide official permission to do something, under certain conditions, almost identical to a contract[^626CYl], where one party (the licensor) agrees not to sue the other (the licensee) for exercising the granted permission, provided that the licensee doesn't violate the terms under which they received that permission.  We all probably have some familiarity with a driver's license, for example, which grants conditional permission to operate a motor vehicle on public roads within a certain jurisdiction.  Some careers have licensing around them, where you may not practice that occupation without some organization granting your conditional permission.  Copyright licenses work through similar processes, where a licensee receives permission from the creator of some work protected by copyright to use that work in some agreed-upon ways.

[^626CYl]:  I gather that Vizio even acknowledged that the GPL operates like a contract does in [*Software Freedom Conservancy v. Vizio Inc.*](https://sfconservancy.org/copyleft-compliance/vizio.html) this past week, so this view comes fairly close to the mainstream.

In a subset of copyright cases---music in particular, in the United States---we have developed a regime of [compulsory licenses](https://en.wikipedia.org/wiki/Compulsory_license), where to facilitate the spontaneity of (non-dramatic) live performances, organizations and/or governments have already negotiated the license, so that you never need to *ask* for permission within a certain range of uses, but you do need to pay the standard fee whenever you take advantage of that permission, in a sense applying "easier to ask for forgiveness than permission" to actual law.  Patents also fall under this category, on occasion, where the government or industry deems a key technology so important that having every interested party negotiate their own permission would bog the entire system down.

Public licenses, starting (as far as I know) with what became the [GNU General Public License](https://en.wikipedia.org/wiki/GNU_General_Public_License)[^uW3Cpk], took this idea a step further, and wrote a formal license granting the four freedoms *in advance*, to anybody willing to adhere to the requirements.  In the case of the GPL, you must take steps to safeguard the same freedoms to your consumers, by using the same (or later) license, and in exchange, you can do pretty much whatever you want with the software.

[^uW3Cpk]:  The GPL technically had a variety of immediate predecessors from the GNU project and its predecessors that named each license after the software it governed.  You'll occasionally stumble across software that still carries its bespoke license, often named the GNU Whatever Public License, and it has all the early GPL verbiage.  [Nethack](https://nethack.org/common/license.html) probably makes for the most visible example, itself copied from another license from the year prior to the release of the GNU GPL, also attributed to Stallman, and definitely moving in the direction of the license that we know today with most of the same terms, though far less specific, and so almost certainly with more loopholes.

You can probably see why I find this such an important innovation.  Rather than waste time vetting every request and throwing up artificial hurdles to jump through in order to acquire permission, you deal with violations mostly by demanding restitution for a breach.  However, like I said, I don't want to write this to sell you on the idea.

Rather, I want to point out that these public licenses, at least the good ones, become the mechanism for maintaining the four freedoms.  A Free Culture license directly grants you the "negative liberties" on the lists, things that you can do without any restrictions.  In exchange for those grants, you provide consideration---legally speaking, valid contracts have the parties trade consideration, objects or services of value---that you enforce those same freedoms for others, constructing positive liberties (empowering people to do more) from the negative.

## The Good Licenses

You'll notice that I implicitly divided the public licenses into "good" and presumably "bad" categories.  One set enables "Culture Freedom," while the other emulates it.  And what do I mean by that?  One more time, recall the four freedoms as I paraphrased them at the top.

- experience the work as you wish, without restriction
- study the work, and to create derivative works that say what you want
- redistribute copies so you can help others
- distribute copies of your modified versions to others without restriction

Many licenses withhold one of the four, usually the fourth.  Non-commercial licenses say that you can modify and distribute the work, for example, *but* not for a commercial purpose.  What qualifies as a commercial purpose?  [We don't really know](https://freedomdefined.org/Licenses/NC), because some paid activities don't actually need your permission, and many activities can straddle almost any dividing line that you can imagine, especially with some proper structuring.  Likewise, the assortment of "ethical" licenses[^o7KkIY] tell you that you can modify and distribute the work, but only if you don't engage in work that the owner disapproves of, whether politically, financially, or otherwise...and I suppose that non-commercial licenses fit into this broader set.

[^o7KkIY]:  In addition to the other problems, most, if not all licenses in this class strike me as [hypocritical]({% post_url 2022-07-18-mandela %}#a-long-detour-into-license-land), often by either classifying harm as something that *other* people do while quietly sweeping their own complicity under the carpet, or by not really understanding their own requirements in full.

Other licenses forbid modifications ("no-derivatives"), which withholds the second freedom and sometimes the first[^4efitM].  And if you don't have the first, as mentioned, you don't really have the others, either.

[^4efitM]:  Several journalistic organizations take anti-modification licenses to mean that they can forcibly track readers, for example, while still claiming a commitment to "freedom."

In the old Question Copyright material, they parodied these licensing trends with the mock-introduction of the [Attribution No-Value license](https://jcolag.codeberg.page/qco/367-cc-nv.html), which "allows covered works to be distributed freely with proper attribution, as long as no recipient derives any value whatsoever from them, including but not limited to personal pleasure, commercial gain, or artistic benefit."  When I talk about a bad license, I mean one that tries to push us in that direction.

And then we have the class of informal licenses, which grant you *some* permission, but don't seem to find it worth explaining that permission or your requirements.  Such [pseudo-licenses]({% post_url 2024-08-11-open-source-characters %}) often run less than fifty words, making them convenient to actually read, but often choose to spend those words on "vibes," rather than trying to prevent future legal conflicts[^oO1QAe].

[^oO1QAe]:  I have probably mentioned this over the years, but despite the bad reputation that "legalese" has, contracts and licenses spend so much verbiage on trying to define the relationships specifically to forestall any disputes between the parties.  For long-term projects and the longest contracts, almost every clause comes from somebody finding and exploiting a loophole that led to hurt feelings.  English doesn't avoid ambiguity well, as evidenced by how every project to write software in English inevitably flops.

Oh, and we also increasingly have [source-available](https://en.wikipedia.org/wiki/Source-available_software) public licenses, some version of saying that you can use the product for some uses, but not any use that the corporate overlord might find threatening.

Do I want to tell you not to use those "No-Value" licenses, if you like them?  No.  Honestly, feel free to fill in your own, if that resonates best with you.  However, such works don't rightly qualify as Free Culture, because they don't grant the four freedoms.  We don't really have the same project.

And I also don't think that your choice of license does what you think it does, but I have talked about that since a [post about copyleft licensing]({% post_url 2020-03-29-copyleft %}) that I made early in the blog's life.

### Does It Matter

I do think that the difference between license types matters with a clear best choice.

For example, the "un-licenses," if you'll pardon the term, forget the point that licenses *let* you do things, granting you permissions.  These sorts of licenses---the [Copyheart](https://copyheart.org/)s, the [WTFPL](https://www.wtfpl.net/)s, the [Jenny Everywhere]({% post_url 2024-08-11-open-source-characters %}) nonsense, the assorted [pledges](https://osseeds.org/), the [Unlicense](https://unlicense.org/) itself, and more---claim that they want to give you permission, but they never really tell you what you have permission to do or under what specific conditions.  They also don't give you any sense of how to protect yourself if the copyright owner's estate chooses to sue you, which they can probably do since nobody ever actually granted you any enumerated permissions.  And for all the talk about freedom, they don't have a way of safeguarding any such freedoms after the initial grant.

Among the "self-selective" licenses---the non-commercial licenses as discussed, the [Hippocratic license](https://firstdonoharm.dev/), the [Anti-Capitalist license](https://anticapitalist.software/), the often-sought [anti-AI licenses]({% post_url 2024-03-03-ai-licenses %}), the [Anti-Fascist license](https://github.com/jamiebuilds/anti-fascist-mit-license/tree/master), the [JSON License](https://www.json.org/license.html), and many more---all permit use to "everybody," except for some obnoxious group of people.  But as mentioned, they choose vague categories guaranteeing that different people will have different interpretations of where to draw boundaries, making it difficult to adjudicate any disputes that might legitimately arise, often seemingly deliberately to exert and maintain control over the community[^H8f4Tb].  Even cases where they seem to provide a clear definition, the actual definition doesn't seem to match their claims.

[^H8f4Tb]:  And if you want control over the community, then why use a public license at all?

Perhaps because organizations that endorse one often endorse the other, I associate the self-selective licenses closely with the "toy" un-licenses, those that mimic granting rights, but instead dishonestly solicit volunteer labor.  For example, the no-derivatives licenses claim to offer freedom, but they only really free fans to advertise and distribute the work on behalf of the artist; those same fans shouldn't think of themselves as a part of the creative process.  Similarly, the "source-available" licenses want to bring in a community of volunteer developers while openly sabotaging prospective competitors, something that a company could *probably* sue them over as an overt [anti-competitive practice](https://en.wikipedia.org/wiki/Anti-competitive_practices), where you have functioning trade governance, even though they would probably claim to do it to prevent somebody else's hypothetical anti-competitive behavior.

I understand and even sometimes sympathize with the motivations of these sorts of licenses.  Un-licenses exist at least partly as a result of the constant propaganda suggesting that contracts, lawyers, and courts exist to waste time and drain money[^vp_Fer], misunderstanding that the complexity of "legalese" comes from the need to "game out" all possible misinterpretations and resolve them in advance.  The self-selective licenses come from a reasonable desire to not help terrible people.  And the toy licenses come partly from an opposition to copyright---when people created many of these licenses, authorities cracked down on piracy, so distribution felt important---and partly from seeing art as a product created by a genius whose work we mere mortals shouldn't interfere with.  But even though I can sympathize with a lot of that (other than the genius thing), I also find the solutions misguided.

[^vp_Fer]:  The political right has often loved this idea, discrediting the courts and pushing for a world where we resolve problems with "personal honor," historically meaning duels and similar endurance trial stunts, where we pretend that the willingness to risk death correlates to moral authority and that might literally makes right.

We don't solve the problem of license complexity by chopping them down into insignificance; we solve the problem by educating people about how licenses work, in the same way that Free Culture wants everybody to join up and create together.  We don't solve the problem of terrible people intruding into our communities by trying to find clever ways to not issue them a public license; we solve it through stronger copyleft (pro-labor) requirements, forcing adaptations to publicly close their use, so that the originator has the opportunity to name and shame them, and also by actually pushing their toxic ideologies so far out of favor that they find it embarrassing to act in terrible ways[^RVpFtV]...but also by showing them a better way than using their own exclusionary tactics, when possible to do safely[^gevRYv].  And we don't solve the problem of big studios prosecuting piracy through extremely narrow licenses; we solve it through not supporting the major studios and publishers who want to corner the culture market with their slop (industrially extruded culture-like media products) instead of building communities.

[^RVpFtV]:  "Oh, no, we might drive the behavior underground where it can metastasize."  Right, and remind me, how has it gone, letting them spew their hatred without "feeding the trolls," so that people can hear how foolish it sounds...?

[^gevRYv]:  I'll say something contentious, here, that our problems derive from a concentration of power, not some random creep who wishes that governments would enforce their specific hatreds.  Billionaires mediating energy, commerce, public discourse, health, safety, media, identity, and more make things worse and more fractious, because that enriches them at our expense.  I don't want to suggest "you should still totally support [big tents]({% post_url 2025-10-19-big-tents %}), *because* they pretend to not notice the politics that you disagree with," because I don't believe that.  But I do believe that every individual pro-authoritarian, anti-diversity weirdo who you can peel off from avidly following some billionaire-run company like a needy puppy primes them for fighting the system instead of you, weakening them and their insistence on pitting us against each other.  Excluding them from Free Culture---even if you need to ban them from communities to keep others safe---reinforces their persecution complexes, reinforces their interest in corporate-produced slop, and deprives them of the space and example needed to become better.

In other words, we don't insist on universally granting the freedom to "experience/use the work as you wish, without restriction," because we managed to misunderstand the [paradox of tolerance](https://en.wikipedia.org/wiki/Paradox_of_tolerance) as a cheat-code for smuggling bad behavior into communities, or because we secretly wish that the worst people in the world would use our work[^4noo5A].  We grant those freedoms universally, because it *stops serving as a public license* if you might need to investigate every use of your work, because clever people can always find bureaucratic tricks to appear to comply with the license through proxies, and because the idea doesn't fit with other licenses[^4wz-QS].  That, and a better world needs to figure out how to deal with terrible people, beyond politely asking them to disengage.

[^4noo5A]:  I do, however, believe that the minimalist licenses---the aforementioned WTFPL, the [BSD](https://opensource.org/license/bsd-2-clause) license, the [MIT](https://opensource.org/license/mit) license, and other "almost public domain" licenses---directly encourage that sort of exploitation, by insisting that we need to make freedom as useful as possible to large corporations.

[^4wz-QS]:  Yes, maybe you don't care about---or maybe you *look forward* to---people unable to mix your work with the wider collection of works released under the terms of licenses that you probably dismiss as "amoral."  Further, maybe you believe that you have compellingly marked out territory, whether with your amazing project or your moral stand, and therefore everyone will quickly flock to your banner instead of fragmenting a tiny community even more.  History would tend to suggest, though, that you'll get mutually unintelligible fragments instead of a better community.

And on that note, I'll point to my post on a [different way of looking at copyright]({% post_url 2025-05-18-copyright-thoughts %}), where I pitched the idea that---maybe---copyright has value in that it forces us to take responsibility for how people use our works.  And I think that applies here.  Free Culture doesn't try to cede copyright, so creators still maintain some responsibility for how people use their art.  But it also needs to rely on creators positioning their work in a context that makes it unappealing for terrible uses, and using their voice to speak out when people do so.  That, at least to me, seems far more sensible than the equivalent of hanging a "no shirt, no shoes, no service" sign[^hXjXTw] in your store.

[^hXjXTw]:  For those not aware, those signs started as an attempt to target Hippies without naming them.  But it also creates a lot of collateral damage and arguments over boundary conditions.

The good licenses, then, form the framework for a community and accept responsibility for the consequences.  The bad licenses continue to center the creators as unique geniuses who know better than their communities how to use their works.

### Not So Fast

You might notice that I haven't given you a list of "good licenses," only a way to evaluate them.  I made that choice intentionally, because all the public licenses need work.

At least in my opinion, no current public license yet has a sufficiently strong copyleft clause, one that requires that adaptations contribute directly back to the project.  As I mentioned, this would allow projects to denounce abuses.  But instead, they all allow people to ignore the "upstream" project, and licenses such as the GPL even allow people to hide their work by only supplying it to "customers."  Likewise, the Creative Commons instance of this idea refuses to require releasing whatever passes for "source"---justified by the idea that art doesn't necessarily have a form more conducive to manipulation[^NY8RHX]---which feels like it doesn't actually enforce that first freedom of allowing people to experience the work how they please...

[^NY8RHX]:  This feels like a load of garbage, by the way, because I could write all my *software* directly as instructions for a target microprocessor, if I wanted, which would equally mean that software doesn't necessarily have a convenient-to-edit "source" form, but that possibility doesn't put the GPL and similar licenses off requiring source.  Therefore, it doesn't seem remotely problematic to say that, if you use my work for something, then you must release the form(s) of it that you used to build whatever you made.

As a bonus, strong copyleft would also scare companies away, preventing them from harvesting free labor.

### Enforcement

Now that we've talked about licenses, we need to talk about enforcing those licenses.  What happens when somebody chooses to take you up on your offer to share, *but* refuses to abide by the requirements?

Actually, we already know the answer to that one.  They have violated the terms of the license, which voids the agreement, which means that they have infringed on your copyright.  You then deal with that however you need to.  As mentioned in prior posts, copyright holders can opt to completely ignore infringement, wait until later, or aggressively pursue it.

I see this, by the way, as another flaw in what I called the "bad" licenses.  In almost all those cases---I suppose except for the source-available and similar licenses---the ambiguities make it difficult to actually sue somebody for violating the license.  The project didn't *really* engage in commercial activity, they might argue, because they charged for distribution, not the product.  Or they donated the profits to charity, or would if it actually ever turns a profit, but you know [how rough the media landscape](https://en.wikipedia.org/wiki/Hollywood_accounting) can get.  They didn't violate your anti-fascist clause, because fascists suppress dissent, but *they* embrace their watered-down token opposition party, or because fascism specifically means a movement in Europe during World War II to them.

Terrible people love to find these sorts of semantic dodges, and if you need to fight it out in court, then you want to make sure that the courts can't see those semantic gimmicks as reasonable interpretations, rather than choosing a license for its catharsis.

## Coming Soon

I have probably overlooked some advances in licensing, and surely ignored plenty of specific licenses that might interest us, but this should give a broad sense of how we can and sometimes need to see Culture Freedom as a set of practices legally encoded into public licenses.

And once again, we'll end here, so that this doesn't become some unhinged rambling manifesto.  But when I return to the topic for the fifth post in the series, probably in a couple of weeks, we'll turn from the mechanisms of Free Culture and public licensing to the "other stuff" mechanisms, making Free Culture work beyond the licenses.  I'll (probably) borrow more than a bit from other Free Culture projects.

See you then...

* * *

**Credits**:  I adapted the header image from [FC.o logo](https://www.flickr.com/photos/mllerustad/117878252/in/set-72057594090576065/) by [Karen Rustad Tölva](https://www.flickr.com/photos/mllerustad/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license.  They created the original version for [FreeCulture.org](http://freeculture.org/), but you can see as well as I can that the site no longer exists in any meaningful way, so I have decided to appropriate it...
