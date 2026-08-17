---
layout: post
title: Developer Diary, North River
date: 2026-08-17 07:47:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, mini-server]
summary: Progress on assorted projects
thumbnail: /blog/assets/clermont-fulton.png
offset: -26%
description: This week's projects include my mini-server and some changes to blog plugins.
spell: tcAOGV tvg EXTINF EPGs Bensell Cron
proofed: true
---

* Ignore for ToC
{:toc}

This week's not-quite-interesting anniversary celebrates the launch of the {% wiki North_River_Steamboat|*North River*|en %} steamboat---"the *Clermont*" in some circles---the first steam-powered commercial water vessel, originally operating on the Hudson River between New York City and state capital Albany, which should make "North River" make a bit more sense as a name if you know the eastern United States.

![An illustration of the North River from Great Fortunes, and How They Were Made](/blog/assets/clermont-fulton.png "I love how you can tell that the artist added the foreground figures from right to left, starting out with realistic bodies pointing at the weird boat to a series of smaller figures...preparing for chest-bumps, maybe?")

And with that, on to the week's projects.

## Mini-Server, Part 29

While I haven't installed anything, some small modifications impressed me and might interest some readers.

As I mentioned in the second post on [escaping big companies]({% post_url 2026-08-09-shop-small-2 %}), Jellyfin has the ability to [add IPTV streams](https://jellyfin.org/docs/general/server/live-tv/setup-guide#m3u-tuner-specific-options), such as what companies now refer to as <dfn title="Free Ad-Supported Television">FAST</dfn> channels.  You add a Live TV source[^tcAOGV], identify it as an "M3U Tuner," and give it an M3U file.

[^tcAOGV]:  It also supports "Home Run" devices, antennas with a TV tuner and an Ethernet port.  Most likely, it only supports recent versions of the device, though, because it doesn't recognize the one that I bought (no great loss, since it can only pick up one channel, because of the hills in the area), even though Emby did, back when I still used Emby.

{% cw I admittedly haven't deeply considered the legal aspects of this.  It *seems* like copyright shouldn't care about this at all, since it doesn't involve breaking any DRM or even avoiding ads more than you already might, but I still don't care for including the links, in case it subjects them to more scrutiny. %}

After some searching, I landed on [IPTV.org's page](https://iptv-org.github.io/), which...I couldn't figure out how to use on the first try.  However, I did spot the link to their GitHub page, leading me to their [collections of channels](https://github.com/iptv-org/iptv), and *that* I could understand.  Click to the *streams* folder, and if you pick any file, and it has channels that you'd like, let's say their [US PBS stations](https://github.com/iptv-org/iptv/blob/master/streams/us_pbs.m3u)[^Zvlg5R], then you can click the *Raw* button to get the URL of the M3U file to add.

[^Zvlg5R]:  Many local PBS affiliates geo-block their streams preventing most people from watching this way, and you'll have a better experience through PBS's own apps, so I feel less conflicted about using them as an example.

That can get overwhelming, though, with some lengthy lists, many of which have redundant entries.  This also shows that the files have a clear format.

```
#EXTM3U
#EXTINF:-1 tvg-id="KETS21.us@HD",Arkansas PBS [Geo-blocked]
https://ketsdt.lls.pbs.org/out/v1/03c094dbd7874a4a8c3fe9fb10081bdb/index.m3u8
```

The files all start with the same `#EXTM3U` line.  Then you have two lines for each channel, one identifying it (`#EXTINF`, an ID, and the name) and one with the stream's URL.  If you have favorite channels from some service, then, you can quickly assemble your own file with only the channels that you want, save it to the server running Jellyfin, and use that as the M3U file.

For some reason, Jellyfin (at least the TV app) takes a while before it starts recognizing regular use of channels, but they do slowly make their way to the top of the list so that you can get to them easier.  It also defaults to a text-based search to filter the list.

That does a lot of work---if you know what you want to watch, then you can tune right in---but for the FAST channels that rotate through a lot of material, you want a schedule, information from the Electronic Program Guides (EPGs).  The same IPTV group happens to have a [script to download information from EPG providers](https://github.com/iptv-org/epg).  Personally, I found setting it up frustrating, but it eventually worked, and now runs every night as a {% wiki Cron|cron job %} to produce an XML file that Jellyfin accepts as one of its *TV Guide Data Providers*.

Because they occasionally need to throttle users to prevent abusive scraping, sometimes parts of the schedule don't come through, but it works more often than not, giving Jellyfin a full episode guide for at least most of the channels that interest me.

You could also pay for a (specific) service, saving all that hassle, at the expense of paying for and relying on a third-party service.

Anyway, between the two pieces, my Jellyfin server now mostly replaces the various "Live TV" apps for me.  That said, I should note that I have no insight into the *stability* of this setup.  For all I know, in a couple of weeks, I might need to redo a lot of this work or otherwise have trouble keeping Jellyfin looking at the right things.  But for now, it works well, and it doesn't exactly leave me without places to watch shows.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

As mentioned last time, the wiki plugin now escapes the page ID, so that I can, for example, refer to `Disambiguation_(disambiguation)` {% wiki Disambiguation_(disambiguation)|(a real page) %}, but the HTML will show it as `Disambiguation_%28disambiguation%29`, to minimize the chances of a parsing problem somewhere.  Likewise, it guesses at the page ID, if I only give it the title, especially useful for the [*Star Trek*](/blog/tag/star-trek) posts, where the overwhelming majority of links go to a guest star's page, letting me only specify the name, such as---not appearing in any *Star Trek* production, as far as I know---{% wiki Benjamin Franklin %}.

Oh, and the plugin also fails silently if something supplies it a non-string, which especially trips if I start using the plugin and don't fill it in.

{% cw Care to guess what else happened?|question %}

I also had a sudden urge to overhaul the content advisory plugin, so that it can support multiple kinds of boxes.

{% cw I don't actually know if I'll ever use these, but it seemed important at the time|info|Fun Fact %}

In addition to the conventional content advisories that I especially use in the [social media roundup](/blog/tag/link-dump) posts, it can now also produce boxes for informational asides and questions, plus a colorless box with a generic icon.  The last should never actually appear in a post, serving more as a fallback if I have a typo in specifying the variety of box, so that the blog doesn't stop building.

## Next

I think that I got most of the blog changes out of my system, though I might experiment with something.  Instead, I'll head back to Scrawls, to see if I can get the editor running more seriously, maybe also cleaning out some library updates, since I never slogged through that full backlog.

Oh, and based on a couple of deliveries over the past couple of days, I would also expect to see some recipe-type talk over the next couple of weeks.

* * *

**Credits**:  The header image is [Consternation at the Sight of Fulton's Monster](https://www.gutenberg.org/ebooks/15161) by G. F. and E. B. Bensell, long in the public domain due to expired copyrights.
