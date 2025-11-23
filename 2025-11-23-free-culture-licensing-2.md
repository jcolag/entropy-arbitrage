---
layout: post
title: Free Culture Licensing Addendum
date: 2025-11-23 07:12:12-0500
categories:
tags: [education, free-culture, license]
summary: Part four-and-a-half of a fairly deep dive into Free Culture as a concept
thumbnail: /blog/assets/117878252_3c00463c07_o.png
update: [
  2020-03-29-copyleft.md
  2025-11-16-free-culture-mechanics.md
]
description: Returning to the post on how Free Culture's mechanics to clarify and expand on it.
spell: UMG institutionalist Ártica un-licenses sIFelt zchhwv Sybase Watcom WKZ bR KOhmar WTFPL zRvBfD Rustad Tölva
proofed: true
---

* Ignore for ToC
{:toc}

After I published last week's post on the [mechanics of Free Culture]({% post_url 2025-11-16-free-culture-mechanics %})---which already ran too long or my tastes for these posts---I realized that I somehow had even more to say.  Partly, I probably skipped over some key points.  In other cases, I should have shored up key aspects before moving on.

![A logo representing Free Culture, featuring a sketch of three definitely generic modular brick toys stacked as a corner](/blog/assets/117878252_3c00463c07_o.png "One day, I'll come up with a new image for these sorts of posts")

Strap in for this one.

## Non-Discrimination

I have recently seen several people argue against non-discrimination clauses in licenses (as in the clauses that say that anybody can work with the material), because they don't want offending people using their work.  Many of them seem to cite right-wing extremists installing and running community-oriented services to grow their audiences.

And I bring this up not to shame them---and I don't link to them, because I don't want to direct conflict their way[^t6_2_e]---but to point out that a public license (or not) on source code doesn't actually do anything about that.

[^t6_2_e]:  Also, I have seen *so many* of them over the past couple of weeks that it feels like some concerted effort to fragment one of the few spaces where you can still find actual alternatives to the growth-at-all-costs market concentration.  I mean yes, both iOS and Android have Open Source and Free Software kernels, Mach and FreeBSD for the former, Linux for the latter, so you could argue that Open Source powers that concentrated market.  But you can't tell me that Apple or Android (later purchased by Google) couldn't have developed their own kernel.  Google even has the Fuchsia project waiting for maturity to replace Linux in Android.  And when you exclude Android, you don't see many companies getting some massive benefit from code released under copyleft-oriented licenses.

Let's take an example that happened to catch my eye recently.  They explained that a known-in-some-circles authoritarian used their community's network software (forum, social media website, whatever) to spread their authoritarian message.  And I agree that I wouldn't like that either.  However, consider what changes if you move to a license that somehow manages to accurately exclude such people.

...Nothing.

As far as I can tell, all current public licenses, including the so-called "ethical" licenses, only care about distribution and modification.  If you could selectively deny the right to download code that you put up for public download, then news outlets could change their paywall to after-the-fact, shaking you down for having visited their website, because that downloads/copies the article.  I also can't think of a reliable way to prove the identity of software running on a computer that you don't control, and if we legally hold people innocent until proven guilty, then you won't get too far arguing that they can't use your software, either, because they could plausibly use something only designed to look like your software[^3twylm].

