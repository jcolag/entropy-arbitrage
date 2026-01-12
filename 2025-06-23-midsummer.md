---
layout: post
title: Developer Diary, Midsummer
date: 2025-06-23 08:41:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, css, library-update, mini-server, stenotype]
summary: Progress on assorted projects
thumbnail: /blog/assets/Mittsommerfest-in-Norwegen-Insel-Tysnes-IMG-4425WI.png
offset: -30%
description: This week's projects include a computer crisis, Stenotype Corner, the blog's code, and some library updates.
spell: stenotype Typey Codidact Tysnes nokogiri STOEUPB Klaviatura Sten Mashinki Bisheng Mittsommerfest Norwegen Insel
proofed: true
---

* Ignore for ToC
{:toc}

In defiance of the summer equinox the other day, much of the European-influenced world celebrates today as [Midsummer](https://en.wikipedia.org/wiki/Midsummer), where May Day allegedly began summer.  Unsurprisingly given the Northern Hemisphere's climate range this time of year, those celebrating generally do so with outdoor meals and bonfires.  I tend to see it as something of a precursor to the raft of patriotism-themed holidays that we see this time of year, which have largely replaced bonfires with fireworks, I assume to more efficiently traumatize pets.

Oh, if you'd like something less associated with recent horror cinema, we also have [United Nations Public Service Day](https://en.wikipedia.org/wiki/United_Nations_Public_Service_Awards), when the body bestows its Public Service Awards to those making creative contributions to improved public administration.  I'd bet that we could all brainstorm names that *won't* show up on the list...

![Midsummer bonfire in Tysnes, Norway](/blog/assets/Mittsommerfest-in-Norwegen-Insel-Tysnes-IMG-4425WI.png "I maintain that we recognize the equinoxes and solstices under various names and dates as excuses to stay up late with friends.")

Anyway, on to the week's projects.

## Argh

No, not a new project with a funny name (yet), but my new laptop died yesterday, so I send this to you---if it gets sent at all---from the at-least-fifteen-year-old laptop that I used before that one.  I have a ticket in, pleading with System 76[^1] to help me get the thing running again, but expect some..."hiccups" until I can either fire that thing up or at least use its hard drive as an external device to this monster.  I still had code to push to the repository, so things won't look up-to-date, and I might not have the capacity to announce posts to the usual social media sites.

[^1]:  I don't want to take a position on whether *you* should buy from them, especially since I only have the one experience, but I will point out that the one experience involved a mouse pad never quite working, erratic USB behavior (starting right after the warranty expired), a fragile power supply that actually started sparking, and software crashes that (I believe) fouled up the hard drive leading to a painful recovery effort for the day leading up to the final maybe-heat-related crash in the evening.  Again, I don't want to tell you where to put your money, and I admit that the laptop had some power to it, but the fact that it lasted only a small fraction of the lifespan of almost any computer that I ever bought from an overstock warehouse seems extremely concerning.  (I reserve the right to take this back if, during the week, they reveal that I can get the thing running again without needing to buy anything.)

Honestly, count it as a minor miracle if *this* goes out on Monday morning.  And don't even ask about my backup plan if this laptop fails.  I have one and I don't like it.

That grumbling aside, I do want to point out that my recovery system *mostly* worked.  I managed to pull the blog's code, its assets, and my private nightly backup---the full git repository plus the working tree---of the posts.  Especially since yesterday didn't allow me to do anything productive, I probably haven't lost much work.  As I type this, I have started converting the image assets to AVIF files, about ten percent of the way through.  It *should* complete by morning, but who knows...?

## Stenotype Corner

This time through, I finished [**Learn Plover!**](https://www.openstenoproject.org/learn-plover/home.html) It covered some things that I haven't seen elsewhere. I'd say that not much of it changed my thinking about all this, other than the "Prefix and Suffix Strokes" chapter, which feels like I'll never remember them. Oh, and one correction from resent posts: Tracking back to sources, it looks like the [book *does* have a Free Culture license](https://github.com/openstenoproject/learn-plover?tab=CC-BY-SA-4.0-1-ov-file#readme), though doesn't lift it in the text, for whatever reason. It doesn't seem like any other books in this vein exist for me to hit up next, though feel free to correct me.

Meanwhile, my weird speed slump continues, hovering around twenty words per minute.  Many of the errors slowing me down---other than getting a trailing s/z confused significantly more frequently in drills than in actual practice---seem to involve either the keyboard switches not activating or my finger not pressing them far enough, or occasionally a key "firing" when I don't expect it to, suggesting that I need to monitor my finger positioning more carefully.

The crash, mentioned above, might impact the future of this project for me.  I can *probably* get Plover running, here, but I can't really prioritize it.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Finally grabbing the opportunity to sit and work out the library conflicts on the blog, the blog now builds again.  If past posts didn't explain further than "conflict," then the automated update made it impossible to build everything, because of a conflict with [Nokogiri](https://nokogiri.org/), but if I tried to get everything up to date, a *different* gem/library's compatibility issues blocked the update.

Presumably, this blog doesn't have many readers who use [Jekyll](https://jekyllrb.com/) *and* haven't dealt with this sort of problem on their own, before, but on the chance that such readers do exist, or only for my purposes the next time I need to do this, I solved the problem by manually update that gem/library and *only* that one.

```console
bundle update nokogiri
```

That doesn't solve the other problem, but at least allows me to go back to checking in improvements without breaking posts.

In addition, it *finally* occurred to me to set the section headings in posts to start on a full line.

```CSS
h1, h2, h3, h4, h5, h6 {
  clear: both;
}
```

The [`clear`](https://developer.mozilla.org/en-US/docs/Web/CSS/clear) property says to make sure that the element sits below any elements set to `float` to the left and/or right, such as---for example---the GitHub or Codeberg previews in these [Developer Diary](/blog/tag/dev-journal) posts.  Most critically for these posts, it means that I no longer need to prattle on for a few lines so that the repository link previews don't start stacking up into unreadability.

After that, you've seen in the past few posts an SVG stenography keyboard to illustrate the *Stenotype Corner* sections.

{% steno STOEUPB %}

To save myself some time, I based the underlying image on [Klaviatura Sten Mashinki](https://commons.wikimedia.org/wiki/File:KlaviaturaStenMashinki.svg), released into the public domain, but which took a not-insignificant amount of [Inkscape](https://inkscape.org/) work to get something that "feels right" for the blog.  To get the curved bottoms, I needed to convert the rectangle objects to a path, select the bottom two corners with the "Node Tool," and add a "path effect" for the corners, with "Change only selected nodes" selected.

The plugin itself converts the stenography key list---such as STOEUPB above---to a set of IDs in the image, and adds a `pressed` class to the element to change the color.  Adding some styles to flip the light and dark areas under dark mode, and a tool tip to show the keys, completes the task.

## Library Updates

This week, I needed to update some libraries for [**Bisheng Reader**](https://github.com/jcolag/bisheng), [**Git Graft**](https://github.com/jcolag/git-graft), and [**Renewals Database**](https://github.com/jcolag/RenewDB).

## Next

This week, expect a bit more work on the blog as I clear out that backlog.  And as I've mentioned for a couple of weeks, now, I do have at least the seeds of some new projects.

On the other hand, with my computer situation and the heatwave hammering my area, I'll actually settle for getting posts out, so maybe consider "expect" in the previous paragraph an exaggeration...

* * *

**Credits**:  The header image is [Mittsommerfest in Norwegen, Insel Tysnes](https://commons.wikimedia.org/wiki/File:Mittsommerfest_in_Norwegen,_Insel_Tysnes_IMG_4425WI.jpg) by [Kora27](https://commons.wikimedia.org/wiki/User:Kora27), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
