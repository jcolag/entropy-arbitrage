---
layout: post
title: Developer Diary, Oran Fatwa
date: 2025-12-08 07:25:05-0500
categories:
tags: [programming, project, dev-journal]
labels: [blog, css, javascript, salavi]
summary: Progress on assorted projects
thumbnail: /blog/assets/Moorish-Proselytes.png
description: This week's projects include a Codidact answer, SaLaVI, and the blog.
spell: Codidact SaLaVI Oran javascript salavi minmax amp hellip const txt innerHTML
proofed: true
---

* Ignore for ToC
{:toc}

Because the era has come up a few times, recently, I can't find a better event to mark today than the 521st anniversary of the [Oran fatwa](https://en.wikipedia.org/wiki/Oran_fatwa), an Islamic legal opinion---a fatwa, in fact---recommending less-stringent judgment against Muslims in Spain forced to convert to Christianity, so that they could "pass" as Christians without concern about betraying their faith.

![The Moorish Proselytes of Archbishop Ximenes, Granada, 1500](/blog/assets/Moorish-Proselytes.png "When I call it notable that even the Spanish thought that Columbus went too far, I mean because this sort of thing happened there...")

And on to the week's projects.

## Codidact

During the week, I provided an answer to [Creating PDF from HTML on Debian Bookworm; tools?](https://software.codidact.com/posts/295092/295106#answer-295106), which avoids---because the request wanted to avoid them for whatever reason---Pandoc and headless Chrome.

## SaLaVI

{% codeberg jcolag/salavi %}

While not yet wired up to anything, the game now has an "about" modal describing the game and showing the credits.  They have styles in place, too, for when you can show them.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

In addition to the tags-and-labels work that I announced [last week]({% post_url 2025-12-01-rosa-parks %}), this week brings three bigger features.

### The Calendar

First up, meet [the calendar](/blog/calendar/).  This does exactly what you'd expect from the name, provide a link to every post (and its tags/labels) in a monthly calendar form.  Maybe nobody else will find it useful, because the regular posts---the [developer diary](/blog/tag/dev-journal), the rare [tech tips](/blog/tag/tech-tips), the [*Star Trek* episodes](/blog/tag/star-trek), the [social media roundup](/blog/tag/link-dump), and the [Free Culture Book Club](/blog/tag/book-club)---all have tags that make navigation through them a one-step process.  However, I often find myself asking questions such as what I have done for Sunday posts over a given period, which...takes more work.

The Sunday posts don't have any consistent tag, since the topics range far and wide, at least ideally.  Therefore, I generally need to look at the entire list of posts and filter *out* tags.  Or I want to see the Free Culture projects that I talked about over a certain period.  This seemed like the quickest route to getting that information, *and* if someone else finds it useful, so much the better.

You might find a couple of things interesting about it.  First, I haven't quite finished the math and probably didn't take the most elegant approach[^23OlD7], but it largely iterates through posts like any index would.  Before printing a post title, it checks to make sure that it has the next date; if not, it adds empty days.  When the loop finds a new month or year, it fills out the remainder of the week with empty boxes, then creates a new higher-level container.

[^23OlD7]:  For example, take a look at September-to-October 2025 for where this could use more work.  Because I had no posts on the thirtieth and the first, the September calendar gives up on the twenty-ninth and October starts on the second, *but* it also crams in a 30 and 31 in the empty space of the first week of October.  It doesn't break anything that a reader might rely on, but I'll eventually want to clean that up.

Second, styling the grid turned out to require deeper research than I expected.  I started with a grid layout, but then struggled with the borders, which wouldn't show up consistently, doubling interior borders with no way to simplify them like you can do with a table.  Then, I considered looking at the problem in reverse, using the border color for the month's background, and adding a small gap between rows and columns.  I ended up with the following to make that all work.

```CSS
.cal-month {
  background-color: $text-color;
  border: 1px solid $text-color;
  display: grid;
  grid-gap: 1px;
  grid-template: "a a a a a a a";
  grid-template-columns: repeat(7, minmax(0, 1fr));
}

.cal-month .date {
  background-color: $background-color;
  overflow: hidden;
  text-align: center;
  text-overflow: ellipsis;
}
```

Jekyll uses [SASS](https://sass-lang.com/), hence the dollar-sign variables, but you can presumably figure out how to replace them with an explicit color if you don't have a preprocessor set up.

Oh, and one more little item.  Due to the limited space in the individual date-boxes, it strips off the series names, so that you can actually find a *Star Trek*, book club, or developer diary post, since you (probably) already know that they come on Thursday, Saturday, and Monday.

You can also now find a calendar icon <i class="far fa-calendar-alt"></i> in the page's heading, which links to the page.

### Tag/Label Search

Next, ever since the earliest wiki software came out, the implementation of tags and categories has irritated me.  Users *should* have the ability to use these ontology-type units to narrow down the possible items of interest.  Instead, Web 2.0 orthodoxy quickly became that you can only ever use them to explore one topic at a time.

That changes today, at least for my blog, with the [tag search](/blog/tag-search) page.

On this page, you have a list of every tag and label.  Unlike the normal [tag page](/blog/tags), when you click on one, it toggles a check-box, and displays the posts that include that item as a tag or label.  If you select more, then it will display the pages with *all* specified tags, narrowing the list.

To my chagrin, it also violates what I consider an important principle of user interface design:  It changes the layout when the user interacts with it.  As mentioned, when you click on a tag/label, it lists the pages with it.  But it also hides---and disables, for accessibility purposes---any tags/labels *not* used by those posts.  As I said a good user interface should never do that, because the user then needs to get reoriented.  However, with two hundred entries so far, it feels like it makes even less sense to hunt around for the few additional tags that might help, more expedient to remove the tags that the blog knows doesn't matter.

For a current example, consider looking at the posts that I marked [rant](/blog/tag/rant), of which I currently list eighty-one.  It might take you a while to get through all those posts, so instead, you might then click on the [technology](/blog/tag/technology) tag, which narrows the space down to five posts.  Add the [art](/blog/tag/art) tag, and the list declines to three options.  This will also become more useful as I add labels to old posts.

On the technical side, it looks a bit like the normal [search page](/blog/search), having a JSON array generated at build-time with information about each post.  Some JavaScript then searches the array when turning a check-box on or off.  This lets the page act at top speed, since all the hard work happened at build-time.  Unlike the normal search page, it ignores the post's text, which should make it more stable in the future; every few months, I discover some new character that JSON needs me to escape, leaving the search broken until I spot it, so that should never happen, here.

Oh, I forgot one irritating piece.  To make sure that the code can never break the HTML, the Liquid templates---the little sub-language that Jekyll uses to handle things such as iterating through lists of posts---carefully strip out any existing HTML and escape anything that looks like part of HTML.  Reasonable so far, but when inserting the resulting text into the list of posts, it produces nonsense like *&amp;hellip;* instead of an ellipsis.  Somehow, with all the advances in HTML, CSS, and JavaScript over the last few years, we still don't have a convenient "unescape the HTML" approach, so I needed to write the same horrible function that I needed twenty years ago...

```JavaScript
function unHTML(html) {
  const txt = document.createElement('textarea');
  txt.innerHTML = html;
  return txt.value;
}
```

It raises the question of why we should bother going through the creation of text nodes, if they don't behave in useful ways, but this will suffice for now.

Anyway, like the calendar, you can find an icon linking to the tag-search page in the heading, though the visual didn't come out nearly as well as I would like.

### View Transitions

At the moment, this only works on Chrome-like browsers.  However, during the week, somebody online linked to Mozilla's [beginner-friendly guide to view transitions](https://developer.mozilla.org/en-US/blog/view-transitions-beginner-guide/).  And since it only requires two pieces---actually only one, since it has a default animation---I implemented it directly.

Like the example code in that MDN article, I went with sliding the old page out, so my inserting it here wouldn't do anybody any good.

## Next

I can't guarantee that inspiration will strike, but I really should change the tag-search icon to something that (a) makes sense and (b) people can actually understand without looking at my original SVG file based on the two Font Awesome icons.  Likewise, I should clean up the small problems on the calendar that I mentioned.

And if neither of those, or after them, I should finish the dialog boxes on SaLaVI.

* * *

**Credits**:  The header image is the [The Moorish Proselytes of Archbishop Ximenes, Granada, 1500](https://artuk.org/discover/artworks/the-moorish-proselytes-of-archbishop-ximenes-granada-1500-58928) by Edwin Long, long in the public domain due to an expired copyright.
