---
layout: post
title: Developer Diary, Rosa Parks Day
date: 2025-12-01 06:50:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, codidact, fylakas-onomaton, mini-server, recipe, salavi]
summary: Progress on assorted projects
thumbnail: /blog/assets/Rosa-Parks-Bus.png
description: This week's projects include recipes, a Codidact answer, Salavi, the blog's code.
spell: codidact salavi fylakas onomaton Recy endcook pupusas roux grep cron Rmhermen Unported
proofed: true
---

* Ignore for ToC
{:toc}

Today, an insufficient number of states---Alabama, California, Massachusetts, Michigan, Missouri, Ohio, Oregon, Tennessee, and Texas, plus a city each in Florida, Maryland, and New Jersey---celebrate [Rosa Parks Day](https://en.wikipedia.org/wiki/Rosa_Parks_Day), commemorating the 1955 incident of civil disobedience leading to the [Montgomery bus boycott](https://en.wikipedia.org/wiki/Montgomery_bus_boycott).  As many of you probably already know, many Black people had refused to give up seats to white bus-riders before Parks to little notice, but Parks more closely resembled the "ideal victim" often unfortunately needed for these cases to get wide action, had credibility from investigating the [Recy Taylor](https://en.wikipedia.org/wiki/Recy_Taylor) case a decade earlier---the protest around which arguably launched what we think of as the era's Civil Rights Movement---with the NAACP, and had taken a class in nonviolent civil disobedience.  Way to make everybody else feel like a slacker, Rosa...

![The bus in question](/blog/assets/Rosa-Parks-Bus.png "And then we have the whole thing of conservatives trying to rewrite this with Parks as too tired to stand up...")

Globally, you might also want to draw your attention to [World AIDS Day](https://en.wikipedia.org/wiki/World_AIDS_Day), raising awareness for the continuing pandemic, along with its [Day without Art](https://en.wikipedia.org/wiki/Day_Without_Art) commemorating the artists lost to HIV/AIDS complications, though it has started to turn into a "Day with Out Art" in some circles, to celebrate the artists still with us.

And on to the week's projects.

## Recipes

As sometimes happens this time of year to all of us, I imagine, I found myself with (quick estimation) way too many [expletives deleted] potatoes.  You know the deal, you shop and see a bag of potatoes for five bucks, and oh, ten pounds?  Thanks, Costco, now your potatoes control my life.  Home fries start infiltrating breakfast.  Baked potatoes show up at awkward moments.  Anything left over gets thrown in a food storage bag for freezing, and sometimes I dice up an extra potato for freezing, because I don't need another out-of-control potato plant demanding tribute...

Anyway, during the week, I had an idea that I hadn't tried in decades[^Y7KohT]:  Part of me wanted soup.  I tried to strip down the idea to the bare minimum, in this case.

[^Y7KohT]:  In college, my dorm had stoves and ovens in the suites.  One winter, the local supermarket put twenty-pound bags of potatoes on sale for something like four dollars, which *everybody* bought thinking that nobody else knew about it, and so worked overtime to find ways to use up potatoes...

{% cook 1|Potato Soup %}
Heat @oil{1%Tbsp} in a skillet on medium-low.

Dice @onion{1/2} and add it to the hot oil.  Add @salt{1/4%tsp} and allow the onion to soften.

Dice @potato{1} finely and add it to the softened onion.  Stir to distribute.  Leave cooking for ~{5%min}, stirring occasionally.

Add @vegetable stock{1%cup}, scrape up any onion/potato that has stuck to the bottom of the pan.  Leave cooking for ~{20%min}.

Sift in @all-purpose flour{2%tsp} and stir, breaking up any lumps.  Or enjoy the dumplings, if you prefer; you won't hurt my feelings.  Finish simmering for ~{5%min}.
{% endcook %}

For reference, I have mostly standardized on red onions, so I used one here, though I imagine that any other onion would work fine, and a white or yellow onion might work better since they have less structure, if you (unlike me) want a creamier soup.  While I normally only grab Yukon gold potatoes, this time I went russet because I planned for baked potatoes with Thanksgiving dinner[^NxR1Ff].  And for the vegetable stock, I actually used (Better Than) bouillon and boiling water.

[^NxR1Ff]:  If anybody wants the full menu from Thursday, I pre-made a batch of a simplified version of the "batter" for the Budget Bytes [chipotle sweet potato burgers {% cc %}](https://www.budgetbytes.com/chipotle-sweet-potato-burgers/)---instead of baking the sweet potato, I shred it and an onion in my food processor and cook everything similarly ground up in a skillet---and then used it to make pupusas with my remaining pumpkin seed butter on the side.  Add the baked potatoes and roasted Brussels sprouts, and it made for a solid meal.

I considered frying the potatoes first and adding the onions after, but ultimately went the more traditional route.  It made two or three meal-sized servings with a large onion and relatively small potato, and I liked it enough that I expect to make it through the winter.  And like I said, I kept this to a bare minimum, so I could also probably improve it starting with a roux (instead of thickening with flour at the end) and adding carrots and celery to the initial base.  And then we have the entire world of dairy and other ingredients.  But for "four ingredients"---I gather that professionals don't count water or salt---and half an hour, I'd call that a success.

## Mini-Server, Part 16

Jellyfin has struggled running on the old Raspberry Pi, so I decided to pull out the mini-PC that I previously used to run it.  It shipped with Windows 10, so I decided to replace that with Debian 13.

For now, I haven't gone further than that, because it had started to crash on a regular basis, hence moving Jellyfin to the other servers, so I want to make sure that I don't have a hardware problem before investing more work.

## Codidact

Appropriate to the time of year, I provided an answer to [How do I store part of a raw sweet potato?](https://cooking.codidact.com/posts/295048/295049#answer-295049) based on what I've heard over the years, what I see online, and how I typically handle the problem, myself.

## Salavi

{% codeberg jcolag/salavi %}

While blog changes---see below---interrupted the game progress, I added the leader-line information to the endpoints.  Because of the code that I already had in place for the pre-built boards, that means that the game already mostly works, so you can ["play" it on Codeberg Pages](https://jcolag.codeberg.page/salavi/).

That said, something went wrong with the CSS, probably the grid direction, so it lays out to the right instead of down.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

The tags no longer break across lines at the bottom of posts, fixing a problem that has always struck me as jarring.

That got me thinking about the tags in general.  For the past years, I have tried to use them judiciously in each post, because (in my process) they double as social media tagging.  And especially for microblogs, I neither want to waste the character count nor want to look as if I want to push the announcements into as many feeds as possible.  As such, most posts don't have more tags than identifying the "series" that the post comes from.

Now, I don't know if anybody actually tries to use the tag pages to get around beyond that series-based navigation, but *I* sometimes want (for example) all the posts about (Free Culture) comics or the posts for a particular *Star Trek* show's season so that I can narrow down what I need for the season summaries.  Yes, since I have the Markdown version of the posts in front of me, I can search with `grep` or similar tools, which often happens, but the blog could make it more convenient.  Therefore, posts both need more tags...and don't.

To thread that needle, posts (starting last Thursday) now have a `labels` property in the metadata alongside the `tags`[^vdpBF0].  The latter continue to serve as both tags for the blog and tags for social media announcements.  The former only tag posts internally.  But they both work the same way, though, so that if one post uses a term as a "tag" and another uses the same term as a "label," they'll point to the same tag page, and the tag page points back to both.

[^vdpBF0]:  It took me forever to come up with the name, for some reason, even though that feels like the most direct synonym available.  I actually started thinking about doing something like this months ago, but hated every term that I came up with, because too close a synonym makes the difference unclear, but too far and they no longer feel related.  But tag/label works perfectly with a clothing analogy, where a tag hangs outside the garment to identify reasons to investigate further, whereas a label hangs inside with information for people already interested.

For example, this post has programming, project, and dev-journal as tags, like every [developer diary](/blog/tag/dev-journal) post has for almost six years.  But it also has each project that I worked on during the week, so that---once I go back through old posts to add the relevant labels---a reader could follow the evolution of each project.  The [second *Aether Galaxy*]({% post_url 2025-11-29-aether-galaxy-2 %}) post on Saturday, likewise, has the usual tags for all [Free Culture Book Club](/blog/tag/book-club) posts, but also uses a label to identify the specific project as a "space opera" "setting."

As I expand the labels through posts, that'll make it possible to find the right things.

## Codeberg Profile

{% codeberg jcolag/.profile %}

The repository now has a light adaptation of the template and script that my GitHub profile has used for a few years, with an equivalent `cron` job running.  Unless something went wrong---I expect to check after sending this out---the profile should now update overnight with recent blog posts.

## Library Updates

I needed to bump library versions for [**Fylakas Onomaton**](https://github.com/jcolag/fylakas-onomaton).

## Next

I don't know how quickly I could manage it, but I'll need to start going through old posts to specify the labels for them, when interesting.  And I *believe* that I can put together a tag/label search, parallel to the existing search but narrower and without the guesswork, that would allow for finding posts that have an intersection of tags, instead of needing to slog through every post marked **sci-fi** to find a short story in amongst all the *Star Trek* work.

Going forward for the labels, I have an open question for anybody who tries to navigate the site using the tags, especially if you read the aforementioned *Star Trek* posts:  Should those posts carry labels that relate to the prominent themes that I find in a given episode?  For example, would labeling a post **racism** make sense as a discoverability tool, or does that description only really work for the social media announcements?  Granted, I don't know how much overlap the audience has between these posts and those, so...

The labels should also propagate to the index pages, at some point, I guess.

Oh, also for the blog, I have another new feature ready to roll out, that some of you *might* have already stumbled on as I have tested it:  A calendar view of all posts.  As we approach the end of the year, I find myself wondering what I published for certain projects during certain parts of the year, and figured that somebody might prefer to explore posts that way.  But more on that next time, because it has some maybe-entertaining programming bits to it.

If I get through all that, I'll return to Salavi, since a now-functioning game should probably get some polish, like configuring the board size and (maybe) adding a specific win-state beyond reaching the end of the board.  And a traditional Snakes and Ladders game should have fewer ladders than snakes and some measure of moralizing.  And as I have probably mentioned, I would like the Owl to knock the snakes and ladders away when landing on one of the endpoints, if possible.

* * *

**Credits**:  The header image is the [Rosa Parks Bus](https://commons.wikimedia.org/wiki/File:Rosa_Parks_Bus.jpg) by [Rmhermen](https://en.wikipedia.org/wiki/User_talk:Rmhermen), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
