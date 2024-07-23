---
layout: post
title: Developer Diary, Emancipation Day (observed)
date: 2024-07-08 08:27:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Henry-Highland-Garnet.png
offset: -15%
teaser: This week's projects include the blog's code, continuing to archive Fictopedia, and another bunch of library updates.
spell: Yun Gyeongbokgung Webmentions Fictopedia Arcada enuf CPREP Miniboost Nonogram
proofed: true
---

* Ignore for ToC
{:toc}

(**Note**:  Apologies to anybody who waits for these posts in real time, but I had trouble publishing...)

Look, in the nineteenth century, New York largely dropped the ball on slavery, constantly trying to find some new compromise between not having an open revolt from people who realized that the time had come or passed to abolish the institution, and not angering wealthy people who hated the idea of treating disadvantaged people like humans, especially if labor might cost them money.  Thank goodness that we no longer have *that* problem in this state, right...?  Ahem.

Anyway, after trying ideas such as maybe-freedom for people who spent years fighting in the army, kicking the can down the road in hopes that someone else would fix the problem, trying to build New York plantations, signing onto the Fugitive Slave Act, trying to turn slaves into indentured servants---so...slaves, but the kind that white people could serve as---and maybe freeing the children of slaves born after some arbitrary date, New York *finally* emancipated all slaves on July 5<sup>th</sup>, 1827.  Today, we observe the anniversary of finally getting this right on the second Monday of the month.

![Henry Highland Garnet](/blog/assets/Henry-Highland-Garnet.png "You have no idea how much work it took to find ONE picture of somebody who participated in the 1827 festivities or a place where something relevant took place...")

And on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Back in the ancient times---this past spring, in particular---to better support the [Indie Web]({% post_url 2024-03-13-indieweb-1 %}) and to find a permanent "original location" for any social media posts that I might choose to make, other than blog announcements and the routine activity that I collect in the [Social Media Roundup](/blog/tag/linkdump) blog posts, I developed a cheap way of pushing out posts that resemble social media posts.  I created them with the intent of using more Webmentions, but always imagined them as a place to dump transient thoughts that didn't rate a full post or a newsletter piece.

However, I had a small problem:  Discoverability.  Unless I embed the posts in another post, nobody would ever see them, because they don't show up in the blog's index, and I spent time to [exclude them from the RSS feed]({% post_url 2024-04-03-indieweb-4 %}).  That has kept me from using the format, since discoverability divides between a permanent social media home on one hand, and little more than a personal archive on the other.

To that end, the blog now has a [second RSS (technically Atom) feed](/blog/pseudosocial.xml), which only holds those posts that look like they belong on social media.  That solves *half* the problem, at least, where people who want to see those posts---when they finally start appearing---have a route to doing that.

## Fictopedia Archive

{% codeberg jcolag/fictopedia %}

As promised [last week]({% post_url 2024-07-01-canada %}), I gave the archive of Fictopedia's surviving content some much-needed attention.

For example, the styles look somewhat clearer, including showing links with the `new` class in red, to indicate that the original wiki had no such page, either.  Unfortunately, I don't see any way of marking the pages that I couldn't salvage, other than to literally go through every page to mark those links...and I refuse to do that.

However, we also have additional pages.  Half a dozen entries[^1] made it to the Internet Archive that either got trashed before or I missed during my original "salvage" operation.  I also generated category pages for every category listed in an article, rather than trying to use the pages of unknown quality and vintage on the Internet Archive.

