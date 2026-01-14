---
layout: post
title: Developer Diary, Inti Raymi
date: 2024-06-24 07:24:05-0400
categories:
tags: [programming, project, devjournal]
labels: [blog, fictopedia, library-update, lights-edge, newsletter, post-news]
summary: Progress on assorted projects
thumbnail: /blog/assets/83-Cuzco-Juin-2009.png
offset: -15%
teaser: This week's projects include the blog's newsletter, De-Post, my Post.News archive, the blog's code, The Light's Edge, an archive for Fictopedia, and some straggling library updates.
spell: Inti Raymi Fictopedia Sacsayhuamán de-post unrot∙link diclish ficts wikitext Gorm Norswedish Miniboost Wayback Juin St-Amant Unported
proofed: true
---

* Ignore for ToC
{:toc}

In the remnants of the Incan Empire, the (approximate) winter solstice---summer, for those of us in the Northern Hemisphere---such as today, marks the new year and festival celebrating [their Sun god](https://en.wikipedia.org/wiki/Inti), [Inti Raymi](https://en.wikipedia.org/wiki/Inti_Raymi).  Today, a minority of Peruvians celebrate the festival as more of a historical artifact.

![A 2009 Inti Raymi celebration at Sacsayhuamán, outside Cusco](/blog/assets/83-Cuzco-Juin-2009.png "I imagine that the Incas didn't wear quite as many baseball caps, but otherwise...")

And on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the sixth.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, then you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the ninth of July, since I never publish blog posts on Tuesdays, making that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For June, I wrote a piece about a new addition to my media server, discussed media consumption skewed (somewhat, if insufficiently) towards celebrating Pride Month, and supplied some background information on **The Light's Edge** that goes well with some of what I wrote near the end of the credits for yesterday's story.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## De-Post

{% github jcolag/depost %}

I have added the (presumed) default names of the user content to the `.gitignore` file, so that people don't accidentally commit their own data into the repository, if they choose to play with it.

I also added the current version [unrot∙link](https://unrot.link/)'s client script to the repository, under the assumption that people posting their Post.News archives do *not* want their external links to go to sites that may not have survived as long as the social media site in question did...

In the long term, it *probably* makes more sense to have the script download the latest version and pop open the URL to request adding the domain, but I'll give that some thought later.

## Post.News

{% github jcolag/post.news %}

My [Post.News archive](https://jcolag.github.io/post.news/) itself hasn't changed, but I *have* formally added a Creative Commons Attribution Share-Alike 4.0 International license---exactly like the blog---and a quick overview for the repository.

While I doubt that either will change anybody's life, but if you wanted to work with any of the (minimal) content there that you can't find anywhere else, that does allow for it.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Primarily to support the story that I posted yesterday, [*Please Come Back...*]({% post_url 2024-06-23-customer-retention %}), I spent some time fixing the fake-button plugin that I created for the blog a *long* time ago.  The buttons now have reasonable-looking styles.  But maybe more importantly, I changed the default message on the buttons, so that I don't need to worry about a rogue apostrophe blowing apart the HTML.

I also finally removed the reference to [diclish](https://github.com/Flashwalker/diclish) in my build-and-deploy-the-blog script.  While it seems like a fine utility program, something about my instance makes it highly resistant to operating through the API, so the tool doesn't work.  And if I don't use it, it makes no sense to carry a reference around in the script.

## The Light's Edge

{% codeberg jcolag/thelightsedge %}

Again, I haven't pushed out the updated site, because I need to wait on *one* piece of the puzzle to fit into place, so that I don't need to worry about people clicking links.  However, the site now has *most* of the page for "Fort Sheridan," the fictional army base where action will eventually take place, after the first chunk of story.

I should note that, if you can't wait, the CSS doesn't catch the fonts for some reason, but if you can stomach that, storing HTML pages in a Codeberg repository means that it automatically deploys to Codeberg Pages at <https://jcolag.codeberg.page/thelightsedge/>.

## Fictopedia Archive

{% codeberg jcolag/fictopedia %}

I haven't pushed anything here, yet---I only created the repository, so far---so that means that this'll become the enormous update for the week, I guess.  But years ago, a team created and maintained **Fictopedia**, "an online encyclopedia of user-created fictional information (ficts)," running from around 2009 -- 2022, though insufficient time for moderation meant that the site got mostly swallowed by spam for a few years before the owners pulled the plug on the project.

While I didn't investigate the site until after the community had fallen apart, and so didn't contribute, I enjoyed some of the concepts.  And when I saw the site having problems---the spam that I already mentioned, but also rendering problems making every page look empty to anybody who didn't try to edit the page---I spent a couple of hours writing a script that could go through the remaining viable pages to copy out the [wikitext](https://en.wikipedia.org/wiki/Help:Wikitext) source.  And then I...sat on my archive of wikitext files, because I didn't want to post the information somewhere and have the community return.

When a couple of those concepts slipped their way into the aforementioned *Please Come Back...* story, though, I realized that not only had nothing happened in a couple of years, but [their web host has suspended the account](http://www.fictopedia.net/cgi-sys/suspendedpage.cgi), making a return seem unlikely.  And since [Pandoc](https://pandoc.org/) now supports various forms of wiki markup *and* I proved (in the last section) that Codeberg Pages works fine for static HTML, it feels like the time has come to make a static archive of the **Fictopedia** pages available, translated into HTML with an index for more convenient reading.  Then, if you want to use *Gorm the Old & Sleepy Memorial Norswedish Community Center of Oakland, CA* or the **Zombie Chris** television show in a story or video game or whatever, you can read up on it and abide by the CC BY 3.0 license...

## Library Updates

I needed to bump library versions for [**Miniboost**](https://github.com/jcolag/Miniboost) and [**VS Code Rat**](https://github.com/jcolag/vscode-rat).

## Next

As mentioned, you'll probably see quite a bit of work happen on the **Fictopedia** archive.  After I get my "rescued" pages converted to HTML, I may spend some time seeing if the Internet Archive's Wayback Machine or similar archives happened to catch copies of any pages that I might have missed.  In there, I'll also finish up **The Light's Edge**'s website.

Otherwise, as you can probably guess from the previous section, library updates have started rolling in to keep me busy.  And as I mentioned, **De-Post** could use a tweak or two to keep things relatively clean.

* * *

**Credits**:  The header image is [83 - Cuzco - Juin 2009](https://commons.wikimedia.org/wiki/File:83_-_Cuzco_-_Juin_2009.jpg) by [Martin St-Amant](https://commons.wikimedia.org/wiki/User:S23678), made available under the terms of the [Creative Commons Attribution 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license.
