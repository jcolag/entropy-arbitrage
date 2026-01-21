---
layout: post
title: Developer Diary, Fred Korematsu Day
date: 2023-01-30 06:55:05-0500
categories:
tags: [programming, project, devjournal]
labels: [tool-trunk]
summary: Progress on assorted projects
thumbnail: /blog/assets/Luggage-Japanese-American-internment.png
proofed: true
---

* Ignore for ToC
{:toc}

Today, California and other states celebrate [Fred Korematsu Day of Civil Liberties and the Constitution](https://en.wikipedia.org/wiki/Fred_Korematsu_Day), honoring the Japanese-American civil rights activist whose name you may recognize from [*Korematsu v US*](https://en.wikipedia.org/wiki/Korematsu_v._US), the Supreme Court case attempting to fight the internment of Japanese-Americans during World War II.

![Baggage held at an internment camp](/blog/assets/Luggage-Japanese-American-internment.png "A photographer somehow saw an internment camp and decided that the world needed to see the baggage claim.  Well, it saves us the trauma of looking at prisoners, so I guess I owe that lousy photographer some modest thanks...")

Like Martin Luther King earlier in the month, I can't exactly top Korematsu, so let's move on to software.

## Mastodon Tool Trunk

{% github jcolag/tool-trunk %}

As mentioned [last week]({% post_url 2023-01-23-freedom %}), I decided that I can improve my workflow for scheduling [toots on Mastodon](https://mastodon.social/@jcolag/)---and, yes, still cross-posting to Twitter, for however long that bridge remains---by writing the [Friday round-up posts](/blog/tag/linkdump) first, then parsing the formulaic post for the information to schedule.  I also wanted to find my toots so far that *day*, to fill in the URLs for the final, published version of the post.

I took care of the latter, first, as you can probably guess.  Shell script [`latest.sh`](https://github.com/jcolag/tool-trunk/blob/main/latest.sh) looks at the configured user's statuses; eliminates anything not posted on that day; gets the URL, creation time, and content of them; and opens a text file listing all that.

Of particular note for people who don't necessarily care about the Mastodon API, the script opens that text file in the system's default text editor, in a couple of lines of code to look up the MIME type.  But it also makes liberal use of [`jq`](https://stedolan.github.io/jq/), to query the configuration and resulting JSON objects.

Meanwhile, I haven't yet finished work on [`schedule.rb`](https://github.com/jcolag/tool-trunk/blob/main/schedule.rb), a Ruby program to schedule the toots, but it looks promising, so far.  At this point, it *can* schedule a toot, but doesn't yet handle attached media, so I couldn't use it for this week.

I should note that I started working on scheduling by retrieving an OAuth access token, based on a client ID/secret pair.  The code seems to work, but doesn't return a token that the rest of the API will accept.  I assume this happens because I created the application for development---the "real" access token shows up on my configuration page, so I used it to replace the retrieved token---but will want to research this later, to make sure that I haven't misunderstood the process.  I wasted more time trying to debug that problem than I care to admit.

## Next

I expect to finish the **Mastodon Tool Trunk**'s scheduler before the time comes to schedule the following week's toots.  To do that, I'll need to download specified media, convert it to an acceptable format---I've seen WebP and AVIF images showing up, increasingly, which disrupts my manual workflow---probably resize it, upload it to get an ID, and then hand that ID to the toot as I schedule it.  Those mostly sound like tasks that I used to complete, fifteen years ago or so, with the Ruby library that wraps [ImageMagick](https://imagemagick.org/), so I don't expect that to pose too much difficulty, assuming that the software already understands the modern formats that Mastodon doesn't yet accept.

Time permitting, I may also create plug-ins to manage the metadata that I add to posts, such as content warnings, the header image, and so forth.  While I expect to not use that information in the blog posts, at first, and only use them for parsing, it *does* give me the option of showing a content warning banner and embedding or linking to those rare images released under a compatible license.

Once I have the scheduler code settled, and figure out the access token issue above, I'll try to put together a [tech-tip post](/blog/tag/techtips).

Also, I *believe* that I actually enjoy working with the Mastodon API, so maybe I'll try my hand at an alternate front-end, too, eventually.  For Twitter, I had a nice little setup on Tweetdeck, where I had extra columns for my own activity---to spot-check posts---and for lists of people whose posts I wanted to prioritize higher than the majority of people who I follow.  I'd love something similar with Mastodon, and I don't believe that it would take much more work to do that than it would to create a more conventional client.

* * *

**Credits**:  The header image is [Baggage of Japanese-Americans evacuated from certain West coast areas under United States Army war emergency order](https://loc.gov/pictures/resource/fsa.8c24660/) by an unknown photographer, in the public domain as the work of an employee o the United States government.