[^1]:  If you don't want to hunt around, they include [Arcada Gardenia](https://jcolag.codeberg.page/fictopedia/Arcada_Gardenia.html), [Color Spectrum Fiasco](https://jcolag.codeberg.page/fictopedia/Color_Spectrum_Fiasco.html), [Great Southern Railway](https://jcolag.codeberg.page/fictopedia/Great_Southern_Railway.html), [Scuba Police, the band](https://jcolag.codeberg.page/fictopedia/The_Scuba_Police_%28Band%29.html) and a [disambiguation page](https://jcolag.codeberg.page/fictopedia/The_Scuba_Police_%28disambiguation%29.html), and [*When apples aren't enuf](https://jcolag.codeberg.page/fictopedia/When_apples_arent_enuf.html).

And speaking (again) of the IA, they managed to catch four user pages, which I doubt anybody will care about as such, but a couple have brief conversations that give some indication of how certain entries evolved.  Likewise, seven pages have their respective "talk" page conversations added to the bottom of the entry[^2], along with the [Main Page](https://jcolag.codeberg.page/fictopedia/Main_Page.html) now having fairly extensive content.

[^2]:  No list, here, but I do want to note that I editorialized a *tiny* bit on this part.  The talk pages for several [Falling Bodies](https://jcolag.codeberg.page/fictopedia/category-falling_bodies.html) entries include directions that anybody choosing to edit those pages should read all the pages to get the "right" tone and continuity, and I decided to exclude those repeated messages from this archive.  It doesn't add anything to the fictional aspects, other than the implication that somebody felt possessive towards it and didn't particularly like the idea of their community getting involved on their own terms.  It cuts against the spirit of this sort of project to say that everybody should feel empowered to find a consensus, *except* for this section where somebody needs to vet you as an expert on the fictional world.  The user in question didn't sign their message, so it comes off as an anonymous warning.  And frankly, neither the community nor the edit features exist anymore, so it seems unlikely that somebody will come along to make sweeping changes to those pages.  In that light, I saw no reason to preserve the messages.

And finally, I overhauled my [index page](https://jcolag.codeberg.page/fictopedia/), not only to include the new pages, but also to make navigating around at least a bit clearer.  My explanatory notes now hide under a `details`/`summary` pair, and I've broken up the list with headings per letter, plus sections for the categories and users.

Oh, actually, I have one more thing, here.  It doesn't show on the repository, but since I managed to grab some user pages, I sent an e-mail[^3] to Fictopedia's creator, Chris Reid...presumably *not* the actor, comedian, or association football goalkeeper, none of whom I've ever heard of before writing this paragraph.  I explained that, as a fan of the project, I created the archive, and wondered if anybody on their side might have kept a backup of the site, so that I can work on completing the archive.  If I hear back, I'll mention it here before trying to figure out how to extract the data.

[^3]:  I may change my mind later, but I opted to retain the e-mail address on the page(s) that had it, because role-at-Fictopedia doesn't reveal any personal information and either nobody uses the inbox anymore or somebody uses it for its intended purpose.

## Library Updates

Rather than wait for GitHub to complain to me about everything, I decided to get proactive, this week, upgrading all libraries in projects where convenient.  Those include [**CPREP Background Generator**](https://github.com/jcolag/background-generator), [**Ham Newsletter**](https://github.com/jcolag/ham-newsletter), my [**Mastodon Tool Trunk**](https://github.com/jcolag/tool-trunk), [**Miniboost**](https://github.com/jcolag/Miniboost), my [**Morning Dashboard**](https://github.com/jcolag/dash), [**Picture to Nonogram**](https://github.com/jcolag/picture-nonogram), [**Roku Wake**](https://github.com/jcolag/RokuWake), [**Socialite**](https://github.com/jcolag/socialite), and the blog's own code.

## Next

The next big undertaking on **Fictopedia** involves fixing the inter-page links.  For whatever reason, the conversion didn't always add an HTML extension to the filename---but usually did---so you currently can't always get from page to page, even when the destination page exists.  I don't *think* that I can do it automatically, so expect it to happen in batches over the upcoming weeks.  While there, I should also add links to the license page.

I also want to get a "social index" working on the blog, ideally embedding the entire posts and paginating, but I'll need to see what options I have open to me.

* * *

**Credits**:  The header image is [Henry Highland Garnet](https://commons.wikimedia.org/wiki/File:Henry_Highland_Garnet_by_James_U._Stead.jpg) by James U. Stead, long in the public domain due to expired copyright, or no copyright at all.
