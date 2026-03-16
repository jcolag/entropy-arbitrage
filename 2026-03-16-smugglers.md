---
layout: post
title: Developer Diary, Day of the Book Smugglers
date: 2026-03-16 07:41:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, novel, silver-bat, social-media]
summary: Progress on assorted projects
thumbnail: /blog/assets/Bielinis-2.png
offset: -36%
description: This week's projects include human.json, de-slopping old blog posts, and my novel's second edition.
spell: Jurgis Bielinis slopping Duelyst Kabang Quarkdown ePUB Fodongo hdXJTl CPREP Knygnešys Adolfina Petrauskienė
proofed: true
---

* Ignore for ToC
{:toc}

I realize that Lithuanian holidays feel pretty niche, but I absolutely will not pass over one that celebrates the [Lithuanian book smugglers](https://en.wikipedia.org/wiki/Lithuanian_book_smugglers), who defied the late-nineteenth century ban on Lithuanian material into the Russian Empire.  The country celebrates The Unknown Book Smuggler, and the day most specifically celebrates [Jurgis Bielinis](https://en.wikipedia.org/wiki/Jurgis_Bielinis), the "King of Book Smugglers."

![Jurgis Bielinis](/blog/assets/Bielinis-2.png "...Why don't I have a coat like that?")

And on to the week's projects.

## Social Media

I don't know if it actually qualifies as social media, but for lack of anyplace else to put it, now that they have worked out a few of the snags, I have implemented [human.json](https://codeberg.org/robida/human.json) on the website.  It might not catch on widely enough to actually help anybody, but it probably can't hurt much.

At this point, I have only manually "vouched" for a handful of websites---not through the Firefox plugin, since it requires them to participate---all Free Culture creators, and haven't found any other participating sites.

Why bother?  I know that a lot of people have searched for a "human-made" mark for websites.  All the solutions that I've seen so far feel like scams, whereas this relies on a web of trust, so that we do this together.  I can assert that I don't use AI for the site---other than what I discuss below, as it turns out---but somebody stumbling in here without knowing me probably shouldn't take my word for that, as a badge would imply.  If somebody who you trust approves, though, that "social proof" (as the advertising people call it) supports what I say.

It occurs to me that different communities could probably fork this model for other social movements.  For example, you could imagine changing the criteria (and maybe annotating the files) as something more like the old web-rings that always required too much maintenance.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-posts %}

Unrelated to the human.json thing, I have begun---only begun, don't get too excited, because this takes a lot more effort than I expected---replacing the header images where I used AI for a placeholder.  From late-2022 to mid-2023, eight posts use AI-generated images.

- [*Whatever Happened to Social Media?*]({% post_url 2022-11-13-social %}) uses AI-generated profile pictures of the "characters."  I may retain them, because the size makes them ignorable, replacing them---unless I put in a lot of effort, whether my own or somebody else's---misses the point, and as avatars, they don't have specific meaning to the story.
- [Developer Diary, World Freedom Day]({% post_url 2023-01-23-freedom %}) {% emoji check mark button %} had some sort of generic protest, because World Freedom Day has a couple of unfortunate connotations that I don't want to shove into people's retinas.  I replaced it with a cropped portrait of Sun Yat-sen, who created the "Three Principles of the People," largely also celebrated on that day.
- [Five Stages of AI Grief]({% post_url 2023-02-26-ai-grief %}) {% emoji check mark button %} used a generic image of a figure looking out at a cyberpunk-style city.  It took some work to find elements to compose, but I managed to come up with something that evokes the spirit that I wanted slightly better, though it looks a big sloppier since it involves my doing a lot of photo-editing.
- [Real Life in Star Trek, *Evolution*]({% post_url 2023-05-04-evolution %}) has an image that repeatedly clones a robot image on a generic "circuitry" background.  I actually did the (shoddy) composition work based on generated images.
- [**Death off the Cuff**]({% post_url 2023-05-20-death-cuff %}) uses a generic image of a detective-like figure walking through a hotel.
- [Archive of Our Own, part 1]({% post_url 2023-07-15-ao3-1 %}) {% emoji check mark button %} used a fantasy city with neon highlights.  I'd actually consider it the least offensive, as such things go.  However, that also made it the quickest to replace, finding a vaguely similar city in the **Duelyst** game assets.
- [Archive of Our Own, part 2]({% post_url 2023-07-22-ao3-2 %}) {% emoji check mark button %} used an unfortunate image of random ethnically coded men standing around, which *does* fit, but...ugh.  I have replaced it with a modified photograph of San Francisco, on which I gather the *Grand Theft Auto* franchise based the city in the story.
- [Announcing Kabang!]({% post_url 2023-08-13-kabang %}) uses AI for mock-up game cabinet art, probably the most difficult to replace despite its low quality, since it comes the closest to having the right look.

