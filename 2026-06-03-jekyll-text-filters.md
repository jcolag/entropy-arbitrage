---
layout: post
title: Text Filters for Jekyll
date: 2026-06-03 07:39:05-0400
categories:
tags: [programming, tech-tips]
labels: [blog, jekyll]
summary: More talk about writing plugins
thumbnail: /blog/assets/Laboratory-sieves-BMK.png
offset: -26%
description: Following a mostly clear path with one wild twist.
spell: Unported Eleventy Blosxom jekyll TextFilter
proofed: true
---

* Ignore for ToC
{:toc}

This should go quick, because I mostly want to make sure that I've written down the specific thing that I guess nobody else finds worth mentioning.

![Three round, flat sieves of different densities](/blog/assets/Laboratory-sieves-BMK.png "We have the finest dirt available...")

## Background

As many of you may already know---because I end up talking about it a lot as I change things around---I use [Jekyll](https://jekyllrb.com/) to manage the blog.  Many "static site generators" exist, converting some source code to the HTML that your browser can display nicely, and Jekyll kicked off that trend.  In many ways, I picked it for stability, figuring that over a decade of development (when I started the blog) probably outweighed the sometimes-fancier features of systems such as [Eleventy](https://www.11ty.dev/), [Gatsby](https://www.gatsbyjs.com/), or [Hugo](https://gohugo.io/).  I could've gone even more mature to [Blosxom](https://blosxom.sourceforge.net/), but I used it briefly sometime around 2005, and vaguely remember not caring for how it did some things, and doubt that it has changed much.

{% github jekyll/jekyll %}

Anyway, this has nothing to do with that choice.  Rather, every once in a while, I need to extend Jekyll somewhere to get something done cleanly, and write those as plugins.  For example, in the [developer diary](/blog/tag/dev-journal) posts, I created custom tags (one type of plugin) to show the repository previews, such as the Jekyll repository itself that you'll see to the right of or above this paragraph depending on whether you read this with or without styles.  I gave a sense of how to create those inline tags in an early post on [writing the plugins]({% post_url 2021-07-21-jekyll %}) and did some work on [testing the plugins]({% post_url 2022-01-26-test-jekyll %}) a few months later.  And the blog itself includes a collection of around two dozen plugins, ranging from tiny items to insert recurring text segments that would take more work to type up to showing graphs, recipes, and user interface mock-ups.

## Filters

Getting to the point, it sometimes occurs to me that posts have recurring sections, and I avoid extracting them out into a partial file to include later, because they have some detailed changes from use to use.  For (the actual) example, consider the developer diary blurb at the end of every month about the newsletter's imminent release.  It generally comes in a couple of paragraphs, copied and (one hopes, but not often enough) edited, to say something like this.

- Mention the month's newsletter.
- Link to [sign up](https://www.buymeacoffee.com/jcolag) with instructions.
- Note the expected release date.
- Describe the automated contents, such as the two sets of links, the blog traffic and analytics.
- Describe the bespoke written content, such as my media consumption, project previews (or autopsies), and the pieces that wouldn't fit on the blog for whatever reason.
- Increasingly, link to the archive of past newsletter issues.

Some pieces, I could pass in as parameters.  Actually, I could do that for everything, but then I'd need to manually edit everything, which doesn't change much from manually copying the text from the previous month and hoping that I catch everything.  Jekyll uses [Liquid](https://shopify.github.io/liquid/) for making changes to the generated text, including the plugins such as the tags, and so a task like this *wants* a new version of Liquid's filters.

Again, to use the real example, when does the first Tuesday of the month fall?  I can't do that in "out of the box" Liquid, and it doesn't work as a tag without filling in a lot of information that becomes manual maintenance, but if I could create a filter, then I could have something like `page.date | first_tuesday`, so that I can firmly say that (*not* a real example) the November 2419 goes out on the third of December without my needing to check the calendar or even remember to update the phrasing.

And yes, it turns out that [Jekyll filters](https://jekyllrb.com/docs/plugins/filters/) take little to no effort to whip up.  I named mine `TextFilter` for clarity.

```ruby
module Jekyll
  module TextFilter
    def first_tuesday(input)
      # A discussion for another time, maybe
    end
  end
end
Liquid::Template.register_filter(Jekyll::TextFilter)
```

Now, I pretty literally (though I changed the names) call `page.date | first_tuesday`, potentially with more parameters, and I get the new information.

## Inching Along

However, I didn't write the post for that.  You can probably guess that, because I haven't provided any information so far not already found right in the documentation.

Things went horribly wrong when I tried to create a second filter.  I whipped up another plugin, restarted the build, and...nothing.  It acted like I didn't have the new filter at all.  The original still worked, but Liquid passed the input through, and even debugging statements refused to show up in the log on the console.

After a shocking number of search failures, I finally started flailing, and accidentally stumbled on two pieces of information, the actual reason for the post.

### We Love All Names Equally

First, Jekyll or Liquid doesn't bother to check for valid filter names.  This feels shocking to me, because Liquid usually gleefully crashes a Jekyll build on the slightest typo in a tag name.  But `123 | filter_that_does_not_exist` sails straight through, despite the lack of a valid filter.

In other words, I found it impossible to debug the problem, because the system doesn't seem to care about petty issues like naming.

### Big Happy Family

Finally, the real discovery.

In moving things around in frustration, I discovered that Jekyll and/or Liquid wants one and only one of each named filter module.  Best guess, which I could probably confirm if I cared more deeply about the mechanics, it probably picks the first file in alphabetical order and silently discards the others.

And after all that, I managed to get both filters running by putting both methods into the same file.

Now, I can have as many filters as I please...probably.  Honestly, it wouldn't surprise me to find out that it has some weird limit that I'll trip this time next year. {% emoji shrugging person %}

* * *

**Credits**:  I adapted the header image from [Laboratory sieves BMK](https://commons.wikimedia.org/wiki/File:Laboratory_sieves_BMK.jpg) by [BMK](https://commons.wikimedia.org/wiki/User:BMK), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/) license.
