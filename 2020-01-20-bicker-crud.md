---
layout: post
title: Bicker Progress - MLK Day
date: 2020-01-20 07:09:24-0500
categories: programming
tags: [ruby, rails, programming, project, devjournal, bicker]
summary: Progress report on Bicker
thumbnail: /blog/assets/light-construction-repair-welding-darkness-lighting-598394-pxhere.com.jpg
offset: -28%
---

* Ignore for ToC
{:toc}

![Welding](/blog/assets/light-construction-repair-welding-darkness-lighting-598394-pxhere.com.jpg "Welding")

As [previously discussed]({% post_url 2020-01-06-bicker %}), I am currently in the process of remaking [Bicker](https://bicker.colagioia.net/) with modern technologies and architecture, hopefully along with lessons learned over the last decade about what makes a good community system.  In the interest of transparency, I'm using the blog as a kind of developer journal while I work, posting occasional updates as to where things stand.

If you want to read the other posts in the series, you can get a full list of posts under [the **bicker** tag](/blog/tag/bicker).

## Plan A

After [last week]({% post_url 2020-01-13-bicker-1 %})'s easy wins, I started out this past week thinking I would nibble at *Bicker* around the edges.  Create some quick controllers and views and dump out a working [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) foundation to build the rest of the user interface on.

{% pull ...I stupidly made a whole bunch of fields in my database models required... %}

So, I rigged up a quick global menu to allow for basic account management, based on [that same Nopio article](https://www.nopio.com/blog/authentication-authorization-rails).  That worked well, so I plunged into creating *Categories*...only to realize that I stupidly made a whole bunch of fields in my database models required (non-`null`) and failed to name some of the foreign-key reference columns.  This created a minor disaster, where references couldn't be empty, but also needed to map to a row in an imaginary table.

If you're not a database person, imagine if the government passed a law stating that every person was required to own a vehicle, but due to an offhanded joke and a transcription error, the only permissible vehicle to own was a flying carpet.  The requirement is there, but it's impossible to fill it, so the system chokes itself on red tape.

It's a shame that Rails doesn't have an easy way of validating things like this before they happen.  I understand *why*, of course:  It's the database management system's responsibility.  But since Rails, out of the box, works with [SQLite](https://sqlite.org/index.html) and *it* doesn't handle that kind of validation, it seems reasonable to want a redundant layer to catch issues along those lines.

Regardless, on top of the other issue, I also still had that vestigial `sessions` table that didn't have any part in the program.

## Rollback, into a Ditch

The obvious solution, at this point, was to create a migration to fix the problems.  And I did exactly that.  A small problem, though, is that either Rails or SQLite doesn't allow for changing reference columns if [referential integrity](https://en.wikipedia.org/wiki/Referential_integrity) checks fail.

Again, wouldn't it be great if those checks were performed during *creation* instead of waiting until someone is trying to fix the problem...?

Either way, I couldn't make the necessary changes with a migration, because the schema failed to validate properly.  Oops!

{% pull ...can get away with being fairly heavy-handed... %}

Fortunately, since nobody I know of is using *Bicker* and anybody who might be using it secretly isn't going to be able to make it do anything other than logging in and out, I can get away with being fairly heavy-handed in my solutions, rather than patiently untangling the mess I have gotten myself into.  For example, I can run...

```sh
rake db:drop
```

That wipes the entire application's database.  From there, I was able to rewrite the migrations to something more sensible, delete the migration creating the `sessions` entirely, and then bring the database back up to date.  🎇

## I Don't Know, *CanCanCan* You?

With a new database schema that *wasn't* completely broken, I created the scaffolding for categories and messages.  I also quickly added some authentication to the controllers:

```ruby
before_action :authenticate_user!, except: [:index, :show]
```

So, it's now possible for anybody to read, but a user must be logged in to do anything else.

However, I had a new problem related to permissioning, so still couldn't create any new records.

 > ActiveModel::ForbiddenAttributesError in CategoriesController#create

Some quick research turned up an obvious solution:  Tell [CanCanCan](https://rubygems.org/gems/cancancan) to allow the parameters through.  This changes the existing controller helper function from something that looks like this:

```ruby
def category_params
  params.fetch(:category, {})
end
```

...to this:

```ruby
def category_params
  params.fetch(:category, {}).permit(:name, :of, :category_id)
end
```

That solution works for the categories, but the messages...still needed some work.  In this case, there was no Rails-level error, just an application-level error insisting that **User must exist**, which should already be the case.  Some quick debugging suggested that the `:user_id` parameter was being set correctly in a `hidden_field` and that the ID matched the only user in the database.

Conveniently enough, since the default development database is just SQLite, it's not hard to query, first by calling the following to get at the prompt.

```sh
sqlite3 db/development.sqlite3
```

And then querying like any other relational database:

```sql
SELECT * FROM users;
```

There are actually two problems "hiding" in here, both my errors.

First, due to a stupid copy/paste error, the message's category was coming in as part of a different object than the rest of the message's parameters.  That's easily fixed, of course, just changing the object's name in the view.

Second, I forgot that a major implementation detail of *Bicker*'s model is that the messages don't contain any content of their own, instead farming them out into separate paragraphs.  We'll see why that's important in the next week or two.

This sort of thing is *slightly* harder to fix, but not much.  I needed to do a total of three things.

### Text to Paragraphs

The first step is to take the content of the message that's submitted and divide it up into separate paragraphs.  Because we don't want to waste effort later on down the line, we probably don't want any *empty* paragraphs, so we end up with something like this.

```ruby
def split_paragraphs msg
  pars = msg[:content].split('\n').select { |line| line.length > 0 }
end
```

It takes the parameter set as input, grabs the text, chops it on every newline, and then filters out any line that has no text in it.

### Remove the Content

We can't use the parameters to create a new message object when there are extra fields floating around, so we need to drop the `content` field, here.

Fortunately, Rails provides an `Object#except()` method, allowing me to ask for `params.except(:content)` and get the object I need, so that *Bicker* can create the message object.

### Add the Paragraphs

Now that we have a message object to work with, we can create the paragraph objects.  Because I track the paragraphs based on the *next* item, that calls for `Array#reverse_each` to iterate from last to first, creating a paragraph object linked to the message object and no parent.

Obviously, this needs to keep track of the paragraph that was created most recently (if any), so that it can be set as the *next* property of the new object.  And since paragraphs are owned by the message, we can't create the paragraphs until we have the message ready to go.

{% pull ...displaying the message requires re-assembling the chain of paragraphs into a single text. %}

And then we have the flip side of the paragraphs.  We don't want to edit them---again, the reasons will become apparent in the near future---but displaying the message requires re-assembling the chain of paragraphs into a single text.  Right now, there's a naïve way to handle this (print them in reverse order), but we're going to be rearranging them in the near future, meaning that we need to keep querying for the next paragraph until we have the complete list.  Tedious, but it works...until we need to deal with replies, which will complicate that code a bit.

And that takes care of that!  I *finally* have a basic CRUD application working that allows entry and reading of categorized messages.  🎉

## Arts and Crafts

While doing this, I also put together some new graphic design.  I re-created Bickie the mascot and the logo as an SVG, tossed together a *very* quick (and, frankly, substandard) Earthy color scheme, and chose some basic fonts:

 * [Paprika](https://fonts.google.com/specimen/Paprika) for the headings and logo
 * [Roboto](https://en.wikipedia.org/wiki/Roboto) for the main text

I also created a very simple background texture, since I find that such patterns (like the squares on this page) make a site feel less harsh when looking at it for extended periods.  In this case, I just used the [GNU Image Manipulation Program](https://www.gimp.org/) to create grayscale "plasma clouds," made the image tileable, and then dropped the opacity to something that's not easily noticed, but still detectable.

It's all subject to change, of course, and just done to keep me from staring at a stark white screen for hours on end.  But it also has the nice side-effect of looking like a real application.

## Handling Markdown

Because I still had some time to mess around, I decided to see what it would take to get [SimpleMDE](https://simplemde.com/) to work, here, for creating messages in [Markdown](https://www.markdownguide.org/) for formatting.

It turned out to be trivial.  I added the two links from the [jsDelivr](https://www.jsdelivr.com/#!simplemde) CDN and made the call to `new SimpleMDE()` on the message form.  Worked on the first shot!

Quick discovery along the way, though:  After a while away from Ruby, I somehow convinced myself that equality comparisons looked like assignments (`=`) instead of looking similar but being distinct (`==`), as in C-like languages.  So, displaying multiple messages was pretty broken until I fixed that.

Of course, just because the user can now type Markdown, that doesn't mean we display it properly.  We store the text as the same markup code we receive, so that's what would get displayed.  Instead, we need to convert it.  And for that, it looks like the state of the art in Ruby is the [Redcarpet gem](https://rubygems.org/gems/redcarpet).

It took a couple of tries, because I was (stupidly) trying to handle all the paragraphs in the view and because the documentation isn't clear on what the `renderer` parameter should be.  But after moving that logic to the controller and poking around a bit to discover the `Redcarpet::Render::HTML` renderer, I was able to add code like this.

```ruby
require 'redcarpet'

#...

def show
  mark = Redcarpet::Markdown.new(Redcarpet::Render::HTML, extensions = {
    :autolink => true,
    :disable_indented_code_blocks => true,
    :fenced_code_blocks => true,
    :footnotes => true,
    :strikethrough => true,
    :superscript => true,
    :tables => true,
    :underline => true,
  })
  #...
  p.content = mark.render p.content
  #...
end
```

This comes pretty close to what's needed, but unfortunately, Rails tries to be smart, and so "escapes" the HTML code so that it renders as code instead of formatted text.

Fortunately, though, there's a solution over in the view:

```
<%= raw paragraph.content %>
```

The `raw` function instructs the view to avoid escaping the string.  Because that's a security problem, I'll eventually want to sanitize the input, probably by stripping out any HTML tags.  That's easy enough, since Rails includes `CGI::escapeHTML()` for exactly that purpose.

Hand in hand with this comes [RubyPants](https://rubygems.org/gems/rubypants), which handles conversion of punctuation---something that's going to be *very* important---to the appropriate HTML entities.  The same gem is used by Jekyll for blogs like this, for example, which is why you'll see curly quotes and apostrophes, em-dashes, ellipses, and other "fancy" versions of punctuation, here, some in this very paragraph...

All this conversion, though, causes a few very minor conflicts.  For example, both RubyPants and the process of separating lines breaks up code blocks into units that are no longer formatted correctly.  But again, that's a problem to be solved another day.

### Before Markdown

If you want the *whole* history, here, the original version of **Bicker** supported [Textile](https://en.wikipedia.org/wiki/Textile_(markup_language)) as the markup language via [RedCloth](https://redcloth.org/).  At the time, Textile was standard for Ruby applications and, while Markdown *existed* (its specification dates to 2004), it wasn't in nearly the wide use it sees today.  Since I'm not shooting for backward-compatibility, I'm opting for the more modern lightweight markup language, here.

Most of the same issues are inevitably involved in both, however.  For example, I probably didn't care about code blocks at the time, but numbered lists are inevitably a mess when separating each line into its own paragraph.  The conversion turns each item into its own paragraph and so has its own list, which isn't ideal.

We may not be able to fix this, unfortunately.  When we start adding replies, we'll be adding the ability to split a line item into two paragraphs, anyway, making it impossible to maintain a numbered list's ordering unless we put in a lot of work past the point of diminishing returns.

But, as I've said about a couple of other things, that's a problem to deal with another day.

## Next

Now that I have a functioning CRUD application, after some cleanup, the next big step is to add the ability to insert threaded replies into messages.

The replies are critical to making *Bicker* a functional communication tool, after all, so the that should *probably* come next.  However, thinking about the number of moving parts that might be required to do this in [React](https://reactjs.org/) (my intended target), I reserve the right to change my mind and shift my attention to something that would require somewhat less thought...

#### <i class="fas fa-gem"></i>

* * *

**Credits**:  The header image is [unnamed](https://pxhere.com/en/photo/598394) by an anonymous [PxHere](https://pxhere.com/) photographer and is made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