For the record, I used NightCafé Studio to generate the "original" images, where a quick search of my usual sources failed to provide a "real" image, except for **Kabang!**'s fake cabinet art, which bounced a few times between NightCafé and DALL-E.  I don't really regret using the tools at the time, because the alternative has often involved a similar amount of effort of picking the first image with an appropriate license that I could argue had any connection to the post, so another ill-suited image didn't seem notable.  Even seeing likely copyright problems didn't really concern me, given the small size and number of the images.

However, they do feel more sloppy in retrospect.

## Seeking Refuge

{% codeberg jcolag/silver-bat-01-seeking-refuge %}

As promised, though a bit late after I forgot, the update of my *Silver Bat* novel **Seeking Refuge** has passed out of my self-imposed "embargo" period, so you can now grab the Markdown source edited for the second edition.  That includes the [Quarkdown](https://quarkdown.com/) file defining the formatting, the build script that creates both the PDF and ePUB books, and assets such as the fonts.

As I have said, I delayed the public release as an ad hoc experiment in funding Free Culture, mostly adapting the model used by the [Fodongo](https://fodongo.ca/) comics zine for a longer-form but one-shot project, a novel instead of a short periodical.  How did it go?  The answer depends a lot on the context.

I *did* acquire one monthly supporter on [Buy Me a Coffee](https://buymeacoffee.com/jcolag).  By that standard, it does qualify as a success, in that the project generated revenue.  And given how little I peddled the book---a couple of blog posts previewing the work, and a couple of toots on Mastodon's trunk, none carefully timed---I might even call it a resounding success by this standard.  I have proven to myself that we can at least get *some* funding.

Related, I now have the financial infrastructure set up for future experiments, effort that I shouldn't need to invest in again.  Likewise, that script means that any future books will take far less time to produce than the first edition did.  I'd call those successes, too.

At the other end of the spectrum, if we look at the experiment as whether we can make the production of "Free Cultural Works" sustainable, there, it starts to look like a failure.  I could plausibly trim server costs down to where this would constitute a profit if I ignored the time involved in revisions, but the idea that somebody could live on that or even consider working less elsewhere seems silly.  And while I don't know if *I* would want the lifestyle of an artist hustling for fans with disposable income[^hdXJTl], but when I pitch making more Free Culture to people, I'd like it to serve as something more than them giving up their time and effort.

[^hdXJTl]:  Problem number one, in a case like this, Free Culture work tends to primarily attract the attention of Free Culture workers, and we can't keep passing the same money around in circles while different platforms take their transaction fees, because that does the *opposite* of supporting anybody.

In that sense, you won't find me running the same experiment again, but you'll definitely find me adjusting the ideas as I have new things to sell.  And if you'd like to spend money on this anyway, or support me arbitrarily, [the "store"](https://john.colagioia.net/store/) covers the best available options.

## Library Updates

I needed to bump library versions for [Bicker](https://codeberg.org/jcolag/Bicker) and the [CPREP background generator](https://codeberg.org/jcolag/cprep-background-generator).

## Next

I'll probably return to cleaning up the blog's updated color scheme, as I stumble across old or new flaws.  And I'll also want to get back to updating libraries for a bit, to get some of those out of the way.

* * *

**Credits**:  The header image is [Knygnešys Jurgis Bielinis](https://www.limis.lt/valuables/e/805661/44298876) by Adolfina Petrauskienė, almost certainly in the public domain due to an expired copyright.
