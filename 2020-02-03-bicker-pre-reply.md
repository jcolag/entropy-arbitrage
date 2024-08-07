---
layout: post
title: Bicker Progress - Groundhog Day (Belated)
date: 2020-02-03 06:46:55-0500
categories: programming
tags: [ruby, rails, programming, project, devjournal, bicker]
summary: Progress report on Bicker
thumbnail: /blog/assets/animal-wildlife-zoo-america-mammal-squirrel-1362487-pxhere.com.jpg
offset: -8%
---

* Ignore for ToC
{:toc}

![Groundhog](/blog/assets/animal-wildlife-zoo-america-mammal-squirrel-1362487-pxhere.com.jpg "Groundhog, interrupted")

As [previously discussed]({% post_url 2020-01-06-bicker %}), I am currently in the process of remaking [Bicker](https://bicker.colagioia.net/) with modern technologies and architecture, hopefully along with lessons learned over the last decade about what makes a good community system.  In the interest of transparency, I'm using the blog as a kind of developer journal while I work, posting occasional updates as to where things stand.

If you want to read the other posts in the series, you can get a full list of posts under [the "bicker" tag](/blog/tag/bicker).

Unfortunately, this past week has been busy, so I didn't accomplish a *whole* lot, but there's still some progress.

## Dodging HTML Entities and Tags

This time around, the highest priority for me was to not need to skip semi-colons, meaning that there's a need to extract things like `&ouml;` (as in "&ouml;") or `<strong>x</strong>` so that the formatting code doesn't turn them into `[&]ouml[;]` and so forth.

This is mildly tricky, but certainly not out of the question.

To briefly review, the **Bicker** code currently handles punctuation by inserting a carriage return before and after each one.  Since we have already separated the text into paragraphs, a carriage return is the only character that can never be part of the text.  The view then wraps the lines containing our punctuation marks in a button.

So, there are two ways to handle the tags and entities.  We can...

 * Extract them *first*, so that the carriage returns can't be inserted into them or
 * Scan through the multi-line paragraphs looking for split-up tags/entities and put them back together.

The latter seems easier, since there isn't a need to figure out what to do with the extracted entities and tags.  In that case, we need to find each entity/tag and replace them with themselves *without* the spurious carriage returns.  So, just nest `'\1'.gsub()` inside of `gsub()` and we're done, right?

Not quite.

For this, we need the long form of `gsub()` to allow the nesting.  Specifically, we need this:

```ruby
paragraph.content = paragraph.content
  .gsub(
    /(\.|,|!|\?|:|\(|\)|&|;|\/|&ndash;|&mdash;|&hellip;)/m,
    "\n".concat('\1').concat("\n")
  )
  # This next bit is the new piece...
  .gsub(/(<a [^<]*<[^>]*>|<[^>]*>|&[A-Za-z]*;|&\n*#[0-9]*\n*;)/) { |match|
    match.gsub(/\n/) { |inner| "" }
  }
  .split("\n")
```

The cartoonishly ugly regular expression includes...

 * URLs in their entirety (since they include other punctuation),
 * Other HTML tags,
 * Named HTML entities, and
 * Numeric HTML entities.

We take the matched string and replace all the carriage returns with empty strings, giving us what we need.

Interestingly, there's either a new problem or a previously-unrecognized problem:  After all the work identifying the list of entities that [RedCloth](https://redcloth.org/) generates, I now see *numerical* entities.  So, based on some additional testing, the new set of punctuation is as follows.

 * `.`
 * `,`
 * `!`
 * `?`
 * `;`
 * `:`
 * `(`
 * `)`
 * `&`
 * `/`
 * `&ndash;`
 * `&#8212;`
 * `&mdash;`
 * `&#8211;`
 * `&hellip;`
 * `&#8230;`

It looks like overkill, but those now get turned into buttons and we *should* have that settled for now.

## Pro Forma

Now that we have buttons straightened out, we can rig those buttons to show a reply form.

This is *fairly* straightforward.  We can create a simple reply form (a `textarea` and a `button`) as a React component and add the component to our `PuncButton` component.  It's not ideal, but to make sure the link doesn't take us anywhere, we can set `href='javascript:void(0)'` on the punctuation component.

We can then create a CSS class.

```css
.reply-form {
  border: 1px solid $text-color;
  border-radius: 1em;
  display: none;
  padding: 0.25em;
  text-align: center;
  width: 100%;
}
```

The important piece, here, is `display: none`, which hides the form for us.  Now, the punctuation button needs a function to call on the message page for click events, something like...

```javascript
function toggleReplyForm(e) {
  e.persist();
  var target = e.target;

  while (target.tagName.toLowerCase() !== 'a') {
    target = target.parentNode;
  }

  var id = target.attributes.name.value;
  var formId = `reply-form-${id}`;
  var form = document.getElementById(formId);

  if (form === null) {
    console.log(`can't find ${formId}`);
    return;
  }

  var state = form.style.display;

  if (state === 'block') {
    form.style.display = 'none';
    target.classList.remove('toggled-punctuation-button');
    target.classList.add('punctuation-button');
  } else {
    form.style.display = 'block';
    target.classList.remove('punctuation-button');
    target.classList.add('toggled-punctuation-button');
  }
}
```

Short version, we bubble up until we get the top-level link, then swap the styles around by both displaying/re-hiding the form and switching the appearance of the button.

The form doesn't yet *do* anything, of course.  But it should be relatively obvious to see where this is going:  Adding a reply is going to require splitting the paragraph into two pieces (before the reply and after it) and add the reply (a new paragraph) as a child of the first piece.  Then, we need to display the reply paragraphs indented underneath their parents or indent the parents with respect to the children.

Some of this will require some refactoring.  For example, the code that splits messages into separate paragraphs will need to be applied to multi-paragraph replies and the display code will need to recursively treat child messages.

## Cleanup

I've been [moving fast and breaking things](https://en.wikipedia.org/wiki/Move_fast_and_break_things_(motto)), in a push to get things running.  One of the big broken things is how the application has been handling things when users aren't logged in.  That is, I've been relying on the user being logged in, so looking for things like `current_user.login` threw a bunch of exceptions.  They were all easy to fix, but pretty embarrassing.

And in the vein of dumb moves due to testing the wrong thing, I've been testing the reply forms on messages with only one paragraph and assigning the forms IDs that didn't take multiple paragraphs into account, so all of the buttons pointed to the first paragraph.  That wasn't great, but it was easy to have an additional property filter down to where it needs to be.

## Next

That's about all I could get through, this week.  Up next should *finally* get to work on managing the replies.

I am also going to start adding tests.  Why wait so long when it could have improved things earlier?  It was deliberate, because I've worked on a lot of teams that were opposed to automated testing on the theory that it would be too much work to *suddenly* start writing tests.  So, I'd like to put that theory to the test.  Now that **Bicker** is nearing the minimum viable product state, it's a great time to see how bad creating after-the-fact tests would be.  My suspicion is that it's not going to be bad at all, but I'll make sure the journey ends up in the updates.

Finally, I didn't have the time to look at the roles, so that will need to happen at some point, as well.

#### <i class="fas fa-gem"></i>

* * *

**Credits**:  The header image is [Groundhog](https://pxhere.com/en/photo/1362487) by an anonymous PxHere photographer and is made available under the terms of the [Creative Commons Attribution-Share Alike 3.0 Unported LicenseCC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
