---
layout: post
title: Developer Diary, World Environment Day
date: 2023-06-05 06:49:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/15636978156_5313675756_o.png
teaser: This week's projects include my Periodic Scripts and a mess of library updates.
proofed: true
---

* Ignore for ToC
{:toc}

Today celebrates [World Environment Day](https://en.wikipedia.org/wiki/World_Environment_Day), a platform to advocate for various environmental issues.  Every year, the committee behind it chooses a host city---or small country, in recent years---and theme.  While I can't find a reference to today's host, but the [official website](https://www.worldenvironmentday.global/) tells me that we have *Beat Plastic Pollution* serving as this year's theme.

![The helmet worn by the UN Peacekeepers force](/blog/assets/15636978156_5313675756_o.png "Do they pad them on the outside?  That seems irresponsible")

I'll leave it to all of you to decide whether my projects look more like pollution...

## Periodic Scripts

{% github jcolag/periodic-scripts %}

I discovered that I didn't sanitize my `editor.sh` script, so the history unfortunately will perpetually have some (misleading, ironically) traces of the layout of my system in the repository history.  Therefore, I tossed off a quick change that replaced opening specific files with opening the files specified on the command line.

We have a nice loop to do that.

```sh
for file in "$@"
do
  sleep 0.25
  (nohup "$editor" "$file" 2>/dev/null &)
done
```

If you don't have much familiarity with the various shell languages, `$@` holds the list of parameters.

I also fixed a bug that someone mentioned, where the default MIME handler might refer to a desktop shortcut file.  In that case, the script searches the---presumed common---shortcut for its `Exec=` line, and continues from there to find the application to run.

And `diary.sh` now has all its variables quoted.  They should never have spaces in them, but if they somehow do, it will no longer derail the entire script.

## Library Updates

I needed to bump (finally) versions of libraries for [**Bicker**](https://github.com/jcolag/Bicker), [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton), [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Renewal DB**](https://github.com/jcolag/RenewDB), [**slackup**](https://github.com/jcolag/slackup), and [**Uxuyu**](https://github.com/jcolag/Uxuyu).

## Next

I expect that this week will continue the library updates.  I let them sit long enough that GitHub's bot stopped telling me about changes.  Plus, I expect to not have much discretionary time for a bit.

* * *

**Credits**:  The header image is [Marine Debris Removal in the Northwestern Hawaiian Islands](https://www.flickr.com/photos/40322276@N04/15636978156/) by [NOAA's National Ocean Service](https://www.flickr.com/photos/usoceangov/), in the public domain as a work of the United States government.
