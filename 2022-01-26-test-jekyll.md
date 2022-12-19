---
layout: post
title: Testing Jekyll Plugins — Small Technology Notes
date: 2022-01-26 06:51:05-0500
categories:
tags: [techtips, jekyll, blog]
summary: Ruby code should be Ruby code
thumbnail: /blog/assets/work-technology-vintage-wheel-retro-clock-606288-pxhere.com.jpg
update: [
  2021-07-21-jekyll.md,
  2022-01-24-education.md
]
proofed: true
---

Once in a while, I have a small problem with some regularity that has an easy solution.  Traditionally, I write a note to myself, somewhere, and then need to hunt down the note when I need it next time.  Since that’s inefficient, whenever I have one of these solutions, I now use them as short blog posts.

![Gears](/blog/assets/work-technology-vintage-wheel-retro-clock-606288-pxhere.com.jpg "Fiddly technical things ahead")

This week, we have *The Case of Testing a Jekyll Plugin without Restarting the Blog Every Two Minutes*, starring...oh, let's say [Hercule Poirot](https://en.wikipedia.org/wiki/Hercule_Poirot), since he has some early appearances in the public domain.  If you want a drier version of this post that just gets to the point, I worked out [most of the details](https://stackoverflow.com/q/70779122/3438854) on Stack Overflow <i class="fab fa-stack-overflow"></i>.

More to the point, though, as you might know from following the [developer journal](/blog/tag/devjournal) posts, **Entropy Arbitrage** now uses an inline tag that pulls metadata from a specified GitHub repository webpage.  The preliminary runs worked well, so I dedicated a good part of last week to adding caching, so that if I ultimately refer to the same repository dozens of times, from week to week, I'm *not* waiting to request that webpage dozens of times.

## Development versus Testing

That's mostly fine.  Caching information like this---all text---is easy enough.  Every time we download something, we add the data to a JSON or YAML file, so that it's there for the next run.  We can rebuild the cache on every deployment, since that information might eventually become stale, but it's *probably* not going to change while the blog gets redeployed.

That is, the problem isn't the development side of this.  I raise this issue because of what's involved in testing:  If there's a bug in the code, such as emitting the wrong HTML or running into a race condition, the debugging cycle for [Jekyll](https://jekyllrb.com/) looks something like this.

 * Make a change to the plugin.
 * Confirm that a blog post uses the plugin as required by the current code, in case handling of the inputs has changed.
 * Stop the local server.  Until the server restarts, the local version of the blog is inaccessible.
 * Rebuild the blog.  Depending on the blog and the computer, this can be a multi-minute process.
 * Restart the local server.  Technically, this happens automatically with the build (or vice versa), but they provide different kinds of error messages at different times.

If there's an error, go back to the first step.

This is necessary, because Jekyll doesn't monitor plugins for changes after it has started, probably for good reasons.  However, it's still remarkably tedious, especially since it involves doing plenty of work that has nothing to do with the plugin at question, namely all the posts that do *not* use it.  For example, as I write this, **Entropy Arbitrage** has well over five hundred posts, of which only two use the GitHub plugin.

### Slight Improvement

While no less tedious, some extra work could be removed by creating a second blog with only one post, and using that framework for the testing.  While it would speed up each test, it still requires repeatedly stopping and restarting the server.

Worse, this approach introduces extra steps to the debugging process:  Once the plugin works, it needs to be manually copied back to the "real" blog.  And while I can't speak for anybody but myself, I will say that this is exactly the sort of manual step that I'm likely to forget about when I'm tired, so I'd rather avoid that direction.

### Utopian Dreams

