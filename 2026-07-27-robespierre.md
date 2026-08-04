---
layout: post
title: Developer Diary, Madame Guillotine Strikes
date: 2026-07-27 07:57:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [library-update, mini-server, scrawls]
summary: Progress on assorted projects
thumbnail: /blog/assets/terracotta-Robespierre-Deseine.png
offset: -53%
description: This week's projects include my mini-server, my Scrawls editor, and some library updates.
spell: Maximillen Blakeney Deseine Platner Tartube dlp ytdl Fýlakas Onomáton Twitterbot Miniboost Uxuyu Solresol
proofed: true
---

* Ignore for ToC
{:toc}

Lacking a more substantial holiday, on this day in 1794, the French Revolutionaries put {% wiki Maximilien_Robespierre|Maximillen Robespierre|en %} and {% wiki Louis_Antoine_de_Saint-Just|Louis Antoine de Saint-Just|en %} to death in the guillotine.  If the names sound familiar, the close friends---despite a strong start as staunch, pro-democracy voices---led the {% wiki Reign_of_Terror|Reign of Terror|en %}.  Louis also lends his name to the fictional Marguerite St. Just, the actress married to Percy Blakeney, the Scarlet Pimpernel, while Robespierre makes an appearance in many adaptations of the novel, not to mention each of them showing up in dozens of fictional works.

![Terracotta bust of Robespierre by Deseine, 1791](/blog/assets/terracotta-Robespierre-Deseine.png "Hey, that piece looks really shiny; can I get a closer look...?")

I'd say "if you want something less grim," but I only have {% wiki World_Hepatitis_Day|World Hepatitis Day|en %} as a backup...

And with that, on to the week's projects.

{% include newsletter.md
  media='Disability Pride Month'
  preview='an attempt at an off-the-grid correspondence course'
  topics='some quick thoughts about Graham Platner by way of old science fiction|an interlude in nature'
%}

## Mini-Server, Part 28

I have a small addition to the servers that someone else might find useful.  While I don't use YouTube for much of anything anymore---so little that I completely ignored it for that first post on [extricating ourselves from big companies]({% post_url 2026-07-19-shop-small-1 %})---I do try to follow a handful of channels, of which a minority post videos regularly.  Over the years, I have tried various approaches for avoiding YouTube itself, for a variety of reasons.

- It takes multiple seconds to decide whether it wants to show me a light or dark page, then takes longer to set the page up.
- The ads never stop.
- It keeps turning autoplay back on.
- Recommended videos show that it outright wants to feed me right-wing content, probably because the people who watch it fall for the ads.
- Alphabet tracks everything.
- Probably other things that I've forgotten about.

Meanwhile, solutions always seem brittle.

