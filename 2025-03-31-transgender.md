---
layout: post
title: Developer Diary, Transgender Day of Visibility
date: 2025-03-31 07:23:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, newsletter, notoboto, open-badges, social-media]
summary: Progress on assorted projects
thumbnail: /blog/assets/trans-visibility.png
offset: -38%
description: This week's projects include the blog's newsletter, social media changes, the blog's code, Notoboto, and a bit of Open Badges.
spell: Dia visibilidad Sez Spoutible Notoboto sfx ttk Tcl Treeview Pajaro
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the [International Transgender Day of Visibility](https://en.wikipedia.org/wiki/International_Transgender_Day_of_Visibility), somehow more relevant today than when [Rachel Crandall Crocker](https://en.wikipedia.org/wiki/Rachel_Crandall_Crocker) suggested something happier than a remembrance day in 2009.  We can only hope that we get to the point where you can all decide to live as how you see yourselves, when we can casually *see* you, without needing to worry about a government applauding violence or needing to carve out a special day.

We have [Cesar Chavez Day](https://en.wikipedia.org/wiki/Cesar_Chavez_Day), too, respect to the transgender community and the labor movement not a bad combination to close out March at all.

Oh, and I never catch holidays on Lunar calendars because I don't use one, but it looks like today (and yesterday) I should wish a bunch of people a happy [Eid al-Fitr](https://en.wikipedia.org/wiki/Eid_al-Fitr), too.

![Transgender Day of Visibility celebration in Cartagena, Colombia, 2019, featuring concentric circles of people in a stone area with LGBT+ symbols under yellow light](/blog/assets/trans-visibility.png "🏳️‍⚧️")

With that, let's look at the week's projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the fifth.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the eighth of March.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For March, I wrote a piece on changing media servers, discussed my media consumption, and provided some background information on **The Light's Edge**.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Social Media

Should I break this into two parts?  Sure, if you don't like it, write your own blog...

### Signal

I have debated announcing this for a while, but now that everybody knows the name, for those who need it, you can [contact me on Signal](https://signal.me/#eu/6x4C_EgG-Kc44nOQp2bou8C4aIIOKBDT3mfaR42f8xRGP28wHThBq5M4rQmRxvGV).  For those somehow unfamiliar after this week's news, versions of the [Signal](https://en.wikipedia.org/wiki/Signal_%28software%29) protocol or software have floated around for about fifteen years under different names, briefly part of Twitter, and currently a fully Free Software end-to-end encrypted communications app.

It does---probably unavoidably---require trusting the other person's device security.  If they lose their device or have malware running that scrapes the decrypted messages, then the encryption doesn't matter.  **Don't send private information to people who you don't trust to protect it.**  However, since Signal accepts a Google Voice number (which I've made somewhat public elsewhere on the site, if anybody doesn't want to or can't go through the link above), actually supports encryption, has a fully Free Software stack, and has support in [Beeper](https://www.beeper.com/) (which I use on desktop), it seems like a reasonable backup for people not sold on using [Matrix to contact me](https://matrix.to/#/@jcolag:matrix.org).

Why might you do that?

- You have standardized on Signal and want to chat.
- You need to leak important information, and suspect that my dozens of readers---maybe even *baker's* dozens[^1]---will get the word out.
- Somebody needs to make friends in a safe place *really* quickly for an [unscheduled vacation](https://en.wikipedia.org/wiki/Underground_Railroad) before the {% sfx ahem %} pressure gets to them, and you never know who I might know who would also like to meet somebody new[^2].
- You need an excuse to try Signal, and knowing someone there feels like a good enough excuse.
- Your casual group chat needs to [secretly plan a military strike <i class="fas fa-copyright"></i>](https://www.theatlantic.com/politics/archive/2025/03/trump-administration-accidentally-texted-me-its-war-plans/682151/?gift=j9r7avb6p-KY8zdjhsiSZ2YMi_b3Wu2jLKUeoI_W4F8) and you think that I should probably hang out[^3].

[^1]:  I actually don't know how many readers I really have, between RSS and the like.  To me, people looking at an old post---meaning that I should probably review it to make sure that it still makes sense and doesn't embarrass me---and people getting in contact matters far more than general numbers, since I won't sell ad space or anything like that.

[^2]:  Especially with modern technology, you'd generally contact somebody who contacts somebody else (possibly multiple hops, using different technologies/providers) who gets back to the person in need, to obscure the relevance.  The clearer the connection between you and your help looks, the easier the time someone will have of stopping it.  Therefore, whether you need to escape an abusive significant other or an oppressive government, you want to overcomplicate the network, rather than reach out to anybody for help directly.

[^3]:  Have I mentioned, by the way, how much I hate how much of that story---and reporting on the reporting---centers on the horrors of a journalist learning about military actions, and not the administration cheering people's deaths and wondering how we can extort European allies with it?

I don't expect people to *actually* reach out---it happens rarely enough on other platforms---and I ask you not to expect replies on Signal any faster than anywhere else.  But given the direction of "things," these days, it seemed better to model the behavior of supporting open protocols with end-to-end encryption rather than not, and provide people with a safer-than-Mastodon way of catching me.  And hey, if I end up on a Cabinet-level group chat, I'll find it far funnier than Mr. Goldberg did...

### Sez Us

This feels far more experimental.  I recently read an article about a new social media site, yet another designed to serve as sort of an anti-{% x %}.  Since I generally try to support these initiatives, and also enjoy learning from them to see *how* they want to prevent the obnoxious behavior found in the big social media sites, you can now [follow me on Sez Us](https://sez.us/user/jcolag).

Do I think that it'll thrive?  Honestly, no, I don't give it good odds.  In the past couple of years I've watched Pebble, Post.News, Cohost, and Spoutible all insist that they could create a safe space without the toxicity.  Three of them fell after about two years, because---as I've written about too many times to count---advertising largely requires conflict to drive "engagement."  You can have the toxic people, then, or you can find another route to financing.  The survivor on that list, Spoutible, serves more as a loss-leader for the owner's reputation-assessment system, so he doesn't care as much about the network's profitability.

Meanwhile, Sez Us describes their business model as follows.

> ...built on advertisers working directly with creators and investing in great content

I don't actually know what that means.  But the keyword "advertisers" tells me that the site won't do well with level-headed analyses and polite discussions.

They also have the single most intimidating "like" system that I've ever seen by a wide margin.  I don't know if I'll ever like *anything* enough to rate it across five dimensions, when I usually use those buttons for "if this site has an algorithm, it should show more like this," or "I read your message and support you posting," depending on whether I know the author...

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage %}

As promised [last time]({% post_url 2025-03-24-tuberculosis %}#next), the script to generate the link- and language-annotation styles now should work as advertized.  It had some small brittle areas, presuming that the format of the original stylesheet would conform precisely to what Simple Icons uses, when it turns out that we can't even count on Font Awesome to stick with the same format from version to version, in some areas like quotation marks.  I also apparently never committed the change that acknowledges styles without a color identified, so that has gone in.

In addition, as you've already seen in this post, Signal links now have their annotation icons.

Finally, the Codeberg has overhauled its Open Graph information at some point, warranting a massive clean-up on the plugin that the blog uses for previews.  Previously, the plugin created the preview by mocking up something similar to GitHub's preview image (as you can see over to the right) in HTML, because Codeberg only provided the user's avatar.  However, they have since updated to supply an equivalent-to-GitHub image, so now the plugin uses that, instead.

## Notoboto

{% github jcolag/Notoboto %}

The document map tree now has the same styling as the rest of the application.  The `ttk` widgets have an entirely different approach to styles, using a common style per widget-type, rather than accepting `background`, `foreground`, and similar arguments.  And we change the look of the widgets by changing that style.

```Tcl
ttk::style configure Treeview -background $bg -foreground $fg -font uifont -fill both -expand 1
ttk::style configure Treeview.Heading -background $fg -foreground $bg -font uifont
```

That "configures" the style for all `Treeview` widgets, filling the same styles that the code uses for everything else.

Weirdly, though, I can't seem to get the background of the pop-up window to cooperate, even though the search pop-up does everything correctly.  It produces bland white-space, for trees that don't have enough entries to fill the window.  It has gotten closer, at least...

## Open Badges

{% github jcolag/badging %}

In pursuit of proper "proof" or "evidence" for the badges, it looks like the code needs to present the information as [JSON-LD](https://json-ld.org/), so that it can link between pages.  Therefore, the code now uses the relevant library.

It doesn't actually affect anything, but since I don't want to lose it, I added a comment to remind myself how the IDs should look, in case the code needs to generate them.

## Next

This week, I'll probably continue with the Open Badging, finally, though I can't guarantee that something shinier won't attract my attention.

* * *

**Credits**:  The header image is [Dia de la visibilidad Trans 10](https://commons.wikimedia.org/wiki/File:Dia_de_la_visibilidad_Trans_10.png) by [Juan Pajaro Velasquez](https://commons.wikimedia.org/w/index.php?title=User:Juanrapave&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/) license.
