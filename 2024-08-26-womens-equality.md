---
layout: post
title: Developer Diary, Women's Equality Day
date: 2024-08-26 07:31:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/30004393205_1c983b741d_o.png
offset: -15%
teaser: This week's projects include the blog's newsletter, the blog's code, my Codeberg profile, more toys (LLL-1 revisited), and my home page.
spell: LLL-1 Eshoo Speier coc devjournal bookclub em es imgr Aether Notoboto
proofed: true
---

* Ignore for ToC
{:toc}

Today, we celebrate [Women's Equality Day](https://en.wikipedia.org/wiki/Women%27s_Equality_Day), commemorating the adoption of the Nineteenth Amendment to the United States Constitution, prohibiting governments from blocking people from voting based on gender.

![Nancy Pelosi, Anna Eshoo, Barbara Lee, and Jackie Speier speaking at a UCSF Womens Equality Day event](/blog/assets/30004393205_1c983b741d_o.png "The lab coat assures accuracy...")

And on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the thirty-first, one of the occasions when the Saturday of the last week of the month falls in the actual month.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the third of September.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For July, I wrote a quick piece updating the status of trying to keep out of people-search engines (and a draft that might need to wait for next month), discussed media consumption skewed slightly towards celebrating Disability Pride Month, and provided some background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

This week mostly went to cleaning up the changes that I've made to the blog over the last couple of weeks.  With the link annotations indicating where I send you, the time had come to remove the emoji placeholders that I used on the Free Culture "send help" and mailing list subscription verbiage.  The [search page](/blog/search) now has a better color scheme *and* uses the little "JC" logo as the spinner[^1] instead of a Font Awesome glyph.  The CSS changes should have stabilized by now, including more Mastodon servers that get the icon.

[^1]:  I have taken one more step towards becoming Batman from the 1960s TV series...

In addition, I updated the [code of conduct](/coc) with some---but not all---language updates from the [Contributor Covenant](https://www.contributor-covenant.org/) that I use as its source.

Most usefully, though, assuming that I haven't broken anything, tags in posts can now have hyphens in them, so that I don't have clunky compound words like *devjournal* or *bookclub* in the posts...except in this sentence, I guess.  The tag pages haven't changed, so if you have a bookmark somewhere or rely on your browser history, then everything will continue to work.  But this saves me some angst during proofreading and ideally makes the intent clearer when you click on a tag at the bottom of the page.

Once again, I should have thought about this four-and-change years ago when I built the tag system, but didn't.

## Codeberg Profile

{% codeberg jcolag/pages %}

I edited my "profile page"---or whatever they call the thing---on Codeberg, mostly changing emphasis and clarifying some thoughts.

You can see, in both the Markdown and HTML versions, that I didn't do anything more significant than tell people that I don't mind if they reach out to me.

For those who need an explanation, Codeberg has a feature where, if you have a repository called **pages**, and you have some setting or other enabled, then it deploys the contents of the repository to `https://[your-user-id].codeberg.page`, such as [my profile](https://jcolag.codeberg.page/).  This competes with GitHub Pages, where you name the repository something like `[your-user-id].github.io` and it deploys to that URL...and now I realize that [my GitHub page](https://jcolag.github.io/) hasn't gotten an update in almost a decade...

## The Light's Edge --- Toys

{% codeberg jcolag/lights-edge-toys %}

Our buddy LLL-1 has gotten some nice improvements, I think.  E slimmed down dramatically, over the past week, making em more credible as a model for a humanoid character.  Es limb lengths and head size now follow the height of the model, which they always should have done.

Maybe most usefully, though, es model now includes a shaft through the torso to attach the front and back with a #6 machine screw under the [Unified Thread Standard](https://en.wikipedia.org/wiki/Unified_Thread_Standard)---so about three and a half millimeters in diameter---which I believe that you can find pretty much anywhere.  It shows some flaws in the design, like I still need to tweak the pegs holding the limbs in place, but this should make the figures easier to assemble *and* more secure than tape or glue.

![LLL-1 considering the exploration of a crystalline cavern](/blog/assets/lights-edge-lll-2-a.png "Pardon the dust. I've had that geode on various shelves for over thirty years and never figured out how to clean it, but at least I finally found a use for it...")

I used half-inch-long screws for the assembly, by the way, because the local store had them in stock, but I'd suggest dropping to three-eighths of an inch or a quarter-inch to keep everything secure.  You can see the screw head protruding out of es back *and* a significant gap between the front and back of es torso from where I over-tightened after reaching the bottom of the shaft.

Otherwise, some unused code also went away.

However, I promised you more toys, including recycling some old junk, so I present the cheapest "vehicle" toy as an example, even though it probably won't get a spot in the repository.

![LLL-1 piloting a toilet paper tube in space](/blog/assets/lights-edge-lll-2-b.png "I couldn't resist hamming it up in the lower-right.")

{% imgr The interior of a toilet paper roll with an oval hacked from its surface and affixed with transparent tape straight below the hole, forming a cheap seat|roll-ship-2-interior.png|Honestly, this looks better than some real toys that I owned in the 1970s, if I remember correctly... %}

Yes, I used the core from a toilet paper roll and---poorly---cut a hole in it for the cockpit and that mostly finished it.  While not necessary, because the arms hold LLL-1 in place, I taped the cardboard that I removed from the hole down as the "seat," to boost em up a bit.  And yes, it looks silly, but cover the front, maybe add some wings, and find a clear cap as the equivalent of a cockpit canopy, and we quickly hit a tipping point where even this literal trash starts to look credible, even if the brown feels more like it would better fit [**The Aether Age**]({% post_url 2024-07-20-helios-1 %}) than any mainstream science fiction franchise.

More to the point, though, as I mentioned [last time]({% post_url 2024-08-19-humanitarian %}), I chose this scale at least partly for the flexibility in using junk as part of the toys.

## Main Website, Too

While I haven't decided whether to make the repository with [my home page](https://john.colagioia.net/) public---other than links to things that I do, I don't have anything more interesting than my résumé, which doesn't help anybody to have under a public license or letting people dig through the history that I can see---I have propagated the same dark mode color scheme from the blog down there.

## Next

Now that I have two forms of tags in the blog, I might put a bit more effort into generating the pages, particularly creating empty pages with the hyphenated forms that redirect you to the actual tag page, in case somebody tries to get there manually.  Likewise, especially for the most commonly used tags, I'd love to put together some scheme that lets me describe the intent behind the tag somewhere on the page.

Oh, and finishing this post brought up a glaring error in my image-handling that I hope nobody else noticed.

Alongside that, I also have another idea for **Notoboto**, which I've neglected for a shockingly long time.

Also, expect to see **The Light's Edge** continue to creep forward.  As mentioned, I want to experiment more with the pegs holding the limbs and head in place and tweak some of the torso.

* * *

**Credits**:  The header image is [Women’s Equality Day (30004393205)](https://www.flickr.com/photos/speakerpelosi/30004393205/) by [Nancy Pelosi's Office](https://www.flickr.com/photos/speakerpelosi/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/) license...but probably also technically in the public domain, since that account comes from her official office.
