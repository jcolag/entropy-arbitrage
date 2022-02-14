---
layout: post
title: Developer Journal, Valentine's Day 💘
date: 2022-02-14 06:42:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/38_of_The_Quiver_of_Love.png
offset: -26%
proofed: true
---

Yep, the best holiday that I could scrounge up for today is the absurdly obvious [Valentine's Day](https://en.wikipedia.org/wiki/Valentine%27s_Day).  It turns out that there were a bunch of Christian martyrs known as Valentine, which explains the varying contradictory claims about the "real" origins of the holiday.  Regardless of which Saint Valentine is supposed to be the one we care about, today, the celebration actually appears to have been a relatively recent creation, first reported by Geoffrey Chaucer in [*Parliament of Fowls*](https://en.wikipedia.org/wiki/Parlement_of_Foules) (1382), possibly even accidentally *created* in that poem, as later readers assumed that a then-current event was actually a widespread celebration.

![A painting of two women in dresses, one leaning on the other's shoulder, both staring at a flower in one's hands](/blog/assets/38_of_The_Quiver_of_Love.png "Would that yon bloom could be but a humble unmoored far-hearing device of some intelligence, we might use it to mark our relationship status as a thing less complicated on that venerable yet secular Book of Life.")

Note that this can probably be used as evidence by both the people who believe that this is an important holiday to celebrate *and* the people who believe that this is a made-up holiday designed to move leftover winter-holiday merchandise.

On the other hand, you might prefer to [read about Kamadeva](https://theconversation.com/this-god-shoots-love-darts-but-no-its-not-cupid-176685), the parrot-riding Hindu god who shoots love-darts at people, and who at least dresses better than Cupid.

And, honestly, what better way to express love than talking about code.  Oh.  Literally any other mode of expression would be better?  Well, code-talk is what I shopped for...

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Keen-eyed readers might have noticed that, when I include a quotation in a post, I italicize the text.

 > ...Like this...

It finally annoyed me that---especially in the [**Real Life in Star Trek**](/blog/tag/startrek) posts, due to the adaptations, though not exclusively---when I cite specific text that *includes* italics, the italicized text doesn't show up.  This has "forced" me to change *italicized text* to **bolded text**, which is inaccurate and potentially misleading.

So, I finally just added a style---provisional for now, and I'll undoubtedly revise it as I refine my idea of how it should appear---to handle this properly.

```css
blockquote i, blockquote em {
  font-style: normal;
}
```

Now, there's a difference between *italicized text* and **bolded text** in excerpts, like so.

 > Now, there's a difference between *italicized text* and **bolded text** in excerpts, like so.

Pardon the repetition.

Like I said, the style is mostly just a placeholder, for now.  "Reverse-italic" isn't a sensible or particularly *readable* idea, so I'll need to experiment with it.

Oh, and I went back and updated all the quoted text so that what was meant to be italicized is no longer bolded.  Readers will no longer see ship names inappropriately bolded.

Similarly, I noticed that the occasional glyph from [Font Awesome](https://fontawesome.com/) will contort to fit into italicized text, and it looks terrible, so I gave those CSS classes the same `font-style: normal` treatment.

## Miniboost

{% github jcolag/Miniboost %}

During the week, I found an old note---probably where I was just experimenting with [Boost Note](https://boostnote.io/)'s features---that included a few references to random emoji.  It was in the format common to chat applications, with the name surrounded by colons, `like :this:`, where "this" would be the name of a hypothetical emoji.

I could have ignored this.  As I said, it's an old note, and in the rare case where I add emoji to my notes at all, I paste in the actual glyph.  However, there's something to be said for readability and consistency.  In particular, the text editing box that **Miniboost** uses different sets of glyphs for emoji:  Characters that are part of early standards and predate Unicode look like they were typed under MS-DOS, but others are photo-realistic.

Worse, if something goes wrong and there isn't an emoji font available, they'll just be invisible.  As I said, then, it's compelling to be able to say `:emoji:`, so that everything is consistent and readable.  And so, I added a library to **Miniboost** that provides the emoji glyph based on a name.

## Library Updates

This was another busy week, so just to keep active, I took some time to bump library versions on [**Generic Board Game**](https://github.com/jcolag/generic-board-game), [**Bicker**](https://github.com/jcolag/Bicker), [**RenewDB**](https://github.com/jcolag/RenewDB), and [**Ham Newsletter**](https://github.com/jcolag/ham-newsletter).

## Next

I should consider doing something similar with emoji here in the blog, as I did with **Miniboost**.  The "canonical" source files for the blog---in Markdown---should have an independent representation of any emoji.  My hope is that I don't need a full Liquid tag, though, since `{/ emoji wave /}` (syntax mangled, in case I create that tag in the future) is a lot sillier than I'd like.

* * *

**Credits**:  The header image is [38 of 'The Quiver of Love. A collection of Valentines ancient and modern. With illustrations, in colors, ... by W. Crane and Kate Greenaway](https://www.flickr.com/photos/britishlibrary/11112970976/), courtesy of the British Library, and long in the public domain.