- [Tartube](https://tartube.org/) seemed *really* nice for a while, but keeping a desktop application open all the time means corrupting and repairing its database on almost every unexpected reboot, eventually unrecoverable.  Also, getting the videos on the server required keeping the desktop session open there, plus finding some way of organizing the videos for [Jellyfin](https://jellyfin.org/) to pick up so that I can watch on television before deleting.
- The various privacy-protecting interfaces, such as [Invidious](https://invidious.io/), break all the time when Alphabet changes YouTube's page layout.  It also means that I won't watch the videos on television.
- [Pipeline](https://flathub.org/en/apps/de.schmidhuberj.tubefeeder) means watching on the desktop, which I have accepted for the last year or so, but it has started to break, unable to play, then even to *list* videos.
- Again, I have probably missed some solutions that I've tried.

Taking a step back before looking for yet another alternative, I realized that I mostly only want the videos (temporarily) downloaded in place for Jellyfin to pick them up, ideally named in some useful format.  And I actually know *how* to do that, so let's have one more list to sketch out the minimal algorithm.

- Go to a YouTube channel's page, let's say for the [Blender Foundation](https://www.youtube.com/BlenderFoundation) so that everybody can follow along.
- In the biography ("Official YouTube channel for..."), click **more...**
- Scroll to the bottom of the pop-up box and click *Share channel*.
- Click *Copy channel ID*.  For Blender, you should now have `UCSMOQeBJ2RAnuFungnQOxLg` copied to your clipboard.
- Add that ID to the end of this URL:  `https://www.youtube.com/feeds/videos.xml?channel_id=`, so <https://www.youtube.com/feeds/videos.xml?channel_id=UCSMOQeBJ2RAnuFungnQOxLg>, in the Blender case.
- As you probably saw if you clicked the link, that gets you an RSS feed for the channel, so we can now treat the problem like an RSS feed reader---or podcast client, more specifically---would.
- For each `entry` element, do the following.
  - Find its `link` element and pull out that URL.
  - Have [yt-dlp](https://github.com/yt-dlp/yt-dlp) or similar download the video from the URL from the last step.
  - Grab any other interesting information, such as the `title`, `author`, and `published` elements.  Entries also have a `media:group` element, which has another title and link, the thumbnail image to use, a description, and so forth, which might prove useful to naming the file or providing metadata to the media server.
  - Wait an appropriate amount of time so that YouTube doesn't flag your IP address as violating its terms of service before repeating.
- Keep track of what we have downloaded so far, so that we don't download it again.

In other words, if I took some time to figure out how to best name the files and provide metadata for Jellyfin's consumption, then I could almost certainly write first-draft code that does this in less than an hour, parsing the RSS and turning it into something Jellyfin-friendly probably taking most of the time.  And if *I* could build a bare-bones version in an hour, surely over twenty years of frustrations, somebody else has done this and refined it.  In fact, for a while, podcast players started doing something like this, so plenty of people out there know how this works, and I only know *because* of that work.

That all brings me to [`ytdl-sub`](https://ytdl-sub.readthedocs.io/en/latest/).  It admittedly only runs on the command line, so doesn't have anything like a fancy interface.  But it does something like what I describe above---probably not via RSS---plus it names the files with seasons (named for the year) and episode number (probably the MMDD date and a two-digit counter), which Jellyfin likes.

I wrote a quick configuration file to set the working directory---putting all its files on a media drive, instead of the much smaller internal hard drive, since I don't know what it'll work on there---and followed their example for a "subscriptions" configuration, running it with the following.

```console
ytdl-sub sub subscriptions.yaml --config configuration.yaml
```

If you mark channel categories as "Only Recent," then it'll only grab the videos in a specified range and delete them as they age out on subsequent runs of the program, probably the right choice overall and what I want; if you don't, then it'll try to archive every video from every channel that you list, which I *assume* will trigger all sorts of throttling from YouTube and take forever to get everything into place.  I set up a {% wiki Cron|cron job|en %} to run it every night, and that should work well enough until Alphabet inevitably decides to destroy every podcast, client, script, and report around the world that has relied on those RSS feeds for decades, or the YouTube downloaders can't keep up with changes to the site.  Until then, at least, this feels like a close-enough solution.

I then added the download folder as a library of television shows in Jellyfin, which treats it like it does the DVD rips, but with only the handful of channels as shows instead of the maybe-too-many actual TV shows, giving me a (slower and tightly curated) version of YouTube that only needs Internet access for a while in the middle of the night.  Now, I can watch [**The Tiny Angry Witch** {% cc %}](https://www.tinyangrywitch.com/) in peace...

## Scrawls

{% codeberg jcolag/scrawls %}

The editor has finally seen some real progress.  Primarily, it now uses a configuration file written in YAML---which will eventually set the root folder---to set a version number for [Code Mirror](https://codemirror.net/5/), so that the HTML template doesn't need to pin itself to the known version.  Instead, it replaces the version with a clear placeholder (`~~~~`), which the server populates as needed.

It also, maybe temporarily, in a way that'll need to change in a few weeks, tracks the current open file, because the save-file code that I wrote needs the file object to call it.

The code also looks a bit cleaner, but I assume that nobody really cares about that...

## Library Updates

I needed to bump versions for libraries used by [Fýlakas Onomáton](https://github.com/jcolag/fylakas-onomaton), that [Generic Board Game](https://github.com/jcolag/generic-board-game) thing, the increasingly outdated [Library Twitterbot](https://github.com/jcolag/library-twtterbot), [Miniboost](https://github.com/jcolag/Miniboost), and [Uxuyu](https://github.com/jcolag/Uxuyu).

## Next

I want to get file saving and at least a gesture at a multi-document interface for Scrawls, and also have some minor work to do on the blog.  In fact, I have a new idea to experiment with, so we'll see if that percolates fast enough to push out during the week.  (If you want a hint, I dug out a Solresol dictionary for the first time in well over twenty years...)

* * *

**Credits**:  The header image is the [Robespierre IMG 2303](https://commons.wikimedia.org/wiki/File:Robespierre_IMG_2303.jpg) by [Rama](https://commons.wikimedia.org/wiki/User:Rama) (though Claude-André Deseine sculpted the bust), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 France](https://creativecommons.org/licenses/by-sa/2.0/fr/deed.en) license (though the bust long lost its copyright).
