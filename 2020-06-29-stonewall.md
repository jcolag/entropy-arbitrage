---
layout: post
title: Developer Journal, Stonewall Uprising (Belated)
date: 2020-06-29 06:46:12-0400
categories:
tags: [programming, project, devjournal, uxuyu]
labels: [blog, newsletter, vscode]
summary: Progress on assorted projects
thumbnail: /blog/assets/Stonewall_Inn_1969.jpg
offset: -85%
---

* Ignore for ToC
{:toc}

Yesterday, of course, was the anniversary of the [Stonewall uprising](https://en.wikipedia.org/wiki/Stonewall_riots).  Sometimes, it almost seems like American history should be built around protests, uprisings, and riots, with the conditions leading up to them more instructive as to where we are and how we got here than the relative non-stories of the [War of 1812](https://en.wikipedia.org/wiki/War_of_1812) or the [Battle of San Juan Hill](https://en.wikipedia.org/wiki/Battle_of_San_Juan_Hill).

![Stonewall Inn, 1969](/blog/assets/Stonewall_Inn_1969.jpg "Stonewall Inn, 1969")

## Entropy Arbitrage

I tweaked the code that generates the list of posts updating a given post.  I also added a panel to encourage visitors to sign up for the mailing list.  Speaking of which...

### Mailing List

This is getting closer.  The first edition *may* need to be sent out manually (though I still have two days to work out the remaining kinks), but it looks increasingly like I'll be able to create a newsletter programmatically.  That means that I should be able to include anything I saved in my RSS feed, bookmarks, posts from this blog, and maybe content from other data sources.  That's good, because I absolutely do *not* want to manually scrape through those sources every month to assemble a template.

You'll also note a semi-functioning sign-up form over to the right, if you're not reading this from the RSS feed or the repository.  I call it "semi-functioning," because it doesn't work when browser-tracking is blocked.  So, it may need to be rewritten using Mailchimp's API.

Either way, be sure to sign up, especially if you want a monthly round-up of the posts here, what I've been reading, and the occasional project preview.

## VS Code Rat

Similar to last week's [**URL Rat**](https://github.com/jcolag/url-rat), [**VS Code Rat**](https://github.com/jcolag/vscode-rat) is my new experimental project to learn how Visual Studio Code extensions work.  Using the same idea, it will send the path name of every viewed file to a remote URL.

Again, it's a terrible idea as a standalone project, but I have some ideas of what the information from those two extensions might suggest.  Either way, it doesn't do anything, yet, but expect a post about writing an extension for Visual Studio Code this Wednesday or next.

## Uxuyu

Work has begun on the thread that will scrape the different user registries I've found---six, so far.  Right now, they're hard-coded, but should probably be stored in some configuration file for easier updates.  They don't make much sense in the user configuration, though, so I'll need to investigate that.

In any case, using regular expressions, it's easy enough to parse the two (or three, depending on how you count) types of registries, making it easy to bundle the retrieved users up to pass to the account worker thread.  And I already have the infrastructure set up to update the database with a set of new users, making that similarly easy.

Mixed in there, I also needed to squash a bunch of bugs.  Some, I'm not even sure where they came from.

## Next

It looks like **Uxuyu** might be close to an official release, once I work out the kinks in using the registries.

I also want to add handle-lookups, though, so that---on the occasions I send a message to someone specific, something I need to work on doing more---I don't need to remember the fussy "`@<handle url>`" syntax *and* look up the user's URL.  Ideally, if someone types "`@jcolag`," they shouldn't need to know or even see my feed's URL at all.

It might also make sense to add debugging commands to the entry field, so that it can be possible to auto-update registries and refresh all feeds, and maybe change some configuration options.  That might also solve the follow/unfollow problem.

* * *

**Credits**:  The header image is---probably obviously---the [Stonewall Inn, 1969](https://commons.wikimedia.org/wiki/File:Stonewall_Inn_1969.jpg) by Diana Davies with the New York Public Library, made available under the terms of the [Creative Commons Attribution-Share Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
