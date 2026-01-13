---
layout: post
title: Developer Diary, Ozone Day
date: 2024-09-16 07:20:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, codidact, fictopedia, ham-newsletter, lights-edge, notoboto, social-media]
summary: Progress on assorted projects
thumbnail: /blog/assets/Ozone-over-southern-hemisphere-Sep11-1957-2001.gif
offset: -48%
teaser: This week's projects include social media updates, Codidact answers (some old), the blog's code, Ham Newsletter, Notoboto, my archive of Fictopedia, and toys for The Light's Edge.
spell: Codidact Notoboto fictopedia Radicle endraw OpenSCAD RedAndr Unported
proofed: true
---

* Ignore for ToC
{:toc}

Today marks---deep breath...---[International Day for the Preservation of the Ozone Layer](https://en.wikipedia.org/wiki/International_Day_for_the_Preservation_of_the_Ozone_Layer), commemorating the 1987 date signing the [Montreal Protocol](https://en.wikipedia.org/wiki/Montreal_Protocol).

![Animation of the ozone layer over the Southern Hemisphere, 1957-2001](/blog/assets/Ozone-over-southern-hemisphere-Sep11-1957-2001.gif "I once pitched raising money by selling ozone shovels...")

If you'd like a more traditional style of holiday, you can try the [Cry of Dolores](https://en.wikipedia.org/wiki/Cry_of_Dolores), celebrating [Miguel Hidalgo y Costilla](https://en.wikipedia.org/wiki/Miguel_Hidalgo_y_Costilla) using the church bells to signal the start of the [Mexican War of Independence](https://en.wikipedia.org/wiki/Mexican_War_of_Independence).

Otherwise, let's check out the projects.

## Social Media

It looks like [Cohost will end normal operations](https://cohost.org/staff/post/7611443-cohost-to-shut-down) at the end of the month, really this time, not a conclusion drawn from scant facts.  Even though they didn't necessarily fit my vision of a long-term, stable social media site[^1], I have enjoyed getting to know at least a few members of the community over there, so the decision disappoints me, but people need to do what they need to do.  I'll leave it to the folks who felt a (positive or negative) stake in the site's success to argue over the tipping points and what could have gone differently, though you should also expect a small piece on it in the September [newsletter](https://buymeacoffee.com/jcolag).

[^1]:  If you want to grow big in the space, then you need to avoid moderating terrible people to "boost engagement," so that people look at the ads, *or* you need to sell user content for data-mining.  If you want to stay small but survive, then you need to distribute the load better than one small company running one website, such as through federation and Free Software.  I still don't believe that it works in any other way, though I also believe that we should support it when people make a good-faith attempt at it.

I'll continue posting there---to the extent that I post *anywhere* other than the blog, here---until the end of the month when they make everything read-only.  And once they provide a full export (or somebody from the community does a better job), I'll give my posts there the same treatment that I gave to my exported posts from [Twitter](https://jcolag.github.io/twitter/), [Pebble](https://jcolag.github.io/pebble/), and [Post.News](https://jcolag.github.io/post.news/).  Most of my original writing has probably already featured on the blog, except for some that I planned to expand into larger posts later, but I do want to make that a consistent tribute to the sites that didn't survive.

Regardless, I no longer recommend following me there, since it'll close up shop completely at the end of the year, and that won't get you anything.

## Codidact

I nearly forgot that I contributed two quick answers to the "Incubator" on Codidact, for their prospective world-building community.

 * [What could be a believable reason for technologically advanced underground people to not notice the end of surface war for hundreds of years?](https://proposals.codidact.com/posts/292509/292520#answer-292520)
 * [What's the least traumatic way to integrate resurrected historical humans into modern society?](https://proposals.codidact.com/posts/292552/292576#answer-292576)

And looking through my history, it looks like I also neglected my answers on these.

 * [How do I fry donuts safely?](https://cooking.codidact.com/posts/291872/291918#answer-291918),
 * [Seeking feedback on experience with open source chat software](https://meta.codidact.com/posts/292005/292013#answer-292013), and
 * [Don't close questions for lack of detail/confusion](https://software.codidact.com/posts/291064/291557#answer-291557).

In other words, I forgot to link people to what I wrote after promising to do so.  At this point, I have pretty much stopped visiting Stack Overflow, by the way, not that I have participated in over two years.  But the ongoing moderation issues and their bizarre positions on AI make me less interested in returning, and Codidact---at least for now---seems like it has a better vision.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

For my personal purposes, I made two tiny but critical changes to the build script.

 * Uploading to the server now compares checksum of files, rather than dates, before deciding whether to overwrite anything.
 * My local test server now rebuilds incrementally.

The first speeds up deployment significantly, because the date of every file *always* changes between posts, because I rebuild the site every time[^2].  The second lets me see changes in a second or two, instead of waiting thirty to forty seconds every time that I save changes to a post.  Those make me extremely happy, since it means less sitting around waiting for Jekyll to give me what I need.

[^2]:  Because I have many partial and some complete posts ready weeks and occasionally months in advance, I either rebuild the entire blog or you get the developer diary posts for the rest of the month now, before I write anything in them, which doesn't help anybody.

I also added a script to test the "embed small image to the side of the text" plugin, to make sure that it uses AVIF files when available.  Since I couldn't think of a better place to stash it, the table (YAML file) of tag explanations now lives in the repository.  I updated the list of files to ignore, so that people don't accidentally download a script from the website.

Front-facing, post titles now have a `white-space: balance` style applied, so that if they run longer than a line, the lines will have roughly the same length, so that you won't see a single-word "dangler."

And my favorite change, mentioned last time, I finally added a plugin to simplify my referring to {% x %}, by remembering the HTML code for the double-stroke letter and says "née Twitter" in the title-text.  Now I can type `{% raw %}{% x %}{% endraw %}`[^3] and not need to think about the details.

[^3]:  Ah-ha, I finally figured out how to embed Liquid code into a post.  Jekyll has a `raw`/`endraw` tag pair, with nothing inside getting interpreted.

Oh, and I also updated the 404 error page again.

## Ham Newsletter

{% github jcolag/ham-newsletter %}

I forget if I actually noticed the problem this month or last month, but when dealing with old posts, the code that checks for changes can't always find a summary---since I don't think that I started including them until later---and so had difficulties assembling the newsletter.

To fix that, every post now has a default summary of "No summary found," replaced if the code can find anything more suitable.  I'd rather a better solution, but don't exactly see one...

## Notoboto

{% github jcolag/Notoboto %}

When I added the code to embed images last week, because of the way that I generally type, I didn't notice that---sometimes, but not always---the editor will pull attention away from where the user types to the newly re-inserted image, which made embedding more confusing than helpful.

After some quick research, I found the `see` command, which directs the text widget to pull a particular location into view.  Combining it with the work that I did for the search-and-replace code to determine where the user can type next, it only occasionally looks jarring, presumably if a screen update happens between re-embedding and pushing the caret back into view.  More importantly, it never interrupts the flow.

## Fictopedia Archive

{% codeberg jcolag/fictopedia %}

Even though everything in the repository---except for my CSS files---has the same license, because it includes so many small files where somebody else owns the copyright on the content, I decided that this made another good target for [REUSE](https://reuse.software/).  While probably not as directly productive as I hope, the fact that the Fictopedia project existed entirely for the purpose of people picking out elements that appeal to them made it a good candidate for distributing the license identification, at least in theory.

This also has the potential to simplify processes down the road.  For example, if somebody wanted to revive the project as a fork of this archive, they can identify new material with the copyright notes, separating theirs from the work attributed to the Fictopedia community.

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

First, as a small experiment, you can now get this repository through [Radicle](https://radicle.xyz), "an open source, peer-to-peer code collaboration stack built on Git."  In other words, it looks kind of like GitHub, but without a centralized server.

At least assuming that I don't need to perpetually run my node, and until I decide that I might not want to associate with this network, I believe that you can clone the repository like so.

```console
rad clone rad:zD8EQAjWgSqRgDwDFjPasEb7aEEW
```

Why might I abruptly back away from the project?  They [explain their motivations](https://radicle.xyz/guides/user) as follows.

 > Furthermore, our world is increasingly polarized, and this reality is finding its way into software companies and therefore into software products. Users are banned from using a platform because of their geographic location or the ideas they stand for.

That reads to me like "we don't like that people keep rejecting ideas from Nazis."  Nobody seems to worry about "polarization" silencing "the ideas they stand for" besides the people aggressively peddling ideas debunked hundreds of years ago.  I think of it as a dog-whistle as opposed to a genuine complaint, because outside the right wing, people generally provide specifics of who has gotten silenced, knowing that their choice of example won't embarrass the project.  GitHub *has* blocked Iran, Syria, and Crimea, which I disagree with, but they do that because of (regrettable) government sanctions that could get the entire site shut down, not because of some ideological slant.  But because of the implied politics, the Radicle network *could* quickly become a haven for misogynistic AI undressing apps, violent propaganda, and the like, that nobody else will host.

Or I might abandon it, if I need to keep my server running for people to access the repository.

Despite those concerns, the project looks interesting, and I like this sort of anti-corporate, DIY environment, so I'll at least give it a brief try with an occasional low-stakes repository to see how it works in action.

Beyond that, I cleaned up the shape of LLL-1's head a bit, with the intent of eventually printing it in one piece.

Oh, and I also added the STL export to the archive, since that probably makes more sense for most people who want to use the model for something.  OpenSCAD makes more sense to me, but people who want to make their own modifications will probably want to do so with a more conventional CAD program, and 3D animation tools such as Blender will import STL files.

## Next

I don't really know.  This might quickly become a good week to clean out the backlog of library updates.

* * *

**Credits**:  The header image is [Ozone over Southern Hemisphere Sep11 1957-2001](https://commons.wikimedia.org/wiki/File:Ozone_over_southern_hemisphere_Sep11_1957-2001.gif) by [RedAndr](https://commons.wikimedia.org/wiki/User:RedAndr), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license.
