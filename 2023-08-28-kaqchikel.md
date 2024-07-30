---
layout: post
title: Developer Diary, Kaqchikel Rebellion
date: 2023-08-28 07:00:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Iximche.png
teaser: This week's projects include Notoboto and the August newsletter, pretty much.
spell: Notoboto Kaqchikel Iximché cson Tcl externalizer Colocho
proofed: true
---

* Ignore for ToC
{:toc}

In keeping with this month's accidental theme of oppressed populations telling colonizers where they can stuff their power and authority---a lot of the Caribbean celebrated various Emancipation Days early in the month, too, before the month's first developer diary post---today marks the 499<sup>th</sup> anniversary of the Kaqchikel Rebellion.  As the [Spanish invaded modern-day Guatemala](https://en.wikipedia.org/wiki/Spanish_conquest_of_Guatemala), they forged a handful of alliances, particularly with the [Kaqchikel](https://en.wikipedia.org/wiki/Kaqchikel_people).

When a priest claimed that the Kaqchikel would inevitably destroy Spain, the Kaqchikel abandoned their alliance and joined the defense, which largely stalled Spanish advances for about six years.  Strip that story of its religious and maybe superstitious trappings, and consider that it only took *one person* to make an entire population rethink what side of history they wanted to stand on.

![Ruins of Iximché, the capital of the Kaqchikel at the time](/blog/assets/Iximche.png "I have images of angry Spaniards coming here, reaching that steep staircase at the center of the frame, and becoming even more irate that anybody would flout building codes like this...")

And with that, let's talk project work.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the second.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, then you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the fifth of September, because I never publish blog posts on Tuesdays, making that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For August, I revived people-search antics, wrote a piece on laptop shopping with no conclusions, discussed media consumption, and have some early-stage looks at two upcoming projects.  If you've become a member on Buy Me a Coffee, then you can already see previews for some of that.

## Notoboto

{% github jcolag/Notoboto %}

I focused the week on getting this functional.  And while it certainly has a long way to go before I'd offer to let anybody *else* use it, **Notoboto** now at least lets me work with existing notes.

Specifically, it can now read and categorize the existing files, display them correctly in the editor, and writes out the file after the user (like myself) has made changes.  Oh, and I also have the *start* of the code that will ultimately create new notes.

Included in this, you'll find what will probably remain the ugliest---and simultaneously least useful, for most people---code in the system.  The `parseCson()` function turns the text of a CSON file into a Tcl dictionary object, while `stringifyCson()` takes the dictionary and turns it into CSON text.

Yes, yes.  "CSON," I hear you cry pleadingly in distress.  Think of CSON as analogous to [JSON](https://en.wikipedia.org/wiki/JSON)---a format to "externalize" data from a (usually) JavaScript program for other programs to consume---but for CoffeeScript, because they wrote the original [Boost Note](https://boostnote.io/) using that ecosystem.  "CoffeeScript," I hear you wonder again?  You can put [CoffeeScript](https://en.wikipedia.org/wiki/CoffeeScript) on the long list of projects aimed at improving and displace JavaScript.

At some point, by the way, I had convinced myself that Microsoft had backed CoffeeScript, at least initially.  However, I can't find any evidence of this.  Most likely, I confused it with the much older [Microsoft Coffee](https://microsoft-coffee.medium.com/microsoft-coffee-25545836a7e3) prank and Microsoft's non-prank [TypeScript](https://en.wikipedia.org/wiki/TypeScript) that serves a comparable role to CoffeeScript.

At any rate, since few developers work with CoffeeScript, and therefore little software exists that writes CSON, you won't find much non-JavaScript support for CSON.  And amusingly (but also frustratingly), when I checked with AI's "usual suspects," they all insisted that I try Tcl's `cson` package.  And when I pointed out that I couldn't find one, they all claimed that they suggested it as an example of what I *could* do, if the library existed.  {% emoji exploding head %}

## Next

This week, I expect to continue on with **Notoboto**, because I have it closer to where I want it than I would have expected.  After I finish new-note creation, I need to make sure that I manage the note list properly when the user updates a note, add functionality to the remaining buttons, and work out how to only show the buttons that I care about at any given time.

And while I may have mentioned this last week, at some point, I should seriously consider whether I want to retain the CSON-formatted notes at all.  Instead of supporting a parser and externalizer that probably don't completely conform to the official specification, this *could* export the notes to a format that looks more like the Markdown source of these blog posts, where the metadata looks something like a [YAML](https://en.wikipedia.org/wiki/YAML) file, followed by the Markdown content, and named after the title of the note instead of a [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier).

* * *

**Credits**:  The header image is [Iximché](https://commons.wikimedia.org/wiki/File:Iximch%C3%A9.JPG) by [Colocho](https://commons.wikimedia.org/wiki/User:Colocho), released into the public domain by the photographer.
