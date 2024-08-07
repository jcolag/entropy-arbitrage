---
layout: post
title: Bicker Progress - End of February
date: 2020-02-24 07:15:55-0500
categories: programming
tags: [ruby, rails, programming, project, devjournal, bicker]
summary: Progress report on Bicker
thumbnail: /blog/assets/cute-pet-kitten-cat-mammal-close-up-997331-pxhere.com.jpg
offset: -38%
---

* Ignore for ToC
{:toc}

As [previously discussed]({% post_url 2020-01-06-bicker %}), I am currently in the process of remaking [Bicker](https://bicker.colagioia.net/) with modern technologies and architecture, hopefully along with lessons learned over the last decade about what makes a good community system.  In the interest of transparency, I'm using the blog as a kind of developer journal while I work, posting occasional updates as to where things stand.

![Cat peeking out](/blog/assets/cute-pet-kitten-cat-mammal-close-up-997331-pxhere.com.jpg "Cat peeking out")

If you want to read the other posts in the series, you can get a full list of posts under [the "bicker" tag](/blog/tag/bicker).

## Non-Bicker Updates

I don't *just* program, of course, because that's never all I do.  That should be apparent in how slow progress has been on Bicker, if nothing else.  It doesn't take (shy of) six weeks to get this little accomplished unless I'm only spending a little bit of time every day on it.  To give some quick insight into what this past week has included aside from "the usual," I'd like to point everybody to yesterday's post, a translation of [Le Mulâtre (1837)]({% post_url 2020-02-23-mulaitre %}) from the French, as a very small contribution to Black History Month.

Also, in "honor" of a completely fake awareness holiday that I'd otherwise completely ignore---National Banana Bread Day (also yesterday)---I'd like to point out a quick discovery I landed on:  Banana bread is better when it's bread than when it's cake.

That is, your typical banana bread is a [quickbread](https://en.wikipedia.org/wiki/Quick_bread), leavened with baking powder and usually containing eggs, milk, and sugar.  In other words, it's a cake disguised as bread or a gigantic, rectangular muffin.  It tastes fine (if usually too sweet), but is soft and tears/crumbles easily.

This past week, though---unrelated to Banana Bread Day, I promise---I had some leftover bananas and decided to try something different.  I made a half-batch of no-knead bread dough (1½c whole wheat flour, ½tsp salt, ¼tsp yeast, and ½c water) plus three over-ripe bananas, some crushed walnuts, and a tablespoon or so of sugar.  I then let it rise eighteen hours and baked at 425ºF for forty minutes and got a *much* better banana bread out of the deal.  It's less sweet, which I prefer (and can be changed significantly by...y'know, adding more sugar, if you prefer) and it's physically strong enough to not crumble when spreading butter or peanut butter on a slice.

Why am I mentioning this in a Bicker blog post?  Partly because it's not worth a whole blog post of its own, partly because I've noticed a significant overlap between programmers and bakers, and partly because I'm closing in on finishing the core features.  Plus, you could've hit **Page Down** at literally any time, so if you're complaining, that's really on you...

## It's Alive!

As mentioned [last time]({% post_url 2020-02-17-bicker-live %}), the top priority for this week---after *many* digressions---was to have the user interface split paragraphs and insert replies as they're created, so the majority of this update revolves around the process of making that happen.

### Adding State

The first step down the path of updating React controls is to move data access to a `state` property of the component.  This comes in two steps for each component.

 * Replace every use of `this.props.`*property* with `this.state.`*property*, so that we're now looking at the (about to be created) new `state` object.
 * In the constructor---create `constructor()` if it doesn't already exist---create a state object that contains one property for every React property.

So, the `Message` component now has a constructor that looks like the following.

```javascript
constructor (props) {
  super(props);
  this.state = {
    paragraphs: this.props.paragraphs,
  }
}
```

The other components have more complicated states, since they have more properties coming through.

Working with the component's state allows us to *update* that state, something that won't work with the properties object.  When a component's state changes, it re-renders itself to match the state.

### Main Callback

A possible small flaw in this architecture is that a reply form component doesn't have access to anything outside of itself.  It's sort of the core conceit for components, of course.  To resolve this isolation, we can pass callbacks down to the reply form that can update the appropriate targets.

The first callback is *from* the reply form.  We want to change the button's click handler to...

```javascript
onClick={(e) => submitReply(e, this, this.replyCallback)}
```

And the `submitReply()` function back on the `show` page now takes those parameters (`component` and `callback`) to send the results of the AJAX call to the reply form itself.

```javascript
callback(component, resp);
```

And `replyCallback()` will look something like this.

```javascript
replyCallback(self, data) {
  console.log(`Callback! ${data}`);
  self.setState({
    response: data,
  }, self.setStateCallback);
}
```

In theory, we should be able to bind `replyCallback()` to its instance of the `ReplyForm` component, so that we don't need to throw the component back and forth as a parameter.  I wasn't able to get that to work after a minute or two, so it'll have to be a task saved for later refactoring.

### Targeting Callbacks

The foregoing should give some insight as to how the callback scheme works, so we can now gut `replyCallback()` up there---since there isn't necessarily anything to update in the form itself, yet---and expand the scope to get what we really want out of this.

If React works properly and if it can interpret data correctly, the best place to update the state is the `Message` component.  When React components (and their data) are arranged correctly, React should ensure that the only changes that occur will be limited to the components that *need* to change.  So, we'll start there.

That isn't *very* different from what we see above.  Instead of `replyCallback()`, the `Message` component has an `updateParagraphs()` method that sets `this.state.paragraphs`, and we pass that through as a property from `Message` to `Paragraph` to `PuncButton` to `ReplyForm`.

That property, then, gets passed back to the `submitReply()` function from the reply form.

#### Data Management

Note that we're messing around with these callbacks because we only have a couple of chunks of data to throw around.  If we had much more than this, the callback chains could easily become an unmanageable mess.

In that case, we would probably want to add a state-management layer such as [Redux](https://react-redux.js.org/), an implementation of the [Flux](https://code-cartoons.com/a-cartoon-guide-to-flux-6157355ab207) model.  Rather than pushing callbacks all over the interface, Flux imagines a unified application state that is partitioned in such a way that components can (essentially) subscribe to the parts they need.

I have also previously used [Reflux](https://github.com/reflux/refluxjs) (such as in ([SlackBackup]({% post_url 2019-12-22-slack-backup %}), an older library based on the same model, which I've generally found to be faster for programmers new to React to understand, but it looks like it's no longer maintained.  So, use Reflux at your own risk.

Dollars to donuts, the callbacks are still there behind the scenes, but the abstraction programmers see is that they include different parts of the state into each component so that changes appear to automatically propagate from component to component.

I'm not planning to add Redux (or Reflux) to Bicker, since the data requirements are so small, but I did want to mention it for anybody reading along and looking for some way of handling a more complex data distribution.

### New Paragraphs

The React components now have a primitive pipeline that takes the response from posting a reply and sends it down the tree to the root component, where we can use it to modify the paragraph list in the state.

Now that we have that bit of plumbing set up, the last piece of at least the first pass on updating the paragraphs is to pass back the updated paragraph tree.

We already have code to gather the paragraphs, but it's in the *original* version of the message controller to support the `show` action, whereas replies come through the API version.  I could, obviously, copy and paste the code; I've already pulled nonsense like that for this project out of expedience, after all.  So instead, this time, I'll extract it out into the `Message` model, instead, where it (probably mostly) belongs.

In that case, we need to prefix the transplanted method names with `self.` to bind them properly.  And then a couple of the methods need an extra parameter or two, because constants like `helpers` and `current_user` don't exist in the context of a model.  (I'm not bothering with specifics, here, because it's not hard to see what I moved by just looking at [the model code](https://github.com/jcolag/Bicker/blob/master/app/models/message.rb), since that's all that's in there.)

Now, the reply handler can send back the same paragraph tree that's used to populate the React components in the first place.  Both now call `Message.getParagraphs` with our parameters.

And that gives us...well, *something*.  It provides us with the second half of the split paragraph (if we're talking about a top-level paragraph), but we don't get the children or update the first half.  It's not a complete solution, but it's a small step forward.

A heavy-handed solution to this new problem, which should probably be carefully investigated and improved later in case it's re-rendering everything, is to set the paragraph list to an empty array, *then* set it to the new array acknowledging the user's reply.

```javascript
updateParagraphs(reportError, data) {
  const paragraphs = JSON.parse(data);

  this.setState({
    paragraphs: [],
  });
  this.setState({
    paragraphs: paragraphs,
  });
}
```

As mentioned, it's entirely possible that this is forcing React to re-render the entire page instead of just updating the necessary area.  That would be a bad idea, for performance reasons.  It looks like that may not be the case, because the page stays scrolled to the right position, but I should still take a look at that to be sure either way, at some point.

### Error Reporting

In that last bit of code, there's a parameter (`reportError`) that hasn't been used.  This is another callback passed in from the `ReplyForm` component, in case something goes wrong in the controller.

What we'll do, here, is only update the paragraphs when `data` is an array.  If it isn't, we'll pass it back with `reportError()` and update the reply form's state to show an error message.

```javascript
if (Array.isArray(data)) {
  /* ... */
} else {
  reportError(data);
}
```

Some errors should be added to the `reply` method, but...we now have the core product up and running!  There are some known bugs and the code needs some pretty heavy testing to find more, but we have accounts and the ability to post and reply to messages without needing to refresh the screen.  We can Bicker! 🎉

From here, the work is cleanup and/or more advanced features.

## Catching Bugs

Now that we have the core functionality up and running, we can deal with some issues.

### Following Parents

I noticed an oversight where, when we split a paragraph in half, children that should be associated with the second half (which is to say **all** of them) don't move to the new paragraph.

That's an easy enough tweak, nothing more than inserting...

```ruby
Paragraph.select { |p|
  p.parent_id == paragraph.id
}.each { |p|
  p.parent_id = fragment.id
  p.save
}
```

...when we split the paragraph.

Without this fix, the renderer gets *very* confused, since there are now two lists pointing to the same parent with no way to determine which one is valid.

### Fixing Deletion

When I originally wrote the code to delete messages, messages were a lot simpler.  Now, they have comment threads and view-tracking information attached.  So, that needs an overhaul to recursively find all the paragraphs, delete their view states, and then delete the paragraphs in order, followed by the message.

### Main Page Warnings

Somehow, when I created the `FrontPage` component to host the introductory verbiage, I let some `className`s slip through the cracks.  Also, React complains about keeping a list (`<ul>`) inside of a paragraph (`<p>`), so the latter needs to be changed into a `<span>` tag in the one case.  Seems odd, but whatever works.

### Rubocop

[Rubocop](https://docs.rubocop.org/en/stable/) is a static code analyzer that's been around for a long while.  It's a handy tool that picks out (and, optionally, tries to fix) easily-detectable errors, especially style errors.

Calling it like so...

```sh
rubocop --disable-uncorrectable --extra-details \
        --display-style-guide --safe-auto-correct \
        --format html \
        --out rubocop.html
```

...fixes anything that has no chance of altering behavior (such as requiring frozen string literals), annotates the code to show where other changes need to be made like the following...

```ruby
# rubocop:todo Metrics/PerceivedComplexity
# rubocop:todo Metrics/MethodLength
# rubocop:todo Metrics/AbcSize
def create # rubocop:todo Metrics/CyclomaticComplexity
```

...and produces an HTML report showing each issue.

Surprisingly, running `rubocop` multiple times seems to find additional issues to auto-correct.  I guess it's a single-pass algorithm, rather than iterating to check its own work.

Cleaning those issues will is an undertaking, with around two hundred issues unfixed issues detected---almost all stylistic with only a handful of warnings (unnecessary assignments), thankfully, along with hundreds more automatically corrected---but better to take care of these now than run into problems later that could have been fixed.  It also helps bring the code style up to date with modern standards and expectations, which is nice.

Mind you, it would be nice to have the issues prioritized so that I can put off the "line is too long" offenses in auto-generated code, for example, rather than having them show up when I'm looking for real issues.  Along similar lines, I'm not sure that cleaning up `schema.rb` is useful, since it'll just get rewritten on the next pass, so I should definitely do some work on [excluding files](https://rubocop.readthedocs.io/en/latest/configuration/#includingexcluding-files).

## Next

That's it for this time around.  This coming week, I want to start cleaning out a lot of the minor details that have been left for later.  It's now later, after all, and we're in what could be the home stretch or could just be the beginning of a snowball turning into an avalanche.  Guaranteed, the Rubocop recommendations are going to take me a while to get through unless I take a full day or two specifically for it.

Also, as mentioned earlier, I think that I want to display a spurious punctuation mark at the end of any paragraph that doesn't already have any punctuation.  Doing so would make it impossible to post a comment that nobody can reply to.

I also didn't get around to the length miscount issue I discovered last week.

 > ...there's a small bug in escaping the message text.  The punctuation in the escaped text gets transformed into buttons and we also miscount the length of the strings due to the extra characters in an escaped string.  Small issue, but I'll still want to deal with it.

At least, I *think* that's what's going on.

Roles are likewise still sitting there, almost certainly ready to be applied, but never used.  And I didn't have time to look at testing, so for the third week in a row, **those** issues are still on the agenda.

Other likely targets include, though less critical as the above, would be, in no particular order...

 * Use the Markdown editor for replies, rather than just the messages.
 * Reverse the indentation of messages, so that newer replies are wider (and easier to read) than older content being replied to.
 * Possibly add the ability to easily insert emoji into messages and replies.
 * Allow the original message-writer to clone a message with replies to create a new version for people to review.
 * Improve the API layer to support apps.
 * Make user profiles public, instead of just the place to change passwords.
 * Allow users to attach images to messages and replies.
 * Add an e-mail interface that acts (as much as possible) like an old e-mail discussion list and figures out how to place and extract the replies.
 * Show where other people are typing replies in the currently-shown message, block typing in those areas, and generally prevent/resolve any conflicts if people post replies concurrently.
 * Improve the style, since the colors scheme was chosen fairly haphazardly (as a unit, I mean; the entire color scheme came out as a unit) and the background image isn't as good as it could be.
 * Divide the index of messages up by category, since the categories do, in fact, exist.
 * Document everything; this seems intuitive to me, but I'd like an actual manual, as well as reviewing the code to make sure there isn't any non-obvious code that didn't get commented.
 * Review the entire product for accessibility, including undertaking an [internationalization](https://github.com/jcolag/Bicker) effort.
 * At least consider whether there's a useful way to federate Bicker servers with [ActivityPub](https://activitypub.rocks/).
 * Generalize and centralize the punctuation list.
 * Allow for multiple types of replies, possibly using the [Occupy Movement hand signals](https://en.wikipedia.org/wiki/Occupy_movement_hand_signals) as a guide, to help users clarify how they'd like others to interpret their replies.
 * Analyze messages and replies before posting, in order to suggest when they might be interpreted as overly aggressive.
 * Have links to easily share specific comments inside and outside Bicker.
 * Attach previews to paragraphs when URLs are posted.
 * Look at scaling everything; I doubt Bicker will ever see millions of concurrent users, but I'd like to have a plan in place for how to do that, whether that's rewriting parts as microservices or something entirely different.
 * Import and export messages.
 * Turn the message pages into little [progressive web apps](https://en.wikipedia.org/wiki/Progressive_web_application), allowing users to keep working even if their connection to the server goes down for a while.
 * Make it possible/easy to embed into another web page.
 * Move these possible features to issues on [the GitHub repository](https://github.com/jcolag/Bicker) for better tracking.

Will I plow through all of these as March marches on?  Almost certainly not, because I have other projects I would like to kick off and that's a *long* list, especially given how much time per day I have to dedicate to these projects.  But as a loose roadmap, this should give some sense of what the *Bicker of the Future*<sup>&trade;</sup> might look like.

Will I get through the entire list eventually?  I'd like to get to most of them, but it also wouldn't surprise me at all if a few fell through the cracks or if other projects (and jobs) pull me away more than I'd like.  If you'd like to help out, absolutely dive in and feel free to ask for help!  But regardless, the point is that this project isn't anywhere near finished, just quickly approaching the point where it can be used casually.

Finally, I strongly suspect---foreshadowed by the banana bread discussion up top---that next week's progress report is going to be the last of the Bicker-exclusive updates...unless Bicker becomes polished enough to start marketing, of course, which I think would warrant an announcement of an official version.  Instead, I think that Monday---now that I've gotten into the pattern---will be a general journal of any projects I've been working on.

#### <i class="fas fa-gem"></i>

* * *

**Credits**:  The header image is [untitled](https://pxhere.com/en/photo/997331) by an anonymous [PxHere](https://pxhere.com/) photographer and is made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