The right way to solve this is, of course, to realize that a Jekyll plugin is merely code written in [Ruby](https://www.ruby-lang.org/en/).  It takes input parameters and returns a result.  There's nothing magical about it.

Therefore, we *should* be able to test a plugin along the following lines.

```console
ruby _plugins/github.rb
```

If that worked, there would be no tedious testing cycle or delay.  Like most other systems, the plugins could be tested as changes are made.  Make a change, and test the change.

Unfortunately, that couldn't be the entire story.

### Dystopian Reality

There are a few problems with running the code directly.

First, if you try this on your own Jekyll installation, you'll find that you get an `uninitialized constant Liquid (NameError)` for your troubles.  That makes perfect sense, since the [Liquid](https://shopify.github.io/liquid/) library isn't `require`d in the plugin's code; it comes from Jekyll, when it calls the plugin.

Even if we added the library, however, this still wouldn't work.  A plugin is mostly just a class definition, where the only code to run is the final line that registers the plugin's class with the Liquid libraries.  So, even if plugins *were* written as standalone scripts, they would still only actually do something invisible.

Finally and related, if we run the plugin's code from the operating system command line, what data are we testing that code against?  The plugin responds to method parameters, not the command line.

## Scaffolding

When building something complicated, whether it's a skyscraper or some code, we might erect [scaffolding](https://en.wikipedia.org/wiki/Scaffolding) around it, a support structure that surrounds the *real* structure to make different sections accessible.  That's what we need here.

### Take 1 🎬

Here was my first attempt, trying to just convince the plugin's code to run.

```ruby
require 'liquid'
require_relative '../_plugins/github.rb'

ght = GithubInlineTag.new
ght.initialize 'github', 'jcolag/dash', nil
puts ght.render()
```

This produces the following error.

```
_test/header.rb:4:in `<main>': private method `new' called for GithubInlineTag:Class (NoMethodError)
```

Well...*that* didn't work.  It fails to work in a peculiar way, though:  There *is* no `.new()` method in `GithubInlineTag`, and nothing is marked as `private`.  Weirder, if I create an empty method (`def new; end`) and explicitly mark it `public`, it doesn't change the error.

### Take 2 🎬

Considering the possibility that `initialize()` might be run directly to create objects---it shouldn't be, but I have admittedly never read through the Ruby interpreter's code to confirm---I combined the first two lines of code of the scaffolding, but that didn't work, either.  Running it produced the same error, just now referring to `initialize()`.

Again, the plugin doesn't mark anything as `private`, and declaring the methods `public` doesn't impact the error at all.  The interpreter is convinced that's not the case, though.

## Solutions

The solution was beyond my Ruby knowledge when I started this, but still mostly straightforward, once I connected the pieces of information floating around.

### Clue #1 --- Private Methods

This Stack Overflow answer comes from a question that's about a Ruby on Rails problem, but details [how to call private methods](https://stackoverflow.com/a/21563652/3438854) when confronted with the error described above:  Call the method using `.send()`, as in `GithubInlineTag.send :new`.

### Clue #2 --- Parse Contexts

This indirect call to `.new()` now also calls `.initialize()`---of course it does, because instantiating an object requires that it be initialized----meaning that it needs the three parameters that are required by any plugin.  If you don't recall, the `initialize()` method of almost any plugin for an inline tag has the following signature.

```ruby
def initialize(tag_name, text, parse_context)
  # ...
end
```

The first two parameters are for the testing itself, so they're easy.  The third is---as the name might suggest---a variable describing the current context of parsing the blog's Markdown source.

Documentation on writing Jekyll plugins is never clear on what the parse context actually is, since it normally gets sent automatically as part of the build process.  However, some research and testing turns up [`Liquid::ParseContext`](https://www.rubydoc.info/gems/liquid/4.0.1/Liquid/ParseContext) as the culprit.

### Clue #3 --- Revenge of the Parse Contexts

Finally, the `.render()` method also requires the `ParseContext` value.

### Basic Code

Based on our clues, the simplest test scaffold should look something like this.

```ruby
require 'liquid'
require_relative '../_plugins/github.rb'

context = Liquid::ParseContext.new
ght = GithubInlineTag.send :new, 'github', 'jcolag/dash', context
puts ght.render context
```

I can call this from my blog's root folder with `ruby _test/github.rb`, and it prints the results for [jcolag/dash](https://github.com/jcolag/dash), just as I want.  And it's simple enough that it can be made more sophisticated.

### Extending the Scaffolding

There are two obvious ways to enhance this test scaffolding, and neither of them takes much work.

First, rather than hard-coding the input string, the script can take it from the command line.  This is as simple as adding a couple of lines and replacing the immediate string value.

```ruby
repo = 'jcolag/dash'
repo = ARGV[0] unless ARGV.empty?
# ...
ght = GithubInlineTag.send :new, 'github', repo, context
```

That leaves the default in place if the user doesn't provide a repository, but overwrites that default when there's an alternative provided.

More interesting---especially for testing something like caching, where execution should take different paths through the plugin, depending on whether it has previously stored the information---it's possible to trace execution through the entire plugin.

```ruby
require 'tracer'
Tracer.on
```

The [tracer](https://github.com/ruby/tracer) library is a core part of Ruby's installation, so there's nothing extra to install.  Calling `.on()` causes the script to print how execution travels through the program.  It unfortunately also catches *everything*, down to the lowest levels of the standard library, but it still provides a searchable record.

### Solution, Take 4 🎬

Combining everything that we've learned gives us the following test script.

```ruby
require 'liquid'
require 'tracer'
require_relative '../_plugins/github.rb'

Tracer.on unless ENV['TRACE'].nil?

repo = 'jcolag/dash'
repo = ARGV[0] unless ARGV.empty?
context = Liquid::ParseContext.new
ght = GithubInlineTag.send :new, 'github', repo, context

puts ght.render(context)
Tracer.off
```

This version of the script will print the execution trace, if we run it as follows.

```
TRACE=1 ruby _test/github.rb
```

In my case, this produces nearly ten thousand lines of logging, so I hope that you'll forgive me for not pasting an example into this post...

If we just run `ruby _test/github.rb`, however, we only get the results.  We can also provide different repository paths on each run, to maximize coverage.

While *I* won't do it anytime soon, it should also be mentioned that the command-line input could also easily be replaced with reading from a file and calling `GithubInlineTag.send` in a loop to test many input values at once.

All of that is *much* better than constantly rebuilding the blog for a quick test.

* * *

**Credits**:  The header image is [work, technology, vintage, wheel, retro, clock](https://pxhere.com/en/photo/606288), by an anonymous PxHere photographer, is made available under the terms of the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
