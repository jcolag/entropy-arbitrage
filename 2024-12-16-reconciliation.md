---
layout: post
title: Developer Diary, Day of Reconciliation
date: 2024-12-16 07:05:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, javascript]
summary: Progress on assorted projects
thumbnail: /blog/assets/Flag-of-South-Africa.svg
offset: -28%
description: This week's projects include the blog's code, all blog, all the time.
spell: querySelectorAll uMkhonto weSizwe li const scrollTop scrollY offsetTop Yaldā ParseContext
proofed: true
---

* Ignore for ToC
{:toc}

I couldn't find any holidays for my part of the world, but over in South Africa---land of [Book Dash]({% post_url 2020-09-12-bookdash %}), for those who want a quick jolt of Free Culture in their Monday---takes today to celebrate its [Day of Reconciliation](https://en.wikipedia.org/wiki/Day_of_Reconciliation) and the end of Apartheid, a reclamation of the [Day of the Vow](https://en.wikipedia.org/wiki/Day_of_the_Vow) and anniversary of the founding of the [uMkhonto weSizwe](https://en.wikipedia.org/wiki/UMkhonto_weSizwe), both days that formerly celebrated violence.

![The South African flag](/blog/assets/Flag-of-South-Africa.svg "No, I don't have snarky things to say about somebody's flag...")

Let's check out the week's projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

After a foul-up on my part, the text sizes on the index pages should look correct again.  One of the fixes last week for squeezing out the deprecated SASS code caused a problem there, but that process finally *also* completed.  Most readers shouldn't care about that, because the resulting styling should look roughly the same, but if you find yourself working with Jekyll's Minima theme and the warnings bother you, checking what I changed in those commits might help.

Continuing on the cosmetic issues, the [tag list](/blog/tags) no longer shows underlines on the links, since the page doesn't really have any text to distinguish the links *from*, the explanation for comments now sits closer to the comment box, and headings in posts should no longer look like I picked the sizes randomly.

Then, we have two bigger projects.

### Table of Contents Highlighting

It requires running a small amount of JavaScript, but those of you reading on the web should now see the entries in the table of contents highlight as you scroll sections---sort of like Wikipedia does---to (roughly) the top third of the browser window.  Ignoring declaring the variables, it comes in two parts, each hanging off events.

```JavaScript
window.addEventListener('load', (e) => {
  anchors = document.querySelectorAll('h1, h2, h3, h4, h5, h6');
  links = document.querySelectorAll('#markdown-toc li > a');
});
```

On loading the page, we initialize the aforementioned variables.  The `querySelectorAll()` method gives us a list of all elements on the page that fit the listed queries.  Anchors look for `h1` and similar elements on the page, all headings.  Links---terrible name, in retrospect---look for links in the bulleted list of the table of contents.  Actually, I should probably rename them both, anchors to headings and links to ToC entries.

```JavaScript
window.addEventListener('scroll', (event) => {
  if (anchors && links) {
    const scrollTop = window.scrollY;

    // Clear all highlights in the table of contents.
    links.forEach((link, index) => {
      link.classList.remove("toc-active");
    });

    // Moving backwards, highlight the first match and break.
    for (let i = links.length; i >= 0; i--) {
      if (scrollTop > anchors[i].offsetTop - window.screen.height / 3 && i > 0) {
        links[i - 1].classList.add('toc-active');
        break;
      }
    }
  }
});
```

Anyway, now we have the more irritating part, the part that actually requires JavaScript.  If we haven't initialized `anchors` or `links` yet, we don't care.  But otherwise, we clear any "annotations" from the table of contents, then find the last header above the desired position, the top third of the screen, in my vision[^1].  If we find a match, then annotate (using a CSS class) the equivalent entry in the table of contents.

[^1]:  Why a third of the page?  Visually, that looks the most like "reading the section" to me.

However, we need to do a *bit* more than that, because the page for each post has more headings than entries in the table of contents.  The table of contents, you see, comes from the conversion from Markdown to HTML.  On the other hand, the post's title and the blog's title way down in the page footer come from the page templates that Jekyll inserts the converted HTML into.  As a result, you'll notice that we iterate through `anchors` based on the length of `links`, and then actually set `links[i - 1]`, because the two lists don't quite match up.

This would make me much happier without JavaScript, but it does work.  As you scroll, the table of contents that floats over to the left will show the "current" entry by bolding the name and surrounding it with finger-pointing emoji {% emoji backhand index pointing right %} **like this** {% emoji backhand index pointing left %}.

### Improved Content Warnings

In yesterday's [post on fictional villains]({% post_url 2024-12-15-devils-detail %}), I noticed that the text of the content warnings didn't get converted to HTML, which would make sense.  As much as I believe that textual elements like content warnings should have as little styling applied as possible, sometimes it needs italics (for example) to make sense---in the future, a warning might refer to a book or something, and would need to bold the title---and conservative styling shouldn't mean abandoning smart-quotes and appropriate dashes.

As it turns out, I've done this before, and even documented it on the blog a couple of times, starting with the [2021 Yaldā Eve developer diary]({% post_url 2021-12-20-yalda %}), so I won't go into it the specific changes here.  However, I gave this its own section to mention two issues that led to yesterday's post getting delayed by a couple of hours.

{% cw Don't read this as a **real** warning, but rather an *example* to show that the "formatting and styling" now work... %}

First, as you might know from my [post on testing Jekyll plugins]({% post_url 2022-01-26-test-jekyll %}), I try to build little "test harnesses" for the trickier plugins.  I do this, because Jekyll itself only ever loads the plugin code on startup, meaning that testing a change otherwise requires stopping and restarting my local server, which delays learning whether the update worked.  The test code lets me run a quick check from the command line with some input, inspect the output HTML visually, and move on with my life.

To my extreme frustration, my tests failed on a fundamental level, crashing on the plugin's attempt to retrieve site information.  That made no sense, since I have several other plugins that run exactly the same code, which have never given me any trouble, and I couldn't find *any* discussion of the error message online, though the state of search engines these days makes that meaningless.  But then, I hit on a key piece of evidence:  I didn't have test harness code for any of the plugins that do this Markdown-to-HTML conversion.

While I wish that I could give you some insight that would help you test similar plugins---presumably, I need a different context object to pass in than `Liquid::ParseContext`---but I can tell you that.  Instead, I can tell you that ignoring the test scaffolding and restarting the server *did* show me that the code worked all along.

That led to the second problem, though, empty content warnings.  This turned out to have a more fundamental reason that I should have already realized.  The content warning blocks, in previous versions, used paragraph elements (`<p>...</p>`) to contain the warning information.  However, when this code converts a string to Markdown, it wraps the text in a paragraph element of its own.  An HTML paragraph should only contain [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Content_categories#phrasing_content), though, of which paragraphs themselves don't qualify, so the inner paragraph vanishes.

To fix this, the warnings now come as `div` elements, which can contain "flow content" (same link, different section), and a paragraph definitely qualifies, there.

## Next

I have some cleanup to do from this week's changes to the blog, and then (I hope) a new feature soon that might make casual readers happy.  Or maybe I'll realize that the feature only makes sense for the part of the audience that'll never see it.  Who knows...?

* * *

**Credits**:  The header image is [Protest against child labor in a labor parade](https://www.loc.gov/pictures/collection/ggbain/item/97519062/) by a Bain News Service photographer, long in the public domain due to an expired copyright.
