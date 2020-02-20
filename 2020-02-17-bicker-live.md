---
layout: post
title: Bicker Progress - First (Belated) Mensiversary
date: 2020-02-17 07:15:55-0500
categories: programming
tags: [ruby, rails, programming, project, devjournal, bicker]
summary: Progress report on Bicker
thumbnail: /blog/assets/wood-antique-paper-ink-printing-art-919542-pxhere.com.jpg
offset: -50%
---

As [previously discussed]({% post_url 2020-01-06-bicker %}), I am currently in the process of remaking [Bicker](https://bicker.colagioia.net/) with modern technologies and architecture, hopefully along with lessons learned over the last decade about what makes a good community system.  In the interest of transparency, I'm using the blog as a kind of developer journal while I work, posting occasional updates as to where things stand.

![Antique Printing Press](/blog/assets/wood-antique-paper-ink-printing-art-919542-pxhere.com.jpg "Antique Printing Press")

If you want to read the other posts in the series, you can get a full list of posts under [the "bicker" tag](/blog/tag/bicker).

It's worth noting that I created [Bicker's repository](https://github.com/jcolag/Bicker) on the 10<sup>th</sup> of January, so this past week kicked off the second month's work on the project. 🥂

## Harvesting Replies

The first thing we need, this time around, is to actually show the replies we have, in some respect.  So, to get that rolling, we need to collect the data we need.

```ruby
def getParagraphs message, parent
  result = []
  paragraphs = Paragraph.select { |p|
    p.message_id == message and p.parent_id == parent
  }.each { |p|
    user = User.select { |u| u.id == p.user_id }.first
    pp = ClientParagraph.new()
    p = format_paragraph p
    pp.id = p.id
    pp.message_id = p.message_id
    pp.parent_id = p.parent_id
    pp.next_id = p.next_id
    pp.user_id = p.user_id
    pp.content = p.content
    pp.created_at = p.created_at
    pp.updated_at = p.updated_at
    pp.avatar = helpers.avatar 100, user
    pp.children = getParagraphs message, p.id
    pp.who = user
    pp.when = helpers.time_ago_in_words(p.created_at)
    result.push pp
  }
  result
end
```

And this new `ClientParagraph` class is pretty boring.

```ruby
class ClientParagraph
  attr_accessor :avatar
  attr_accessor :beenseen
  attr_accessor :children
  attr_accessor :content
  attr_accessor :count
  attr_accessor :created_at
  attr_accessor :id
  attr_accessor :message_id
  attr_accessor :next_id
  attr_accessor :parent_id
  attr_accessor :ts
  attr_accessor :updated_at
  attr_accessor :user_id
  attr_accessor :when
  attr_accessor :who
end
```

Notice that we no longer ship off a simple list of paragraphs, but rather have a binary tree, where each "node" essentially has a potential successor and a potential first child.

This method now, of course, replaces the existing `Paragraph.select()` call in the show-message method.

### Oops!

For a long while, I was setting the extra object properties like in the following example.

```ruby
p.class.module_eval {
  attr_accessor :avatar
  attr_accessor :children
  attr_accessor :who
}
p.avatar = helpers.avatar 100, user
p.children = getParagraphs message, p.id
p.who = user
```

This *seemed* like what I wanted, despite being a fairly unpleasant hack (dynamically updating the object's class), but it caused problems when passing the objects to React:  Ruby code could see the complete object, but JavaScript could only see the database model object.  Updating the class definition is certainly a handy trick, but clearly not for use in any work that crosses any sort of application boundaries.

I tried moving the accessors directly into the model definition, but that didn't change anything.  Instead, I just created the new class for paragraph information being sent to the view, which is a lot more straightforward.

## Showing Replies (Static)

Now that we have the replies to play with, we can look at displaying them.  As mentioned [last time]({% post_url 2020-02-10-bicker-test %}), the place to start is on page-load, even though updating the page directly would be far more satisfying.

This requires fiddling around with the embedded Ruby to add in all the new details and to shift the time formatting back.  And then it requires updating the Paragraph component to recursively print any child paragraphs.

It *also* requires shifting some search code out of the (Ruby) view and into the controller where it belongs, so that it's consistent across the entire tree.  You can see that most clearly, above, in requesting the user associated with the paragraph and in formatting the creation time.

That done, we iterate through the children and create the Paragraph components for them.

```javascript
paragraphChildren(self, children, indent) {
  const result = [];

  if (
    children === null ||
    typeof children === 'undefined' ||
    children.length === 0
  ) {
    return;
  }

  children.forEach(c => result.push(<Paragraph
    avatar={c.avatar}
    beenseen={c.beenseen}
    children={c.children}
    content={c.content}
    indent={indent + 1}
    key={`child-${c.id}`}
    pid={c.id}
    pnum={c.id}
    ts={c.created_at.toString()}
    when={c.when}
    who={c.who}
  />));
  return result;
}
```

The newest idea, here, is the `indent` parameter and property.  This allows us to set a style that nests replies underneath the text that they're replies to.

![An example reply](/blog/assets/bicker-reply.png "An example reply")

Visually, it might eventually make more sense in some circumstances to organize the replies in the **opposite** direction, so that they're easier to read than the increasingly-stale original text.  But that's likely to take a fair amount of design time and this is definitely good enough for now.

### Oops, Part II

Now that I have the replies displayed on reload (before taking the screenshot above), I notice a key problem I should have caught when I wrote the code in the first place.  My code to insert replies sets the user incorrectly, so every paragraph is marked as if it was written by the same user as its parent.  I have...

```ruby
:user_id => paragraph.user_id,
```

Whereas I *needed*...

```ruby
:user_id => current_user.id,
```

So, now, replies are assigned appropriately.  It's the little things...

## Highlighting New Content

Now that a message's page might change between viewings, I want to take a quick diversion to show the paragraphs that have been added since the last viewing.

To do that, we need to track which users have seen which paragraphs.  And by *seen*, I mean *loaded*, because it's not yet worth it to figure out which components have been physically displayed to a user.  All we need for that is a table containing a `user_id` and a `paragraph_id`.

With the table, we only need to mark paragraphs that don't already exist in our `show` method, then use the value to choose the CSS class of the paragraph's outer container.

Easy enough, even if changing the thickness and color of the border is a bit ugly.  At least it gets the point across.

## Preventing Collisions

Another small thing I'd like to do before getting to the meaty project is to prevent users from replying to the same text multiple times.  After all, if the goal is to model a well-behaved conversation, you generally don't have multiple people rushing to respond to the same point.  Instead, the behavior we want is for subsequent users to respond to *each other*.

We'll do this by not separating the last punctuation mark of a split paragraph into a button.  Of course, to know if the paragraph was split, we need a flag on the paragraph table to tell us whether it has been split.

Easy enough to do this, but it's worth noting one (relatively) new feature of Ruby on Rails that makes life easier but I don't see widely discussed:  A lot of a migration can be auto-generated from the command line!

```sh
rails generate migration add_split_to_paragraph split:boolean
```

The above creates a migration containing the following, parsing the title to determine what the column specifier means.

```ruby
class AddSplitToParagraph < ActiveRecord::Migration[6.0]
  def change
    add_column :paragraphs, :split, :boolean
  end
end
```

I needed to manually add `:null => false` and `:default => false`, but that's not a bad deal at all, really.

However, making this change draws attention to the fact that a writer can currently block replies by not typing any punctuation (or carefully using marks that aren't on my list), meaning that we should probably circle back at some point to add a bogus mark at the end of paragraphs with no other punctuation.  But that's for next time.

### Obligatory Terrible Ideas

An alternative approach that probably would have worked for most typical relational database management systems would be to assume that any paragraph where `p.next_id > p.id` would be the first half of a split.  After all, most database systems assign IDs monotonically.  So, since we create the messages from last paragraph to first and the second half of a split is added after, the ID numbers in the list *should* decrease except for our split paragraphs and, of course, the final paragrpah.

However, that's very clearly awful practice, because even though it will probably work in most typical database management systems, I would be very surprised if any vendor *specified* the ID-selecting behavior.  Because it's not specified behavior, it's not at all out of the question for a particular implementation to do something strange like recycle IDs from deleted rows or even choose IDs randomly or through a hashing scheme.

So, obviously, **don't ever do this**.  The boolean column doesn't take up much space, even if that's an issue for your application, and you can rely on it being correct.  I only bring up the alternative for the sake of showing a "clever" solution to a problem that's very tempting, but much less clever than it appears.

## Cleanup

Not to sound become a broken record, but there are a lot of niggling issues with how I've managed the React components, especially.  There's too much work happening in the Rails view, when a lot of those tasks would be better split between the controller (preparing the data) and the React components (splitting the message payload into individual paragraphs).

That's just drudge-work, of course.  So, there's nothing exciting to show or talk about, but should still be done.  With any luck, improving that split will also make it easier to update the React components.

Actually, mostly.  If we move the data manipulation back into the controller where it belongs, the Rails view now gets chopped down to this.

```rails
<%= react_component 'Message', paragraphs: @paragraphs %>
```

From there, the new `Message` component needs to turn the objects into a list of rendered components.

```javascript
render () {
  const paragraphs = this.props.paragraphs.map(
    p => <Paragraph
      avatar={p.avatar}
      beenseen={p.beenseen}
      children={p.children}
      content={p.content}
      indent={p.indent}
      key={`p-${p.id}`}
      pid={p.id}
      pnum={p.pnum}
      ts={p.ts}
      when={p.when}
      who={p.who}
    />
  );
  return (
    <React.Fragment>
      {paragraphs}
    </React.Fragment>
  );
}
```

The `.map()` gives us a `Paragraph` component for every object, and then we just return the array of components.

There are some other minor changes to make to get rid of some browser warnings, fix a few small bugs, and generally clean up, but there's nothing useful to say about those changes that can't be seen in the commit.  All the problems were careless typing, basically.

And there's still a lot more refactoring to do to make this code look anything more than hacked together, naturally, but I'll leave a lot of that work for after the basic functionality is in place.  Otherwise, I'll get bogged down too much.  Make it work first, *then* make it work well.

## Next

That's it for this time.  Unfortunately, I ran out of time to get to the dynamic view updates while making interface improvements, so that's clearly going to be the primary goal for this week.  After all, it's the remaining piece of what I'd consider "core functionality" that's still not working.

Also, as mentioned earlier, I think I want to display a spurious punction mark at the end of any paragraph that doesn't have any.  Doing so would make it impossible to post a comment that nobody can reply to.

I also didn't get around to the length miscount issue I discovered last week.

 > ...there's a small bug in escaping the message text.  The punctuation in the escaped text gets transformed into buttons and we also miscount the length of the strings due to the extra characters in an escaped string.  Small issue, but I'll still want to deal with it.

I also didn't have time to look at testing, so for the third week in a row, **that's** still on the agenda.

Happy Presidents Day!

#### <i class="fas fa-gem"></i>

* * *

**Credits**:  The header image is [Antique Printing Press](https://pxhere.com/en/photo/919542) by an anonymous [PxHere](https://pxhere.com/) photographer and is made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
