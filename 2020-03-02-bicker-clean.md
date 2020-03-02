---
layout: post
title: Bicker Progress - In Like a Lion
date: 2020-03-02 06:49:20-0500
categories: programming
tags: [ruby, rails, programming, project, devjournal, bicker]
summary: Progress report on Bicker
thumbnail: /blog/assets/cute-pet-kitten-cat-mammal-close-up-997331-pxhere.com.jpg
offset: -38%
---

As [previously discussed]({% post_url 2020-01-06-bicker %}), I am currently in the process of remaking [Bicker](https://bicker.colagioia.net/) with modern technologies and architecture, hopefully along with lessons learned over the last decade about what makes a good community system.  In the interest of transparency, I'm using the blog as a kind of developer journal while I work, posting occasional updates as to where things stand.

![Cat peeking out](/blog/assets/cute-pet-kitten-cat-mammal-close-up-997331-pxhere.com.jpg "Cat peeking out")

If you want to read the other posts in the series, you can get a full list of posts under [the "bicker" tag](/blog/tag/bicker).

As a quick note, if I haven't mentioned it before, all the backslashes in code displayed below have been doubled.

## Agenda

Because I want to use this week to clean up a lot of the small issues I've been letting slide to get Bicker into working condition, there should probably be a list of those issues...

 * Fix remaining Rubocop offenses.
 * Add a spurious punctuation mark at the end of paragraphs that have no punctuation.
 * Fix length miscounts with extra characters in escaped strings.
 * Add some RSpec tests
 * Use roles, time permitting

That seems reasonable as a starting point, though there's obviously a decent chance of tests sliding *again*, since they require the most thought.  Everything else looks minor and I'm honestly surprised that---without using a bug-tracker, which I should have done---how few "I'll take care of that later" comments flew by without being followed up during the next week.

## Rubocop, Cont'd

When I left off [last time]({% post_url 2020-02-24-bicker-live %}), the big project on the agenda was running [Rubocop](https://docs.rubocop.org/en/stable/) to make sure the style is consistent with what the modern Ruby community prefers.

The auto-corrections make this relatively easy, leaving me with only about two hundred small issues to fix, most of which are warnings that the line (often a comment) is longer than eighty characters.  So, that's not hard to work out at all, just a bit tedious.

All told, after tackling a few that bothered me even as I typed them (not using predicates like `.empty?` or using camel-case names, Rubocop is complaining about...

 * Line is too long (94 instances)
 * Missing frozen string literal comment (85)
 * Use nested module/class definitions instead of compact style (4)
 * Avoid multi-line chains of blocks (2)
 * Prefer `$PROGRAM_NAME` over `$0` (1)

And it's worth mentioning that a lot of these offenses come from auto-generated code.  For one big example, I doubt I want to manually alter `db/schema.rb`, since it's going to be changed on every migration.

### Freezing Strings

While the line lengths and uncommon items should be easy (so easy, in fact, that I'm surprised that Rubocop doesn't auto-correct those), the string literals freezing needs to be applied with some small amount of care.  A *frozen string literal* is a feature in Ruby where a literal string (such as `"Hello"`, an actual data string written into the code) is a constant, constants being a feature that Ruby has historically lacked.  So, the comment it's referring to as missing...

```ruby
# frozen_string_literal: true
```

...improves performance by allocating the strings as static data, and also prevents shenanigans such as this.

```ruby
string.gsub(
        %r{(\.|,|!|\?|:|\(|\)|&|;|/|&ndash;|&mdash;|&hellip;)}m,
        "\n".concat('\1').concat("\n")
      )
```

Specifically, that last bit, `"\n".concat('\1').concat("\n")`, which is a tiny problem, since I yanked that code directly from the `Message` model.  There may be a more elegant solution, but I couldn't find a way to get the regular expression match surrounded by carriage returns.  Single-quotes don't handle carriage returns and double-quotes don't work with back-references.

The way to resolve this is to *duplicate* the rogue literal so that it becomes a variable, so the following works.

```ruby
"\n".dup.concat('\1').concat("\n")
```

I don't think I did this too often (hopefully, this is the only instance), but it still requires more thought than changing compound class names (`Api::V1::BaseController`) to a `class` (`BaseController`) inside nested `module`s, for example.

### Other

There's another batch of offenses that Rubocop was able to identify, but decided to leave `rubocop:todo` comments to point me to them instead of making the change or listing them in the report.

They don't look like they're a huge undertaking in comparison to the hundreds already cleared---there being no more than eighty-five of them---but they're a *tad* more complicated, as well.  Here's the breakdown after clearing out the easy items.

|Count|Offense|
|----:|-------|
|12|[Metrics/MethodLength](https://docs.rubocop.org/en/stable/cops_metrics/#metricsmethodlength)|
| 5|[Metrics/AbcSize](https://docs.rubocop.org/en/stable/cops_metrics/#metricsabcsize)|
| 4|[Metrics/BlockLength](https://docs.rubocop.org/en/stable/cops_metrics/#metricsblocklength)|
| 4|[Metrics/BlockNesting](https://docs.rubocop.org/en/stable/cops_metrics/#metricsblocknesting)|
| 3|[Metrics/ClassLength](https://docs.rubocop.org/en/stable/cops_metrics/#metricsclasslength)|
| 3|[Metrics/CyclomaticComplexity](https://docs.rubocop.org/en/stable/cops_metrics/#metricscyclomaticcomplexity)|
| 3|[Metrics/PerceivedComplexity](https://docs.rubocop.org/en/stable/cops_metrics/#metricsperceivedcomplexity)|

In other words, Rubocop thinks I should break thing up more.  And note that a lot of these are talking about the same code.  For example, the message `reply()` method (the API version) is flagged for ABC Size, Cyclomatic Complexity, Method Length, and Perceived Complexity; inside, there's also a Block Length offense, and outside, there's a Class Length offense.  In reality, they're somewhat complicated to untangle, but the reality is that we're mostly only talking about ten issues, total, if I'm reading this right.  Specifically, the following methods are all too long or too complex.

 * API:MessagesController:reply()
 * CategoriesController:create()
 * CategoriesController:update()
 * MessagesController:create()
 * MessagesController:update()
 * MessagesController:sort_paragraphs()
 * ApplicationHelper:flash_message()
 * Message:unroll_paragraphs()
 * Message:get_paragraphs()
 * RolifyCreateRoles:change()

There's nothing really exciting about any of this, just some tedious refactoring that I *may* push off.  After all, a lot of these are *extremely* arbitrary, particularly the line-counting rules.  And yes, I can configure Rubocop to change those rules to what I want, that just emphasizes how arbitrary "ten lines in a function should be more than enough."

Plus, it seems like there's something wrong with the counting.  For example, I have one function in a migration...

```ruby
create_table(:roles) do |t|
  t.string :name
  t.references :resource, polymorphic: true

  t.timestamps
end
```

Rubocop is convinced that this is twelve lines, too big for the ten-line limit.

So,

 * [x] Fix remaining Rubocop offenses.

...in other words.

Don't worry.  I probably won't make that a running gag.

## Emergency Punctuation

There are two obvious ways to handle this.

On the one hand, I can dig into the `Paragraph` component and, if it hasn't issued a `PuncButton` component inside of it (and it's not a split paragraph), create a bogus item with a special character such as a pilcrow (&para;) to make it clear that it's not normal punctuation.

On the other, when creating the message, I could scan paragraph objects as they're created and append punctuation for those that don't contain any punctuation in the text.

Because I don't like the idea of automatically changing user input beyond absolutely-necessary sanitization, I'd rather handle it in the view.  Doing so requires only one small change in the controller, which is to make sure it doesn't try to `.strip()` a non-existent substring when submitting the reply.

![Screenshot with fake punctuation](/blog/assets/no-punctuation-test.png "Screenshot with fake punctuation")

So, overall, that's pretty reasonable.  Users don't need to do anything special to make it work and there aren't any points where the text in the database differs significantly from what the user typed.

## Count on Me

OK, I misjudged the miscount error slightly.  The problem isn't actually that the offset is wrong, but rather that the paragraph-splitting code doesn't understand multi-character punctuation.  Therefore, we would split an ellipsis (`&hellip;`) into a period marking the final punctuation of one paragraph and then two periods to start the next paragraph; an en-dash will end the first half and start the second half of the split paragraph with a hyphen.

That's less of a bug, but still unpleasant.  Understanding the problem, however, we can fix it pretty easily by kicking the `innerText` of the punctuation button back to the controller and bumping up the offset to the end of the punctuation.

That's not trivial, but it's pretty close.  About the only problem I actually had was telling the two kinds of dashes apart, since the controller receives them as decoded entities.

## Other Bugs We Made along the Way

I noticed that, somewhere, I stopped substituting the HTML-ified paragraphs for the original Markdown text, leading to some ugly results.  Strange typo in code that I had no business changing.

But, if you have tested Bicker before and were concerned about that bug...

![No-longer-broken tables](/blog/assets/bicker-table-display.png "No-longer-broken tables")

...it's now fixed!  I swept it up into the recount commit, since it was just a one-liner.

This also nicely illustrates how the extra punctuation works for block-oriented paragraphs, like tables and headers:  It lands on the next line, just like you'd probably expect.

Not a bug, but another small change shoved into the existing bug-fix commit was replacing the reply text inputs with the Markdown editor.  If you ever need to do something like this (use SimpleMDE for multiple `textarea` widgets on the same page), the code to use is something like the following.

```javascript
componentDidMount() {
  const simplemde = new SimpleMDE({
    element: document.getElementById(this.state.text_id),
  });
}
```

React's `componentDidMount()` method is called after the component has loaded, which makes it a good time to modify the content.  Then, SimpleMDE requires the actual element to be specified, rather than (as is implied in a few places) just the ID.

It never seemed as important for the replies to be treated as first-class citizens, and in fact I hide a bunch of the buttons for replies (though all functionality is still available), but since we're only talking about another few lines of code, it seemed worth the push for consistency.

## Testing, Testing

OK, *finally*, I can look at testing.

As mentioned previously, the "right" way to handle automated testing is [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development), a software engineering style where no development happens until some tests are written to identify working code.  However, despite this being correct, we're much more likely to work on projects where the base code has already been written and there's often a sense on such a team that writing tests after the fact would be too much work.

So, I saved testing for later in the project to test that.  Obviously, this is where I'm going to regret not taking Rubocop's advice on long methods and blocks...

Regardless, I [installed]({% post_url 2020-02-10-bicker-test %}) [RSpec](https://rspec.info/) a few weeks ago, so now we can try to put it to some use.

Unfortunately, we have two unexpected (poorly documented) problems.  First, RSpec doesn't work with Rails unless the **rspec-rails** gem is installed ([apparently v4.0](https://github.com/rails/rails/issues/35417#issuecomment-475723528)---still in beta at this writing---is needed for Rails 6), so that needs to be added to the `Gemfile`...and **rails-controller-testing**, too.  Second, the existing tests are outdated, so we need new tests.

```sh
rm -f spec/controllers/*
rails generate rspec:controller application
rails generate rspec:controller categories
rails generate rspec:controller messages
rails generate rspec:controller site
```

Obviously, those are the controllers in Bicker.  If you're coming here for guidance on your application, you'll need your own list of controllers.

And we can also just get a jump on things and create the model test specifications, too.

```sh
for i in app/models/*.rb
do
  rails g rspec:model $(basename $i .rb)
done
```

That's a *little* bit too clever for its own good, but it does the job.  Now when we call `rspec`, we get a warning:

 > *<Model>* add some examples to (or delete) *`.../Bicker/spec/models/<model>_spec.rb`*

...for each model.  So now, we should be able to get to testing.  Starting with the lowest-hanging fruit, we can check out the main page coming from the site controller.

```ruby
require 'rails_helper'

RSpec.describe SiteController, type: :controller do
  describe 'GET index' do
    it "returns HTTP success" do
      get :index
      expect(response).to have_http_status(:success)
    end

    it "assigns @props" do
      props = {
        logo: '/images/Bicker-logo.svg',
        name: 'Bicker'
      }
      get :index
      expect(assigns(:props)).to eq(props)
    end

    it "renders the index template" do
      get :index
      expect(response).to render_template("index")
    end
  end
end
```

The `describe` method creates a group of examples, typically all the tests for a method; `it` methods create the individual examples.  The convention for the strings are that they should be readable in English.  So, "`it` renders the index template," in that last example.

The actual tests all do something (`get :index`, in this case, since that's all the site controller can do, though the middle `it` also creates static data) and then calls `expect().to()` to compare with a known result.  Here, we ensure that the index is successful, returns the correct (until they change) properties, and renders the `index` ERB template.

So, this will take a while, because we have a lot of features, but this is fairly straightforward.  For example, we can quickly test the `split_paragraphs()` method of the `Message` model by making sure we get the same results whether lines are separated by carriage returns, line-feeds, or both.

```ruby
describe "Paragraph splitting" do
  it "splits each line" do
    multiple_lines = "1\n2\n3\n4\n5"
    array = ["1", "2", "3", "4", "5"]
    result = Message.split_paragraphs multiple_lines
    expect(result).to eq(array)
  end

  it "splits each line by carriage returns" do
    multiple_lines = "1\r2\r3\r4\r5"
    array = ["1", "2", "3", "4", "5"]
    result = Message.split_paragraphs multiple_lines
    expect(result).to eq(array)
  end

  it "checks that letters aren't accidentally used" do
    multiple_lines = "abcdefghijklmnopqrstuvwxyz"
    result = Message.split_paragraphs multiple_lines
    expect(result).to eq([multiple_lines])
  end

  it "eliminates empty lines" do
    multiple_lines = "\n\n1\n2\n\n\n\n3\n\n\n4\n5\n\n\n\n\n"
    array = ["1", "2", "3", "4", "5"]
    result = Message.split_paragraphs multiple_lines
    expect(result).to eq(array)
  end
end
```

The third item (the alphabet check) makes sure that I haven't accidentally used any bogus escape codes.  For example, I briefly convinced myself that Ruby has a separate line-feed character like some languages do.  Normally, this would be a backslash-j (`'\j'` to represent ASCII character-10).  But that isn't the case, so adding it to the list of valid characters to use as a `split()` delimiter would cause the code to use a `j` as a delimiter.

And, as mentioned, I now see that short methods with lower complexity are going to be much easier to test, so that refactoring is higher on the agenda, again.

Other RSpec methods include `context` (nested inside `describe` and containing `it` blocks), and `before`/`after`, allowing something to happen relative to the `it` inside a `context`, like setting up the data requirements.  I don't need them early on, but they'll presumably start showing up in the testing code as I start working with complex data structures.

### Placeholders

For testing loads that need to be added, we also have the `pending` method, which takes a templated string, such as the following.

```ruby
describe "Loading paragraphs" do
  pending "add some examples to (or delete) #{__FILE__}"
end
```

RSpec identifies pending tests separate from failures, and produces a "nag" message like this.

```
3) Message Loading paragraphs add some examples to (or delete) /home/john/code/Bicker/spec/models/message_spec.rb
   # Not yet implemented
   # ./spec/models/message_spec.rb:57
```

If `pending` goes inside an `it` block---since we may have time for most of an example group but need to leave a few for another session---the test needs to throw an error, or else RSpec picks it up as a failure.  This can be done with `raise`.

### I Told Me So

That said, I believe I've validated my hypothesis that there isn't a *bad* time to add automated testing to a project, just times that aren't quite as useful.  That is, had I started Bicker as a [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development) project, I'm certain that many of the bugs I've had to stop and fix would have been caught immediately instead of weeks after the code changed.  That would have been better than adding the tests now and leading development with tests from now on, but the current state is still decent.

Leading with tests also would have kept the code more maintainable, as opposed to the tangled mess that is the formatting code.

So, I'm no longer going to accept the "we don't have time and we're too far into the project" excuse for not having automated tests on projects.  At least for Ruby, it takes almost no time to get RSpec ready (now that I've teased out the semi-secret gems) and the tests can trail development until they catch up.

### Further Investigation

The next step down the automated testing path is to dig into the important questions that led me to dismiss these test harnesses decades ago:

First, how do we validate our tests?  We can't very well write tests for our tests, because that's the [ouroboros](https://en.wikipedia.org/wiki/Ouroboros) of testing with no escape, and *that* can't be right.

Second, how can we be sure that we have sufficient testing?  I assume there's some sort of "code coverage" tools for some systems, but as an example, look back at the first test I wrote up a bunch of paragraphs.

```ruby
it "assigns @props" do
  props = {
    logo: '/images/Bicker-logo.svg',
    name: 'Bicker'
  }
  get :index
  expect(assigns(:props)).to eq(props)
end
```

That definitely covers the current output, in terms of code coverage, but it's possible (likely) that a future version of Bicker will parameterize the name and logo, rendering this test invalid except for (presumably) the default.  Presumably, there's some heuristic or tool that can help decide whether the `props` object I created is sufficient for the test or if we need some more generic solution.

Third---and almost certainly related to the first question about validating the tests---how modular should tests be?  For example, the data structure for a message's content (and replies) is large and complicated in Bicker, some of the tests are going to be long and complicated.  Just setting up the data to validate the process of reordering a set of paragraphs (with no replies) looks like this.

```ruby
@no_replies = []
last_p = nil
@line_texts.each do |l|
  paragraph = Paragraph.new
  paragraph.message_id = @message.id
  paragraph.next_id = last_p
  paragraph.user_id = @user.id
  paragraph.content = l
  paragraph.save
  cp = ClientParagraph.new Helper.new, paragraph, [], @no_replies.length
  cp.children = []
  @no_replies.push cp
  last_p = paragraph.id
end
```

That doesn't even include the code for the broader process of creating a user, category, and message to use for testing, or the stubbed-out `Helper` class that makes `ClientParagraph` happy.  And testing replies is going to need even more than that.

I'm not answering those questions *today*, of course, but they're certainly questions I'll need to answer, and will definitely report as I find the answers...assuming we don't have commenters (*hint, hint*) reporting back on the tools and techniques you all use.

And despite those questions (and the lack of testing for JavaScript/React, at the moment), creating tests is a reasonably fast process.  My tests could stand to be better-organized, but for a first run, I'm very pleased.

## (Not) On a Role

Unfortunately, since I wanted to get a good look at testing, I wasn't able to get to the roles.  I can think of some uses for roles (like an administrative user who can delete messages they didn't write), but that's probably not a critical use, yet.

## Next

Aaaand...that's all for another week.  [Bicker](https://github.com/jcolag/Bicker) now works---in a [minimum viable product](https://en.wikipedia.org/wiki/Minimum_viable_product---sense) and, while there are *plenty* of little (and big) features I would like to add, as I mentioned last time, there are also other projects I want to tackle.  Expect Monday posts to be general project updates.

So, I'll probably keep up with testing, but next Monday, expect some entirely new code with probably much smaller Bicker updates every week or so, mixed into the broader posts.

#### <i class="fas fa-gem"></i>

* * *

**Credits**:  The header image is [untitled](https://pxhere.com/en/photo/997331) by an anonymous [PxHere](https://pxhere.com/) photographer and is made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
