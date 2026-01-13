---
layout: post
title: Developer Diary, Celebrate Bisexuality Day
date: 2024-09-23 07:10:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, codidact, cohost, css, lights-edge]
summary: Progress on assorted projects
thumbnail: /blog/assets/Bisexual_Pride_Flag.svg
offset: -30%
teaser: This week's projects include Codidact answers, the blog's code, my (empty but waiting) Cohost archive, and toys and the website for The Light's Edge.
spell: Codidact img Spoutible Pinkary
proofed: true
---

* Ignore for ToC
{:toc}

Today marks [Celebrate Bisexuality Day](https://en.wikipedia.org/wiki/Celebrate_Bisexuality_Day), also often referred to as a Pride or Visibility day instead of a name that sounds more like directions, but it has a goal of helping to raise awareness of the issues that bisexual people face, and to acknowledge the bisexual people in our circles, who---rumor has it---could look like *anyone*.

![The bisexual pride flag](/blog/assets/Bisexual_Pride_Flag.svg "I see you, or at least some of you.  Actually, could you shimmy to the left a little so that the tree doesn't block you...?")

We also had the equinox yesterday, kicking off autumn around here.

Anyway, on we go to the projects.

## Codidact

I gave another question a shot on Codidact:  [Our site incubator concept needs a re-think](https://meta.codidact.com/posts/292599/292615#answer-292615).  If you'd like an excuse to get involved with the community, this actually feels like a good question for that, since a newcomer would definitely have better insight into the flaws in the existing system than somebody who has used the site for months or years.

Something to consider about the site in general:  I like that it seems to prefer to encourage conversation to "answer the question and move on," but it likewise seems troubling that the community that they've gathered seems mostly disinclined to such conversation.  In particular, I see that almost every answer across the site has a down-vote or two, as if somebody with a vendetta wants to hurt people who really don't care about the numbers, instead of talking out whatever emotional problem they need to deal with.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Especially on this page, it will probably please many of you that I finally realized that I should invert the colors for the GitHub and Codeberg preview boxes, over to the right, when you view the page in dark mode.  For Codeberg, I use the same `light-dark` CSS function that I use everywhere else.  For GitHub, though, since they provide an image, I needed to "cheat" and use the following.

```CSS
img.github {
  filter: invert(0.9);
}
```

The [`invert()`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter-function/invert) filter does what it sounds like, flipping all color values in the image.  If you set it to go halfway (`invert(0.5)`), then everything in the image turns gray, which doesn't generally help much.  Here, though, `0.9` turns the background to a dark gray and the text to a light gray.  It also makes my avatar look weird(er), but nobody cares about that.

In other news, I updated the [about page](/blog/about.html), replaced the magnifying glass emoji (linking to the search page) with the more consistent Font Awesome magnifying glass, removed the tag icon from the suggestions pop-over panel since that now happens in CSS, and---maybe most important---started posting the header images with my blog announcements to Mastodon.

The images have felt like a funny situation.  As some long-time readers might remember, Mastodon announcements came first.  And since I never took the post header images particularly seriously, I didn't bother to figure out how to add the image to the [`toot`](https://github.com/ihabunek/toot) utility.  However, as I started posting announcements to other places[^1] and some places felt more like a community, it felt like I should do more than announce blog posts with more than a title, URL, and briefest summary.  The [`teaser`]({% post_url 2023-02-27-marathi %}) metadata came out of that realization in early 2023, and as long as I had to copy things into multiple sites anyway, I figured that I might as well add the image to make the announcements mildly more interesting.

[^1]:  If you want to go hunting, that list currently includes [Buy Me a Coffee](https://www.buymeacoffee.com/jcolag), [Spoutible](https://spoutible.com/jcolag), [Pinkary](https://pinkary.com/@jcolag), and---until the end of the month---[Cohost](https://cohost.org/jcolag).

Mastodon got the teaser lines, but not the images, because (again) it didn't seem worth checking if the tool would do the job.  However, with Cohost closing, it reminded me that Mastodon---which I've mostly considered the "source of truth" in my social media landscape---now lagged behind everybody else.  To fix that, I actually checked the program instructions to find out that `toot --media "path/to/image" --description "alt text for the image" ...` does what I should've handled years ago.

## Cohost Archive

{% github jcolag/cohost %}

Nothing lives here, yet.  But as I've hinted since Cohost announced their closure, I'll find some way of creating a permanent archive of my posts, based on what they give me in their export.

I won't upload the entire thing, because the archive will apparently include a contact page to find people, and publishing that seems like the worst idea possible.  If it includes comments, I'll also want to remove those, since I don't have permission to release them under a license.

That said, I'll probably also dig through my posts---and comments, if available---and turn some of them into posts here, if they might make sense in this context.

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

Probably most usefully, the README file now indicates what kinds of files we have for each toy.  I have no idea how much variety we might see in those files, but I wanted people with the relevant knowledge to understand at a glance how much work it'll take them to use or modify the source files.

In addition, I somehow forgot to add a license for LLL-1's STL file, and have now corrected that oversight.

## The Light's Edge

{% codeberg jcolag/thelightsedge %}

Because this repository uses content from so many sources, I realized that this actually makes one of the best places to conform to [REUSE](https://reuse.software/).  I mean, it looks like we have ten licenses[^2], including some images that combine multiple sources.

[^2]: Licenses so far include AGPL-3.0-or-later, CC-BY-2.0, CC-BY-3.0, CC-BY-4.0, CC-BY-SA-2.0, CC-BY-SA-3.0, CC-BY-SA-4.0, CC0-1.0, MIT, and OFL-1.1.

I haven't finished, yet, but I have at least *started* the process.  I have a handful of files (seven in particular) that require more effort than looking up the single license, because some, as mentioned, compose multiple other sources, and one doesn't actually have a license---the proprietary Buy Me a Coffee logo---and I'll need to learn how to specify that.

## Next

It looks like the time has come to start chipping away at the backlog of library updates, because I have *plenty* of those to take care of.

* * *

**Credits**:  The header image is [Bisexual Pride Flag](https://web.archive.org/web/20120204071024/http://www.biflag.com/ActGraphics.asp) by Michael Page, presumed in the public domain as ineligible for copyright, based on its utilitarian nature.