[^3twylm]:  And no, [*Apple v Microsoft*](https://en.wikipedia.org/wiki/Apple_Computer,_Inc._v._Microsoft_Corp.) says that copyright doesn't cover your "look and feel."

### Restrictive Permission

Can't you write the license to give you control over their personal use of the software?  No, because you can't "let"---remember, licenses can only grant permission to the licensor---someone do something by giving yourself new forms of copyright.  If you could, think about what Amazon, Disney, Google, UMG, Scripps, and the rest would demand of you for living your life in their presence.

This applies to many, probably all, non-Free licenses.

I have mentioned (multiple times?) before that your moral stance on a non-commercial license won't stop a [major studio](https://en.wikipedia.org/wiki/Hollywood_accounting), because they know *all about* making it look like money actually comes from and goes somewhere that it doesn't.  The license also doesn't cover anything that would fall under [Fair Use](https://en.wikipedia.org/wiki/Fair_use).  And we don't even have a strong definition of commercial activity.

When you can drive a truck through the various lacunae and loopholes in a license with as long and established a history as everybody's favorite non-commercial license, how do you think it'll go when you use a license written by a non-lawyer that tries to prevent association with (for example) a label that an unfortunate number of people dismiss as "whatever the speaker doesn't like"?

### Collateral Damage

I have mentioned this elsewhere, most prominently in my post about the prospect of [anti-AI licenses]({% post_url 2024-03-03-ai-licenses %}), but every discriminatory clause shares one huge problem:  They cast too broad a net while focusing on the wrong problem.

In the AI-related post, for example, I talked about the distinction between different versions of "use my content to train AI."  None of us likes [Claude {% cc %}](https://cybernews.com/news/anthropic-tiktok-gray-bots-threat/)'s aggressive, indiscriminate scraping, abusive across the Internet, so that they can goose their earnings at everybody else's expense.  Most of us dislike the other major AI companies that might abuse us less, but still have a business model that involves exploiting us all as undifferentiated "content" so that they can sell us slop based on our content.  I get it.  *I* certainly don't like them, and don't see any value in allowing that behavior.

However, let's say that we had a well-behaved middle school student who loves your work, respects the load on your server, and would happily comply with a Free Culture license, but also thinks that a custom LLM trained on well-sourced, well-cited Free Culture material might benefit people.  In that case, your hypothetical anti-AI license would block and intimidate them, while the big companies (legitimately) scream "Fair Use"[^8iKGPW] and do whatever they wanted.

[^8iKGPW]:  Because I recently made the mistake of trying to have a conversation about this with somebody who only knew the words but had no interest in what they meant, I'll quickly mention that, while training an AI almost certainly always falls well within the bounds of Fair Use, using generated output in the context that an ordinary person would use the original work almost certainly does *not* qualify as Fair Use.  The former use ticks three of the four factors that United States courts look at in such defenses, while the latter doesn't tick any of them.

In the same way, your anti-capitalist license means that somebody who could really use an income source can't take a small profit for making their favorite work of yours available to friends, while a major streaming service might reasonably argue that oh, they didn't engage in capitalism by making your work available, because they made it available free to people who already subscribed to their service.  Your license that says to not engage in evil excludes anybody aware of the conflict minerals in every computer on the planet---yes, you and I both benefit from either child labor or slavery, no matter who we buy from---while giving a pass to the majority who don't know better.

Any discriminatory license that you might care to float will produce awful false positives (uses that you probably wouldn't mind using your work) and false negatives[^w5eyDM] (uses that you would object to but pass muster).

[^w5eyDM]:  All classification schemes produce false positives and false negatives, but these rule-based schemes based on vibes and visceral emotion seem entirely designed to maximize the failures.

### Possible Alternatives

As I have said over and again in these posts, I don't want to tell anybody what they should do.  That said, *if* you want my advice, and *if* you want to control who uses your software or how, then I would say that you don't want a public license at all, and---further and more controversial---don't want to distribute your software publicly.

Rather, I think that you want to create a "gated community," where the vetted members have access to your software on your terms.  In other words, you probably want to operate like a business, offering a specific [EULA](https://en.wikipedia.org/wiki/End-user_license_agreement).  You might even want to take modern steps, such as asserting that you still own the software, even when it runs on their system, so that you can revoke their privileges if they step out of line.

I present that as a serious option, by the way, and wouldn't judge anybody for taking their software or media down that route.  If it feels like a mean-spirited satire to you, though, because you would *never* use such corporate-style tactics, then you should interrogate why you think that your honor system (a public license) that doesn't trust people (applying restrictions that you implicitly threaten to enforce) feels more appropriate.

## Movement Skepticism

Note that I don't want to say that the movement to date has gone so well that we shouldn't question it and push it to work the way that we need to.  We should question all movements and institutions, to ensure that they provide what we need.  We can't fix them if we don't question their value.

Seriously, this entire series of posts exists, in part, because I want to help re-envision the movement without the counterproductive libertarian drive screaming about copyright law and teaching us to create and "throw it over the world" without any interest in what happens next.

We don't have solid organizations that advocate well for the movement, certainly.  I wrote an entire post on the [Free Culture movement's poor leadership]({% post_url 2024-06-02-free-culture-movement %}) and [where the Free Software Foundation has consistently gone wrong]({% post_url 2021-05-09-fsf %}), so I don't exactly have an institutionalist streak, here.

These days, the best of Free Culture thinking seems to come out of [Ártica](https://www.articaonline.com/presentacion/) down in Uruguay, but writing in Spanish presumably limits its spread---because Internet infrastructure comes out of Silicon Valley's ethnocentric traditions, not because "only" half a billion native speakers doesn't carry enough weight---so I don't find people talking about their material.  And because I don't read Spanish well, with (full disclosure) whatever 1970s **Sesame Street** taught me as a child plus a one-semester class in junior high school opposite a French class, even I don't read much of it.

### Institutional Authority

That said, I suspect that this space doesn't actually lend itself to centralized leadership.  We certainly benefit from the output of organizations such as Creative Commons, The Electronic Frontier Foundation, the Free Software Foundation, the Software Freedom Conservancy, and so forth.  Without licenses written and vetted by intellectual property lawyers and without people with deep pockets willing to go to court to enforce our cultural rights, we'd probably all find ourselves using incompatible "un-licenses" that---as I talked about last time---sound compelling but don't actually do any coherent licensing work, and so getting us into unresolved arguments every time that somebody acts in a way that hurts our feelings.  But the utility of the organizations doesn't mean that we couldn't replace them or that we should see them as *leading* our community.

As I've pointed out in the past, Creative Commons---to single somebody out, though I could make a similar case for all the organizations in the space---still can't bring themselves to tell you what "non-commercial" means or to admit that the non-commercial and no-derivatives licenses don't fit with the rest of the group, but they had plenty of times to offend everybody by proposing [AI Signals]({% post_url 2025-06-29-signal-change %}), and now have seemingly regressed to whining about the public domain with their [Open Heritage Statement](https://openheritagestatement.org/statement) while seemingly demanding the right to misappropriate the art of other cultures.  And yes, in the latter case, readier access to public domain materials would benefit us, but declaring the need doesn't actually get anything digitized and archived.  As such, how does any of that look like leadership?  Or rather, if we saw that as leadership, what would that get us as a movement?

I'll probably return to this later in the series, but the movement needs to come from *us*, with those organizations as peers, not leaders.  If I say something inexcusably wrong about Free Culture, nobody should or would twist themselves into knots trying to justify it as the presumptive direction for the movement to go.  Likewise, it makes no sense to imagine that AI Signals represents the future of the movement.  And I think that I---to bring this back to where we started---find this idea that people need to abandon Free Culture and Free Software so wrong-headed, because it seems to come from the idea that the organizations have institutional authority, or that because some subset of individuals at all these organizations, probably most prominently the [Open Source Institute](https://opensource.org/), believe in a pro-corporate libertarian approach to the world, then the movement must do that.

Granted, I can't really fault a superficial reading of history from leading to that conclusion.  The "Open Source" term exists specifically to weaken the protections of Free Software to make it corporate-friendly, and you'll find many Open Source developers *proud* that some billion- or trillion-dollar company or other uses their code.  And gosh, you say that [such developers burn out {% cc %}](https://opensourcepledge.com/blog/burnout-in-open-source-a-structural-problem-we-can-fix-together/) doing free labor for companies that could afford to hire that person to lead a team?  You say that these enormous companies [take advantage of the volunteer labor without giving back {% cc %}](https://thenewstack.io/ffmpeg-to-google-fund-us-or-stop-sending-bugs/)?  What a shock... {% emoji eyeroll %}

## Revisiting "Good" Licenses

Let's go back to the idea of "good licenses."  I said in that prior post that they don't really exist, yet, though somewhere between CC BY-SA and some version of the GPL currently comes the closest.  Therefore, I want to dig into what this should probably look like.  Note that I tried to do this once before, early in the life of the blog, as my [license wish list]({% post_url 2020-03-29-copyleft %}), but I mostly wrote that off the cuff, and didn't have nearly the experience that I do five years later.  For example, the first two items on my original list show a need for more information (I now see licenses as inherently contractual, and believe that the law sees them the same way) and biased towards authority (I no longer care that Creative Commons says that you shouldn't use their licenses for code or that the FSF says not to use the GPL for art).

Today, revisiting that topic, I would say that a good license (probably) needs (at least) all the following features.  For each of these, I'll talk about why they probably matter, at the end of the section.

### Strong, Specific Attribution

The [GPL](https://www.gnu.org/licenses/gpl-3.0.html), probably for historical reasons, but seeming silly in retrospect, doesn't care about attribution.  Or rather, it cares about attribution in almost the wrong way, insisting that you distance derivative works from their sources so that nobody blames the original creator for your mistakes[^sIFelt], as specified (awkwardly) in the preamble.  However, an author does have the right to add an attribution clause of their own, binding people §7(b) who adapt it later.

[^sIFelt]:  Notice, by the way, the similarity to the "I don't want fascists to use my software," in this.  If somebody (inexplicably) uses [my old BASIC interpreter](https://codeberg.org/jcolag/basic-interpreter) in a weapon, then they can't blame it on me...

Meanwhile, Creative Commons [CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0/legalcode.en) (but really all of their licenses) §1 says this.

> - If You Share the Licensed Material (including in modified form), You must:
>   - retain the following if it is supplied by the Licensor with the Licensed Material:
>     - identification of the creator(s) of the Licensed Material and any others designated to receive attribution, in any reasonable manner requested by the Licensor (including by pseudonym if designated);
>     - a copyright notice;
>     - a notice that refers to this Public License;
>     - a notice that refers to the disclaimer of warranties;
>     - a URI or hyperlink to the Licensed Material to the extent reasonably practicable;
>   - indicate if You modified the Licensed Material and retain an indication of any previous modifications; and
>   - indicate the Licensed Material is licensed under this Public License, and include the text of, or the URI or hyperlink to, this Public License.
> - You may satisfy the conditions in Section [3(a)(1)](https://creativecommons.org/licenses/by-sa/4.0/legalcode.en#s3a1) in any reasonable manner based on the medium, means, and context in which You Share the Licensed Material. For example, it may be reasonable to satisfy the conditions by providing a URI or hyperlink to a resource that includes the required information.
> - If requested by the Licensor, You must remove any of the information required by Section [3(a)(1)(A)](https://creativecommons.org/licenses/by-sa/4.0/legalcode.en#s3a1A) to the extent reasonably practicable.

Pardon my using bullets instead of numbers, but Jekyll did a miserable job of converting the original.

In any case, notice the mess, here.  You must attribute however the author wants, as long as they make a "reasonable" request, whatever that means.  And then you "only" need four notices and some hyperlinks, but use your own judgment in presenting it in a "reasonable" way.  Oh, and the original author can force you to remove parts of it, but only if you can conveniently do it.

Sorry, but *what*?

One license shrugs its shoulders completely, and the other wants a treatise, but also a negotiation, but also don't put yourself out.  At least it gets the pseudonym part right, I guess.

Instead, a good license should specify how to attribute, exactly how to phrase and present it, both online where space doesn't really matter, and in physical forms where you can't click to a credits page with disclaimers.  And it should make that attribution *mandatory*, unless the original work specifically requests not crediting the creator.

Why would attribution matter so much?  Strong attribution requirements serve as the first (but not only) defense against corporate encroachment.  We know this, because a CC BY license almost [derailed **Iron Man** {% cc %}](https://adactio.com/journal/1530/), on the basis that "getting your name in the credits usually costs at least $1,500" in Hollywood[^zchhwv].

[^zchhwv]:  I don't know the specific rule, there, but I suspect that we can thank the relevant unions for it, a reminder (or a sign, if you hadn't thought of this before) that Free Culture as a mechanism works best as part of the labor movement.

### Strong Reciprocation

As I have mentioned before, even licenses that we consider to get the *positive liberty* of reciprocation or copyleft right---the part that ensures that people can build on derivative works---don't really do a great job.  Again, consider the GPL v3; the AGPL has the same text, to my surprise, that when you provide a "non-source form," such as an executable program, you can get away with fulfilling §6(b).

> Convey the object code in, or embodied in, a physical product (including a physical distribution medium), accompanied by a written offer, valid for at least three years and valid for as long as you offer spare parts or customer support for that product model, to give anyone who possesses the object code either (1) a copy of the Corresponding Source for all the software in the product that is covered by this License, on a durable physical medium customarily used for software interchange, for a price no more than your reasonable cost of physically performing this conveying of source, or (2) access to copy the Corresponding Source from a network server at no charge.

In other words, the GPL allows you to "don't ask, don't tell" the source code, and allows you to set a three-year expiration on the copyleft clause.

And over at CC BY-SA?  Shockingly, they do better in §3(b)1, but still not really good enough.

> The Adapter’s License You apply must be a Creative Commons license with the same License Elements, this version or later, or a BY-SA Compatible License.

I hope that you see the problems, here.  These clauses should, at a bare minimum, do the following.

- Like the Creative Commons version says, immediately apply to all derivatives.
- Like the GPL version...hints at, I guess, apply to the "Corresponding Source," as well as the finished product.
- And unlike both, it should require at least some attempt at permanence *and* a good-faith attempt to contribute back <dfn><abbr title="jargon for the original project that the derivative adapts">upstream</abbr></dfn>.

The last seems critical, and I have probably talked about this in various spaces for over thirty years in one way or another.  If, to explain through example, you adapt this post---fix some typo, translate it, dramatize it, insert mocking commentary, or whatever---then more than anything else, I really want to know about it and have a chance to integrate your changes with my version, if (in my opinion) they improve what I have done.  The positive liberty in reciprocation should make it convenient to improve all versions of a work, rather than making it a scavenger hunt with (usually) nobody else playing.

And if I don't approve of the use, such an offer would also give me the opportunity to make that distinction clear to my audience.  That might seem abstract in the sense of somebody adapting this blog post, but consider somebody adapting your software for military use, giving you the chance to shame that action.  If they don't need to inform you, then they can work in secrecy.

Why does reciprocation matter, beyond the little examples?  At least to me, copyleft or "share alike" requirements sit at the core of Free Culture, because they ensure that the work stays free even as people modify and adapt it, the aforementioned positive liberty.  Without reciprocation, Free Culture can only ever encourage exploitation, like the developers excited that Big Software chose to use *their library* for the corporate website without compensating them.

And like attribution and Hollywood, while---as I have mentioned many times---companies can use all sorts of accounting, distribution, and Fair Use tricks to "prove" that they haven't engaged in commercial activity with your work, fascists can use semantic gimmicks to "prove" that they don't actually qualify as fascists, and so forth, but *nobody* can legitimately cheat reciprocation requirements.  If you have modified the project for your own purposes, then you either have made your changes public or you have not, with no way of dodging the question or disguising your lapse.

### Source Requirements

As I sort of mixed in above, good copyleft practice requires releasing what the GPL calls *Corresponding Source*, the (copy-amenable) material that you used to create the product.

Sure, sometimes no Corresponding Source exists.  If you physically put paint to canvas or if you hand-wrote your software as microprocessor operations, then you have nothing more to offer the public or upstream.  I see no trouble, there.

However, usually in the digital world, some source material exists.  If you published a physical book, then you probably have a version from a word processor, or in Markdown, HTML, LaTeX, or even plain text.  You *probably* didn't write everything out longhand and extrude paper out the back of some mysterious box.  If you wrote software, you probably wrote it in a high-level language.  If you created visual, then you probably have a version with layers, maybe used vector art, and so forth.  Film almost always has multiple takes, and separate scenes.  Music often has different tracks and/or "stems" that a technician mixed together.

Believe it or not, we actually have *one* license that almost gets this right:  The [Sybase Open Watcom Public License](https://en.wikipedia.org/wiki/Sybase_Open_Watcom_Public_License), which has this to say in §2.2(c--d).

> You may use, reproduce, display, perform, modify and Deploy Covered Code, provided that in each instance:
> - You must make Source Code of all Your Deployed Modifications publicly available under the terms of this License, including the license grants set forth in Section 3 below, for as long as you Deploy the Covered Code or twelve (12) months from the date of initial Deployment, whichever is longer. You should preferably distribute the Source Code of Your Deployed Modifications electronically (e.g. download from a web site);
> - if You Deploy Covered Code in object code, executable form only, You must include a prominent notice, in the code itself as well as in related documentation, stating that Source Code of the Covered Code is available under the terms of this License with information on how and where to obtain such Source Code;

Granted, §12 (Termination) has some wild nonsense that you can't use their compiler if you sue them or if a court finds a lacuna in the license that makes it harder for them to enforce, which seems bad, you already know that I don't like the idea that their reciprocation clause has an expiration on it, and it doesn't require making changes available specifically to the parent project, so I emphatically do **not** recommend the license.  However, the idea that you need to publish your changes even when you mess around with it privately both feels like the correct path to me and caused the FSF to back away from it as *too extreme*[^WKZ-bR] for them.

[^WKZ-bR]:  I'd call this yet another case of the FSF having a myopic view of things.  Their libertarian streak says that you have no right to infringe on their freedom to do what they like on their own computers, even when this strong reciprocation/source clause preserves freedom for everybody else, allowing everybody to learn from experiments, the thing that they insist that they do best.  It echoes how, early on, they argued against requiring reciprocation for software supplied as a service or in firmware, literally for no reason more philosophical than that Stallman only cared about software running on his personal computer that he might want to edit.

Why would source requirements matter?  It takes less effort to work with source than the final product, or at least provides more options for working with the project, which encourages further adaptation and modification.  If I only give you a hard-copy of this blog post, and you wanted to change something, then you would need to transcribe it[^KOhmar] before you could make any changes.

[^KOhmar]:  It occurs to me that I would probably appreciate the aforementioned Open Heritage Statement if Creative Commons had presented it as comparable to a desire for "corresponding source," so that people could work with it.  Scanning images can feel like back-breaking labor, if you don't have an ergonomic work station, and transcribing print takes a lot of time.  But Creative Commons also doesn't care about corresponding source in their licenses, so we can't expect them to make that connection.

#### Good-Faith Pledge

Speaking of the utility of source, every public license has one *massive* gap in it:  The license conditions don't apply to the creator.

Again, let's use this blog post as our example.  Because I already own the underlying copyright to it, I don't need a license to use it.  Therefore, I can republish the post somewhere under a different license (or no license at all), and I can give private permission for somebody to do the same.  I don't need to provide the Markdown version of the post to make it easier for you to edit, no matter the source requirement.

For software, I don't actually need to provide source code to release software, either.  Releases of images don't need to show the raw content, or any vector elements, or anything else.

No license can enforce this, because the copyright holder grants the license rather than accepts it, but I feel like a good license would build a culture around it that encourages seeing Free Culture as incomplete if the original creator doesn't hold themselves to the same terms in most cases, *especially* in providing the corresponding source.

### Define Compatibility

Recall that, when I brought up improving copyleft terms, I quoted CC BY-SA as requiring that you license derived works under the same "or a BY-SA Compatible License."  What does that mean?  §1(c) explains.

> BY-SA Compatible License means a license listed at [creativecommons.org/compatiblelicenses](https://creativecommons.org//creativecommons.org/compatiblelicenses), approved by Creative Commons as essentially the equivalent of this Public License.

For Creative Commons, compatible means "because we said so."  They *probably* make those decisions based on careful legal reasoning based on the text, but can we guarantee that they will always work that way[^IOWk5c]?

[^IOWk5c]:  In the wake of AI Signals, many people copied the text of their favorite licenses---permissible under the terms of the license---change the title, and claim that they have a compatible license...but they don't, because only Creative Commons gets to make that call, even if the two licenses have identical text.

The FSF inexplicably doesn't bother to mention it in the GPL, but [buried on their website](https://www.gnu.org/licenses/licenses.html#Evaluation), they have a similar philosophy.

> If you come across a license not mentioned in our [license list](https://www.gnu.org/licenses/license-list.html), you can ask us to evaluate whether it is a free license. Please email a copy of the license (and the URL where you found it) to [licensing@fsf.org](mailto:licensing@fsf.org). Our licensing experts in the staff and the board of directors will review it. If the license has some unusual conditions, they may pose difficult philosophical problems, so we can't promise to decide quickly.

Again, I don't doubt that they do this seriously.  But why would we need to trust either organization to make the call correctly, when the organization *could* issue specific guidelines of what constitutes a compatible license?  Make the guidelines restrictive and, as the FSF does, reserve the right to intervene on "unusual conditions," but I would expect any serious organization writing licenses, at this point, to at *least* have the confidence to say that, if two licenses grant equivalent or greater rights under equivalent or broader conditions, then we can call those licenses compatible.

Why do compatibility terms matter?  Back to my comment about institutional authority, the current "because we said so" regime only serves to make the organizations look central.  And if Creative Commons or the Free Software Foundation shuts down, something that will inevitably happen eventually, then nobody has the authority to say that their new license works with another.

### Contributor Rights

My opinions haven't really changed on this since that early "wish list" post, but I think that I can refine the position, now:

A good license should, as a condition of adaptation, explicitly ban assigning copyright to the project.  Done.  Whatever terms sufficed to get the contribution in, they should suffice to get the contribution back out.

Why do contributor rights matter?  A project will only ever ask you to give them copyright over your work for one reason:  They plan to eventually change the license to something non-Free, so that they can benefit from your work without sharing it further.  If every contributor retains their copyright, then the project becomes shared property.

When I talked about wanting a [good-faith pledge](#good-faith-pledge) from creators for various aspects of licensing, multiple contributors force that to happen quickly.  Once I accept somebody's contribution to a project, they literally control the copyright to that part of the project, so I would need their permission to do anything with the project that would violate the license, or I would need to discard their contributions and anything relying on them, which qualify as derivative works.

Therefore, companies (and projects that plan to launch companies) love to insist that they need your copyright before they can accept your help, in the form of the [contributor license agreement](https://en.wikipedia.org/wiki/Contributor_License_Agreement).  Deny that practice through the license, and those companies can no longer cheat the terms of the license.

### Annotation

In the prior "wish list," I think that I erred in calling for "simplicity."  There, I pointed out that the GPL v3 clocks in at over five thousand words, probably too long for most developers to read and understand when making a choice.  By contrast, developers who consider the [MIT License](https://mit-license.org/) probably will read it, because you only need to get through about three percent the length of the GPL, so guess which one people will choose, even though the latter protects less.

And while I think that I had gotten onto the right general track, I overlooked the fact that brevity or smaller words won't solve the problem.  Brevity, as discussed, makes it more difficult to prevent disagreements.  And simpler diction doesn't change the complexity of the ideas.  For example, compare the two prior licenses with the [WTFPL](https://www.wtfpl.net/), which has only nine tiny words, really quick to read and appealing, but tough to understand what rights you actually grant, how to enforce it, and how to protect yourself if somebody accuses you of infringing on the copyright.

Instead, I would now propose that a good license needs an annotated form, the formal license text with clear explanations and analysis inserted inline.

For a loose sense of what I mean, consider the Creative Commons licenses.  Each one comes in two forms.  First, it has the official "legal code," such as the attribution guidelines that I quoted earlier.  Then, it also has the non-binding "Deed" that speaks in plain language, such as this.

> **Attribution** — You must give [appropriate credit](https://creativecommons.org/licenses/by-sa/4.0//#ref-appropriate-credit) , provide a link to the license, and [indicate if changes were made](https://creativecommons.org/licenses/by-sa/4.0//#ref-indicate-changes). You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

Again, I raise this for the broad sense of providing plain explanations, but this really doesn't do the job that I want.  Instead, I mean that, where the formal contract says to "indicate if You modified the Licensed Material and retain an indication of any previous modifications," give us a discussion of that clause, reminding us of the relevant definitions and newly defining anything that you thought didn't need a formal definition.  Show examples of how that might look in practice under different conditions.  Explain how that preserves one or more of the four freedoms.  Describe best practices and where people disagree on best practices.

Why would annotations matter?  True, more words won't make more people sit down to read an entire license that takes itself seriously.  However, that sort of commentary and explanation helps people understand key parts of the licenses.  It demystifies the license, and justifies the verbiage in the face of people whining about legalese.

### Other

Less compelling to talk about again, I still believe that a good license should include clear guidance on how to handle non-copyright forms of intellectual property.  On one hand, the license should grant a license to any patents embodied in the project.  On the other, it should specify what you can do with what trademarks and which you must change before publication.  Along similar lines, a good license should grant the absolute right to break or bypass any [digital rights management](https://en.wikipedia.org/wiki/Digital_rights_management) that any editions of the work or derivatives might have attached.

It would help if licenses had some *path* to making works compatible even if their licenses don't directly match up, though I realize that probably takes too much effort to get right.

And even though I said at the start of this licensing "sidebar" that it probably doesn't matter, it still makes sense to me to make sure to build a license so that it can work for anything, whether art, code, hardware, fonts, games, databases, or whatever else you might have.

## Out of Control Addendum

Yes, my "quick comments" on last week's post turned out longer than the actual post.  Like I said, "even more to say," "probably skipped over some key points," and "should have shored up key aspects."  Had I done all this last week, the post would have come closer to ten thousand words, and who'd read that...?

I hope, however, that this clarifies where my view of the mechanisms of Free Culture goes.  The Free Culture movement *absolutely* needs an overhaul, but I don't see how discriminatory clauses can make that happen, because those discriminatory clauses don't actually do what they want to do except accidentally.  And while we don't have perfect licenses, we can sort of see the shape of what those licenses might look like in the future.

Now, like I said last week, when I come back to this for the *actual* fifth post in the series, we'll springboard from that clarified idea of a "good license" to talk about the other half of the mechanisms of Free Culture, what we need to do more of as participants to make Free Culture do its job, because you can't wind up a bunch of rules and hope for the best[^zRvBfD]...

[^zRvBfD]:  See also corporate management, education, democracy, personal relationships, and pretty much everything else of importance...

* * *

**Credits**:  I adapted the header image from [FC.o logo](https://www.flickr.com/photos/mllerustad/117878252/in/set-72057594090576065/) by [Karen Rustad Tölva](https://www.flickr.com/photos/mllerustad/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license, created for [FreeCulture.org](http://freeculture.org/).
