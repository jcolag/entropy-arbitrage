---
layout: post
title: Developer Diary, Miguel de Cervantes
date: 2025-09-29 07:09:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Cervantes-Jáuregui.png
offset: -38%
description: This week's projects include the blog's newsletter, social media (kind of) changes, my mini-server, the blog's code, Small Things, my periodic scripts, VS Code Rat, URL Code Rat, Kabang, Quotation Extractor, and an open letter to the Ruby on Rails team.
spell: stenotype Kabang Heinemeier Hansson de shiori systemd ini ExecStart Notoboto Nano KSZJId gEdit Codium Clouston
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the 478<sup>th</sup> birthday of [Miguel de Cervantes Saavedra](https://en.wikipedia.org/wiki/Miguel_de_Cervantes), author of (among other things) [**Don Quixote**](https://en.wikipedia.org/wiki/Don_Quixote).  He doesn't look a day over 450.

![Cervantes...or not, honestly, since nobody attached a name to the painting for a century](/blog/assets/Cervantes-Jáuregui.png "It seems strange that the neck ruff didn't come back in style during the twentieth century...")

And with that, on we go to the projects.

## Entropy Arbitrage Newsletter

For those of you interested in such things, I'll have the next issue of the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag) ready to go on Saturday the fourth.

If you have signed up [on Mailchimp](https://entropy-arbitrage.mailchimpsites.com/), I still don't quite trust the company, but you'll get the e-mail on Saturday.  If you have subscribed on Buy Me a Coffee---at the link in the previous paragraph, click the *Follow* button to the upper-right of the page; no money will change hands---you'll get it on Tuesday morning, the seventh of October.  Since I never publish blog posts on Tuesdays, I find that a nicer match than Saturdays.

What will you find inside?  As always, you'll find links to all the articles that I found interesting in my RSS feed or bookmarked, plus some analysis of blog traffic.  For April, I wrote a piece on shoddy job postings, discussed my media consumption, and provided some explanations of where **The Light's Edge** stands.  If you've become a member on Buy Me a Coffee, then you have already seen previews for some of that.

## Social Media

While I doubt that it'll come to anything, if only because it took a lot of resources to get the desktop application running, but you can at least occasionally find me on [Briar](https://briarproject.org/) as---no surprise, here---`jcolag`.  If I can get the [mailbox application](https://code.briarproject.org/briar/briar-mailbox) running, it might improve the chances of messages reaching me, since this runs fully peer-to-peer...

## Mini-Server, Part 12

Rather than mess with the Briar Mailbox, this week, I opted instead to do something that I've wanted for a while, install a bookmark manager.  After reviewing the options available, I settled on [Shiori](https://github.com/go-shiori/shiori/tree/master).  It took a bit of extra work to get it to work under a subfolder, as in this bit of the `systemd` description.

```ini
[Service]
Type=simple
User=shiori
Group=shiori
Environment=SHIORI_HTTP_ROOT_PATH=/shiori/
ExecStart=/home/shiori/shiori server
Restart=on-failure
```

It works, though.  I now need to work out how to authenticate to the API, which gives me some trouble.  I don't need a complete solution, though, until next month, so keep an eye on the [**Ham Newsletter**](https://codeberg.org/jcolag/ham-newsletter) repository for the script when I ultimately figure it out.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

I didn't have any significant changes to go out, this week.  Links to the [World Health Organization](https://www.who.int/) now have the United Nations link annotation icon.  And I added a readable name to my list for the Do Not Enter {% emoji no entry %} emoji.

### Less Relevant

Oh, and you'll only see this in recent [posts](https://codeberg.org/jcolag/entropy-arbitrage-posts) and it doesn't represent a code change.  But last week, as I started splitting up my post [defining Free Culture]({% post_url 2025-09-21-define-free-culture-1 %}), I realized that my approach to footnotes had gone wrong.  If I rearranged paragraphs, then the numbered footnotes became confusing out of order---the HTML version always orders them, but the Markdown needs to make sure that each footnote link leads to one and only one note---and that became worse when I started splitting up the long post.

After some thought, I decided that, except for certain places where I want a semantically meaningful "name" for the footnote, such as using abbreviations for *Star Trek* episodes in the end-of-season summary posts, the most convenient route probably leads through short but unique nonsense strings.  And recalling my recent work making sure that [**Notoboto**](https://codeberg.org/jcolag/Notoboto) notes each have unique names, I remembered that I found a variety of smaller replacements for UUIDs, including [Nano IDs](https://github.com/mrdimidium/nanoid).

The JavaScript implementation of the idea has a [collision calculator](https://zelark.github.io/nano-id-cc/), which convinced me that I could get away with six-character IDs.  At that length, you can spot them at a glance, but they don't take up much room, and they don't carry so much meaning that it seems weird to find them "out of order" (assuming that concept even makes sense).  This week, then, you should start seeing footnotes with identifiers such as `^KSZJId`, instead of a number...in the Markdown source of the posts, I mean, not anything that normal people read.

I wrote a quick program---call the API with a length and print the result---using the Rust implementation of Nano ID, then rigged up gEdit to run it as an "external tool" at a keystroke, so I can generate them without breaking up my workflow.

## Small Things

{% codeberg jcolag/small-things %}

This repository, copied over from GitHub, generally serves as my "junk pile," one-off projects that tested some core idea before I implemented it somewhere else, gave me some "scratch space" to help somebody else with a small enough problem that I only need a few lines of source code, or trying out some new-to-me technology.  A couple of items expose interests that I had---and moved on from---years ago.

Since I don't keep it well-maintained, I occasionally commit some forgotten snippet of code if I don't have anything else of note to publish.

## Periodic Scripts

{% codeberg jcolag/periodic-scripts %}

Copying this over from GitHub as well, this repository contains the majority of the scripts that I run on a regular basis, usually daily.  They don't change often, though now that I have moved to the new machine, I probably need to add a couple of items...

## VS Code Rat

{% codeberg jcolag/vscode-rat %}

Again, coming over from GitHub, this project largely served as a test of how to write an extension for Visual Studio Code.

I haven't maintained it, so it may no longer work with current versions of the application, but it would report to a server when the user opened and modified files.  If I still used VS Code (or Codium, for that matter) regularly at home, I *might* have tried to roll this into a broader note-taking solution that would allow quick cross-referencing between manual coding activity, version control activity, web history (see below), chat logs, and actual notes, building an (I hoped at the time) relatively complete picture of what I had in mind when I did a specific thing.

## URL Rat

{% codeberg jcolag/url-rat %}

Once again coming over from GitHub, this project actually preceded **VS Code Rat**, creating a browser add-on that reported every URL visited.  As hinted in the previous section, I had the vague idea of making this part of note-taking, where the sites visited at a given moment, especially while programming, can give a fairly good sense of the intent in the code, *if* you have that information handy.

## Kabang

{% codeberg jcolag/kabang %}

Another one coming over from GitHub.  To explain, a couple of years ago, after reading [**Project:  Ballad**]({% post_url 2023-07-29-project-ballad-1 %}) for the [Free Culture Book Club](/blog/tag/book-club), the arcade game described in one of the short stories felt like a tractable project.

For it, I installed the [TIC-80](https://tic80.com/) "fantasy computer" emulator and [whipped up an implementation of **Kabang**]({% post_url 2023-08-13-kabang %}).  To my knowledge, this makes the first instance of a tangible "product" created based on something portrayed in Free Culture fiction.

And yes, I sparingly used generative AI---with manual tweaks to get it where I wanted---to short-cut composing the musical theme and to simulate the arcade cabinet art, which I vaguely regret, but also makes up so little of the overall project that it doesn't bother me too much.  I should probably replace the music at some point, though, less because an AI gave me the original notes than because it sounds more "mournful" than "science fiction" to me.

## Quotation Extractor

{% codeberg jcolag/quotation-extractor %}

One last repository coming over from GitHub, if you've ever wondered where I pull the non-thematic quotations from on Mastodon---as you can find in the [social media roundup](/blog/tag/link-dump) posts---I use this code.  Generated by the code in this repository, I have JSON files with the contents of **Familiar Quotations** (9e) by John Bartlett and **The Book of Wise Sayings** by William Alexander Clouston, as pulled from Project Gutenberg, parsed.  Then the `go.js` script pulls one from a specified file, which I repeat until I find something with clear attribution and interesting enough to post.

Oh, and when I brought it over, I noticed that the repository still pointed people at my Twitter feed that I haven't used in years, as opposed to [my Mastodon feed](https://mastodon.social/@jcolag/).

At some point in the future, I'd like to add parsers for the other three books of quotations found on Project Gutenberg.  I forget why I didn't work with them, but I started this project with the goal of having a database (in the loosest sense) of a decent-sized set of quotes that definitely fall into the public domain, so finishing at least the first phase of that might help...

## DHH Open Letter

{% github Plan-Vert/open-letter %}

I almost forgot about this, even though it accounts for probably most of my time on GitHub in the last month, let alone the week.  In short, David Heinemeier Hansson (DHH), "the Rails guy," has increasingly peddled bigotry and hate, and worked to silence liberal voices at his own company under the guise of keeping things "apolitical."  You all know how that scam always goes.  His regressive ideas qualify as normal things that people say, but disagreeing with him only invites pain and strife by doing politics.

This letter asks the Rails team to distance itself from him.  As an occasional Rails developer, I agree[^tP6Ya3], because I can't rightly recommend a platform to people when I know that they won't feel safe around its community.  He can spout whatever hatred that he wants on any forum that feels like tolerating him, but I don't want it attached to a platform that got a lot of people who he hates their entries into the industry.

[^tP6Ya3]:  Also, I still regret not signing the open letter to the FSF against reinstating Richard Stallman as a member of the board, so I prioritized this one.

If you also want to sign, you need a GitHub account.  Go to the repository linked above, and click **Fork** in the upper-right area.  That will create a copy of your own to edit.  You can edit the file and add a line right in the GitHub user interface.  Then, go back to your copy's main page and click the **Contribute** button, which will give you the option to create a "pull request," a signal for the *Plan Vert* team to "pull" your changes into their version.

## Next

Expect more of the same, this week.  The repositories have gotten more obscure, but any "real" repositories---anything not a shell with a vague plan attached to it---should really make their way over to Codeberg.  I may also create a repository for the little application that I threw together to generate Nano IDs for post footnotes.

* * *

**Credits**:  The header image is [Portrait of Miguel de Cervantes y Saavedra](https://commons.wikimedia.org/wiki/File:Cervantes_J%C3%A1uregui.jpg) by (probably) Juan de Jáuregui, long in the public domain due to copyright expiration.
