---
layout: post
title: Developer Diary, Long Count Begins
date: 2025-08-11 07:07:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, fresh-rss, ham-newsletter, mini-server, nginx]
summary: Progress on assorted projects
thumbnail: /blog/assets/East-side-of-stela-C-Quirigua.png
offset: -30%
description: This week's projects include the end(?) of computer woes, the blog's code, and the Ham newsletter system.
spell: Quirigua baktun katun uinal Ahau Cumku fastcgi param params Posio Redis cron Notoboto
proofed: true
---

* Ignore for ToC
{:toc}

Nobody really celebrates it like you might expect, but today marks the five thousand, one hundred thirty-ninth anniversary of the alleged creation of the world in the Mesoamerican (mostly Mayan) [Long Count calendar](https://en.wikipedia.org/wiki/Mesoamerican_Long_Count_calendar).

![East side of stela C, Quirigua with mythical creation date in 13 (or 0) baktun, 0 katun, 0 tun, 0 uinal, 0 kin, 4 Ahau and 8 Cumku and corresponds to August 11, 3114 BCE, in the Gregorian calendar](/blog/assets/East-side-of-stela-C-Quirigua.png "And yet, no Mayan has ever remembered my birthday...")

If you remember weird people worrying about what would happen on the 2012 December solstice, that mess came from certain extremists---the same sorts of extremists who want to see [personality patterns in birth year]({% post_url 2021-08-15-generations %})---believing that the date of the previous creation of the world, which happened to share its Long Count designation with that December, suggested a full cycle that would complete with our destruction and the presumed launch of a "fifth world."

With that, on to the week's projects.

## Argh, Part 8

This post will probably serve as the end of the computer moaning and groaning.  I have settled onto the new laptop---though I do need to buy beefier memory---feel fairly content with the server setup, and except when I find a new service to run on the server(s), I don't expect to have much to say.

Thanks to the people who found any of this interesting or amusing...

### Mini-Server, Part 6

It turns out that I spoke to soon on the NGINX configuration for Fresh RSS, last week, because I ran into a snag with what you see in that post.  I actually needed something more like this.

```
location /rss/ {
  index index.php index.html;
  alias /var/www/FreshRSS/p/;
  try_files $uri $uri/ index.php;
}
location ~ ^/rss/(.+?\.php)(/.*)?$ {
  alias /var/www/FreshRSS/p/$1;
  fastcgi_pass unix:/run/php/php8.2-fpm.sock;
  fastcgi_split_path_info ^(.+\.php)(/.*)$;
  set $path_info $fastcgi_path_info;
  fastcgi_param PATH_INFO $path_info;
  include fastcgi_params;
  fastcgi_param SCRIPT_FILENAME $request_filename;
}
```

Without that setup, the application itself worked well enough, but it couldn't find the API.

I won't bore you with the details of somebody else's code, but in short, Fresh RSS implements [Google Reader](https://en.wikipedia.org/wiki/Google_Reader)'s API, which has a base script `api/greader.php`, but then a path after that describing the endpoint, so you make requests of `api/greader.php/accounts/ClientLogin`, for example.  This setup notes the PHP file in the middle of the path and divvies up the information so that it can find the script and the script can process what it needs to process.

Last week's version put the `location`s in the wrong order for correct matching, tried to process the PHP files twice, *and* also assumed that a PHP file would only come at the end of a path.  Again, none of those mistakes impact the day-to-day functioning of the web app, but it makes a complete mess of the API.

More on the results of that, later in the post.

Along the way, I also considered installing [Posio](https://github.com/abrenaut/posio) so that I could have at least *one* game running, but Django, a spacial database, Redis, and more pieces feel like I shouldn't install that on an already-in-use Raspberry Pi.  I recommend the game, though.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

In a lot of ways, this week went to cleaning up minor changes to the blog.

First, because somebody joked about my small error and I couldn't help fixing it, the {% x %} plugin now correctly reports the sites "birth name" instead of its more famous alias.

Then, it seemed time for [Firefox](https://firefox.com) and [Mermaid](https://mermaid.js.org) to get their own annotation icons, the former distinct from [Mozilla](https://mozilla.org)'s.  That indicated the need to better distinguish between `x.com` URLs---in the rare cases that they appear here---and URLs with domain names that happen to end in `x.com`, such as the Firefox example.  Those icons also appear in the configuration file for Simple Icons annotations, so that they don't get lost.

Then, over to the scripts, which will probably require a bit of back-story to make sense.

As I have probably mentioned, I now use my old laptop as the "night computer."  Specifically, when I go to bed, it runs [Blanket](https://apps.gnome.org/Blanket/) for general noise to keep me from noticing actual noise.  And it also runs a script of my own devising that lets me take quick notes if I wake up in the middle of the night, leaving any issues or sudden concerns for morning, plus giving me a quick test through my [Type Time](https://github.com/jcolag/TypeTime-old) project[^1].

[^1]: The first-thing-in-the-morning typing speed, plus walking speed throughout the day, generally looks like a quick-and-dirty proxy for sleep quality.

That script *also* previously kicked off the proofreading cycle for the day's blog post.  But since I no longer work on the blog from that machine, a bunch of JSON blobs indicating possible typos doesn't help over there.  Instead, that kick-off needs to happen on "this" machine---I gesture to the laptop immediately in front of me, as if anybody can see that action now, let alone after the post goes out---and if I want it to happen without my needing to remember it, then it should happen in a [cron](https://en.wikipedia.org/wiki/Cron) job.

All the way around that explanation, to say that the script needed some changes to run without a full Linux environment set up for it, such as making sure that the right version of [Node.js](https://nodejs.org/en) gets used for the relevant scripts.  Along the way, it also does some quick checking to make sure that files exist before acting on them, so that I don't need to worry about what to do about errors.

## Ham Newsletter

{% github jcolag/ham-newsletter %}

Having fixed [Fresh RSS](https://freshrss.org/) so that I can use the API, it seemed time to...well, you know, *use the API*.  Therefore, the repository now includes a `freshrss.js` script, based on the script that I created to grab starred/favorite/saved/important articles from Nextcloud's News plugin.

It may eventually require some additional work to get batches of posts, but I don't actually know if the API will require it, yet.

## Next

Once again, I don't really know.  As a result of my recent work on **Notoboto**, part of me wants to increase that code's modularity, so that I don't need to constantly sift through hundreds of lines to find what I need, and so that people can reuse the code more freely without needing to worry about dependencies.  And I still need to take stock of the projects that I had in maybe-interesting states before the old laptop bought the farm.

Plus, with GitHub now having an apparently official policy of [embrace AI or leave {% cc %}](https://www.businessinsider.com/github-ceo-developers-embrace-ai-or-get-out-2025-8?op=1)[^2], maybe I should take them up on that offer and leave, at least in terms of sending traffic there...

[^2]:  By the way, nothing makes the AI people look more desperate than these sorts of threats.  If the technology worked so well, then companies would see it as a strategic advantage and *shut up about it*.  Instead, they try to railroad each other and threaten us into adopting the Infinite Monkeys' Paws.  It smells quite a bit like they see the bubble about to burst and need somebody else to buy their paw from them to take on the curse...

* * *

**Credits**:  The header image is [East side of stela C, Quirigua](https://commons.wikimedia.org/wiki/File:East_side_of_stela_C,_Quirigua.PNG) by Cyrus Thomas, long in the public domain due to copyright expiration.
