---
layout: post
title: The Need for Modern Web Application Frameworks
date: 2021-08-08 07:13:32-0400
categories:
tags: [programming, rant]
summary: The state of the art must have changed...
thumbnail: /blog/assets/4901169636_78abb669bc_o.png
offset: -14%
---

* Ignore for ToC
{:toc}

![A canopy frame](/blog/assets/4901169636_78abb669bc_o.png "These workers get it.")

Let's start with a concise summary, to get this post directly to the point, with apologies to anybody who might have been traumatized by the standardized testing industry.

 > 2004:Ruby on Rails :: 2021:________?

Looking at [my résumé](https://john.colagioia.net/resume.html)---don't feel obliged to follow along; I only mention it to give the discussion a starting point---I noticed that, back in 2007 or so, I took my first shot at striking out on my own in the software industry.  I quickly or had already stumbled across [Ruby on Rails](https://rubyonrails.org/) in a book about the (informal) economics of web services.  Ruby and Rails were still somewhat obscure outside the startup space at the time, but the system was also by *far* more advanced than anything else used to develop web applications.  Especially when you include the "scaffolding" features, a functioning web app could be running for basically just a few minutes of planning.

As you might know, those early ventures didn't really go anywhere despite some---if I'm allowed to judge based on what launched and thrived shortly afterward---good ideas, for a variety of reasons, but working in Rails was still a huge upgrade, in terms of getting work done.  Rails took the then-tedious process of building a web application, and automated the most boring parts.

## Comparison

To give the younger and less technical among you an idea of the difference that Rails made---though I hinted at some of this a few weeks ago, when talking about [GitHub Copilot]({% post_url 2021-07-18-copilot %})---the first websites that I created were absolutely miserable projects, such as a simulated class registration system for my college for an open house.  We needed to hand-code every page that was involved---and sometimes every *variation* of a page, since there was no convenient way to modify the presentation based on data---usually with each page having a "form" object (that's "form" as in paperwork, like the form at the bottom to post comments, not as in shape) to collect data.

That form would allow the user to submit data to the server, and the server also needed to be mostly written from scratch.  The server needed to recognize which form was being submitted, process the data, and send a result back to the browser, which was usually a combination of response information and the page to use to display the information.

The protocols that make up the [web](https://en.wikipedia.org/wiki/World_Wide_Web) are "stateless," which means that, if I needed to remember information from page to page---for example, it might be interesting to know which user is logged in when they're about to delete something---I needed to *pass* the information back and forth between the browser and server, because anything that wasn't in transit would be lost immediately.  Libraries that were web-aware would handle this last part by having the developer stuff information into a variable named `session` that it would (try to) manage.

In some cases, this was (in retrospect) dangerous, as early e-commerce sites were sending information around the Internet without much care to who might be able to read it.  [SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security) was available by 1994, but almost everybody but the largest companies considered the certificates too expensive to bother.  This is part of why modern TLS security still assumes that knowing that the connection between your browser and the server is secure is equivalent to trusting the ownership of the server, even though that's not the case.

If you developed websites long enough ago, you'll probably recognize this mess as the [Common Gateway Interface or CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface).  Truth be told, I was *lucky* that CGI already existed, because earlier web programmers needed to build *that* layer from scratch, too.

I never developed anything in [PHP](https://en.wikipedia.org/wiki/PHP) to any serious extent, but I've heard that it improved the work a bit, by allowing programmers to use the server to dynamically produce webpages, rather than writing them manually.  One of the big features of the [dot-com bubble](https://en.wikipedia.org/wiki/Dot-com_bubble) was that just about anybody could generally get hired as a full-time web developer after learning some minimal PHP and [SQL](https://en.wikipedia.org/wiki/SQL).  The jobs didn't survive the crash---leading many to scramble for a different career or a more thorough education, which (I feel like noting) is where some of my best students came from in my [teaching days]({% post_url 2020-01-19-teaching %})---but it gives an indication of how rotten the work was, that startups were willing to pay far better than a living wage for no almost education or experience.  [Flooz](https://en.wikipedia.org/wiki/Flooz.com) wasn't going to just make *itself* a haven for money launderers, y'know...

Anyway, web development was enough of a nightmare that, by 2005 or so, I just didn't think that the web was going to work.  It had been [more than fifteen years](https://en.wikipedia.org/wiki/World_Wide_Web), and the most sophisticated programs fell into one of three categories.

 * Sites with little functionality that were still prone to breakage.
 * What were really desktop applications, but run in a virtual computer inside the browser (usually Java or Flash), and fairly likely to crash the browser before you were finished.
 * Amazon, which seemed to work, but going to the bookstore was still much faster and easier, unless you didn't want your neighbors to know what you were reading.

By contrast, after I started my company, I got an early consulting gig to produce a data entry/retrieval web application for a client.  I spent a couple of hours talking to them about what data they needed to manage, and drove home.  From my desk, I issued the relevant Rails commands, similar to the following.

```console
rails new NameOfApplication
cd NameOfApplication
rails generate scaffold location name:string address:string # ...and so on
rails generate scaffold product sku:string name:string location_id:integer # ...and so on
# ...and so on...
rails db:migrate
```

Honestly, *that* was 99% of the work, just specifying the data models.  It took care of the pages and the basics of the server.  The contract was planned to take a couple of months, based on my initial estimates, and because I didn't want it to look like I didn't take their needs seriously, I only really worked on it for a few minutes each day for a couple of weeks (not months), making sure to talk to them while I was working to any new information, cleaning up handling of the parent-child relationships---like a location having multiple locations within it---and matching the styles to the company's branding guidelines, and collected a significant fee for early delivery.  Everything was stable.

When I say that Rails was a big deal, that's what I mean.  For certain kinds of projects, it does most of the work on its own.  You figure out the "schema"---I gave an overview of [basic database knowledge]({% post_url 2020-04-05-database %}) last year, but I just mean the data relationships, here, which you can change as you go, if you're wrong the first time---and go.  There is no `session` variable (or none that you ever see), no hand-authoring every form (unless you want to), and no wasting time duplicating functionality for every kind of thing that the application deals with.

The tools generate that code, and you benefit from (as I write this) seventeen years of debugging most issues that prior Rails developers have encountered.

## Frameworks

The idea of a [web application framework](https://en.wikipedia.org/wiki/Web_framework) creating a foundation to plug functionality into, rather than having every developer build the entire system, changed the nature of the industry.  They're powerful, because they allow developers to skip the tedious parts that were all going to be fairly similar, anyway.

If you're fuzzy on the idea of an application framework, think of programming like assembling a [jigsaw puzzle](https://en.wikipedia.org/wiki/Jigsaw_puzzle), for a moment.  A standard puzzle starts out as a mess of pieces, and a picture emerges as the solver discovers connections.

Contrast that experience to a puzzle where the picture is on the box.  You go through a *similar* process, but instead of forming hypotheses about where clusters might end up, you already know what colors and textures are going to be placed in which areas.

And if we add a frame to the puzzle, the experience changes again, where you know the dimensions at the start, and so can more easily orient the partial images as they come together.

In some ways, a framework is similar to those modifications to the puzzle experience.

Or, if you don't like that analogy, consider making a new board game:  You *could* spend a lot of time selecting your game tokens, your dice, your money (if any), and so forth, *or* you can just borrow the common bits from another game.  For a while, a semi-popular gift was a box set of high-quality, generic "bits" for games, meant to replace the cheap plastic and cardboard sold with most games.  Then, you just care about the board, the rules, and anything else that might be unique to each game.

In either case, rather than providing the solver or developer with tools *to* build the project, the framework is---in the ideal case---an "empty" application for the developer to add functionality to.  In the case of Ruby on Rails, this meant that your web server, database code, e-mail code, and dozens of other major issues on a project are already solved once for everybody.  It's a frame, ready to receive your picture.

Note that the issues might not be solved in *exactly* the way that you would on your own, but the trade-off is that it's already done and mostly tested, which is much better for most cases.  If you'll pardon a goofy analogy, it's not impossible for everybody to build their own transportation, but we don't bother individually going to that effort, because paying professional designers, engineers, and mechanics---by buying a pre-manufactured car through a company---is cheaper, easier, and provides better results for most people.

Most frameworks today, as pioneered by Rails, take this a step further.  On describing the data, the framework creates what we call a [CRUD interface](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete), automatically generating simple index, add, show, edit, and deletion pages for data elements using what we call the [Model-View-Controller pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller).  Why?  Because that's what most applications *do*, data entry and retrieval.  Check the tabs that you currently have open, and I *suspect* that they'll fall into three categories:  Basic pages with information for you to read and no interaction, data management (blogs, wikis, social media, other information repositories), or a communication/streaming service, which is its own kind of monster.  It might have a fancy and appealing user interface, but your [kanban board](https://en.wikipedia.org/wiki/Kanban_board) is still nothing more than data entry.  Most *games* are just data entry, if you stop to think about it.

## The Present Day

Fast-forward almost fifteen years, and Rails has become more stable and faster---and I appreciate that---but building web applications in Rails is *basically* the same process that it was in 2007.  Meanwhile, most other web frameworks have replicated the Rails workflow, which...I still prefer Rails for many uses, but the fact that I could---and sometimes do---use [ASP.NET](https://dotnet.microsoft.com/apps/aspnet) (which has "modes," for lack of a better term, that effectively turn it into Rails for C#) makes Rails less important, in terms of what it enables.  But it's not just Microsoft, of course.  There's also Elixir's [Phoenix](https://www.phoenixframework.org/), Go's [Beego](https://beego.me/), PHP's [Laravel](https://laravel.com/), Haskell's [IHP](https://ihp.digitallyinduced.com/), Java's [Jakarta EE](https://jakarta.ee/), JavaScript's [Express](https://expressjs.com/), and literally dozens of other major competitors and "clones."

After all, that should be the question for any development tool:  What does this tool/system enable more readily than alternatives?

Or, if you want to put it into more competitive terms, where's the advantage to using Rails, if almost everybody has the same functionality available to them?  If everybody can accomplish the same thing in the same amount of time, then all the tools are basically just there for aesthetic purposes.

## The Future?

That has led me to start wondering:  If Ruby on Rails was what is now today's state of the art, effectively "fifteen years in the future" in 2006--2007, what web application frameworks am I not seeing right now, in 2021, that are fifteen years in *our* future, the framework that everybody else is going to work to catch up to?  That is, we've all been given a lot more to do in web development, and we've all learned more about deploying a product.  So, the idea that we should still specify data objects, and then hand-edit a bunch of generated files to fit what the application needs, seems like it keeps things more difficult than they need to be.

This being the software industry, this requires dealing with useful, if trite, push-back.  Specifically, whenever technologies converge and stagnate, there's the idea that it's for a reason.  "Rails," we might be told, "found the sweet spot of normalizing everybody on MVC/CRUD applications, so we probably don't need more than that."

Note the similarity to my comments that the web was never going to take off, because it wasn't good enough at the time.  So, instead of nodding in resignation, let's answer...

There are other ways to frame questions like this, such as choosing which frameworks to learn or teach.  Really, though, my central question is why I can't do even more with even less effort.

### Why Not Just Live in the Moment?

Other than my self-centered quest to value my time more than a computer's, you might rightly ask why I would bother.  It's hard to improve on MVC and CRUD, and there's always the imaginary chance that artificial intelligence will suddenly start writing software for us...even though I did write an entire post about how [artificial intelligence won't replace programmers]({% post_url 2021-07-18-copilot %}).

So, to explain how web application frameworks can improve, here are some examples of things that, as I have recently been creating new web services again---[Bicker](/blog/tag/bicker), [All Around the News](https://allaroundthe.news/), [Fýlakas Onomáton](https://github.com/jcolag/fylakas-onomaton), among others that I can't talk about, because they're either not finished or not mine to discuss---I find myself dealing with enough that they probably can (and *should*) be automated by the framework.

 * **Adherence to style**:  I try to have my Rails applications all abide by the consistent, usually best-practice, advice of [Rubocop](https://rubocop.org/).  However, Rails apparently doesn't *care* about Rubocop, and so the files it generates create a variety of warnings that could easily have been avoided.  Because I'm never quite sure that it's safe to update the style---surely the Rails team has a *reason* to violate the style guide, right?---I check in the generated code, then update the style, and check that in after verifying that I didn't break anything.
   * I should mention that, while I think that [Go](https://golang.org/) gets far too much attention for features like having a "fast compiler" and tedious 1980s-oriented ideas like being able to "read code out loud," it gets far too little attention for requiring that all "public" code---that is, the appearance of the code while you're not personally editing it---share the same formatting.  It's disappointing that other languages didn't rush to copy that idea.
 * **User authentication and roles**:  I follow the same tutorial every time for adding Devise, Rolify, and CanCanCan to my Rails application.  Almost nothing changes from project to project.  But since I don't start a new project frequently, the process also doesn't stick in my memory, so I keep working from that same tutorial to do something that almost every modern web application needs to do immediately.
 * **Administrative pages**:  Once there are users and roles, some users are going to need dashboards of the entire system to handle support requests or otherwise tinker with the data.  This is easy to build, of course, but it's both time-consuming and so easy that someone *else* should do it, and do it with a consistent interface.
 * **Better graphical design**:  Speaking of interfaces, people have preferences and projects have brand guidelines, of course, but a generated web application shouldn't look like it was written in 1993.  Especially given how few developers have any background in design, generated views should be passable.  To my knowledge, no framework just says something equivalent to "we're going to use [Material Design](https://material.io/) unless you turn it off."  I picked Material, because it's relatively famous, but feel free to pretend that I said [Carbon](https://www.carbondesignsystem.com/) or some other formal system.  Even just using [Bootstrap](https://getbootstrap.com/) would work, if it allowed for choosing a theme from something like [Bootswatch](https://bootswatch.com/).  I care much less about which system is used, here, than *something* being used to save developers from needing to make a choice that they might not understand or even care about.  It shouldn't take effort to make a project look respectable.
   * Again, I should mention that many frameworks *include* Bootstrap or make it an option, but the generated views don't use it, and the option isn't turned on by default.
   * This is a bit beyond the topic, but I *should* be able to specify at least the basics of my project's brand guidelines---logo, fonts, color palette, and preferred curvature ratios, primarily---and a standard design language, and just let the framework integrate it into the application's design system and adjusting other colors to work with what's supplied.
 * **Parent/child relationships**:  When I say that one kind of object refers to another kind of object, the user is expected to know and type in the ID, by default.  In reality, the ID should usually either be known from context---the classic example is a blog comment knowing which post it's associated with, because the user is on that page---or get chosen from a drop-down.  Right now, the developer needs to create each of those by hand, rather than making it a switch during generation.
 * **APIs**:  Especially in a world where developers might need multiple user interfaces to their application (different mobile apps, a JavaScript framework, and so forth), automatically generating API calls alongside the normal controller and keeping them synchronized until the developer says to stop seems obvious, but it's still mostly manual.
 * **Updating views and controllers**:  Once the scaffolding code has been generated, it's entirely up to the developer to maintain it, even as the underlying model might change, which causes errors.  Yet in most cases, a simple memory of what has happened previously would indicate what needs to change.  If a text editor can figure out to change all instances of a name by context, so can Rails.

I could probably go on for a while, but I think these make the point that there's plenty of room for web application frameworks to improve the lives of developers, even *before* we get to the more esoteric ideas, such as automatically generating mobile apps based on the API and style guide, standalone desktop/kiosk software, converting the server into micro-services, or pages that can function without network connectivity, all with the same tools.

And bear in mind that these are only ideas that come immediately to mind, mostly based on prior boring work that I've had to do.  As the (apocryphal but useful) Henry Ford quote goes, though, "If I had asked people what they wanted, they would have said faster horses."  The above are just my faster horses.  When Rails was first released in 2004, I didn't *know* that I wanted scaffolding or choices of basic libraries made for me.  And so, it's safe to say that I have no idea what would make me equivalently happy or impress me to the same degree in 2021 and what the industry might accept as the minimum in 2035.

## Futures of the Past

Oddly, there have been some actual attempts to push the boundaries.  Members of the Rails community briefly worked on [Hobo](https://github.com/hobo/hobo), an enhancement to migrations, data types, permissions, users, administration, and more.  Likewise, JavaScript briefly had [Hoodie](https://github.com/hoodiehq/hoodie), which provided some interesting offline-first default features.  I gave both of them a try, when they were new, and liked them, but they didn't get any traction, and both projects seem to basically be dead, now, with no websites and no updates in years.

So, are there other up-and-coming frameworks that make the competitors look like they were designed over a decade ago...?

Tellingly, I asked this question on [a popular developer forum](https://www.indiehackers.com/post/where-are-the-modern-web-frameworks-dc80d75252), and it felt like I was asking something completely alien.

There were the obligatory people telling me that application frameworks were all hype, and I should go back to writing everything manually; as someone who has written directly to binary files and built an input device---a [light pen](https://en.wikipedia.org/wiki/Light_pen), if that's of interest to you---from parts, I'm always amused when people try to tell me which layers of abstraction I need.  Their opposites are there, suggesting that the "no-code" systems with custom code are the future.

There were people pitching their favorite Rails-like framework, with no indication as to how it's an improvement over Rails other than their preference of underlying language.

However, other than one mention of [Apache Beam](https://beam.apache.org/)---which is for specific needs that I don't think I have---it seemed like the idea of "the modern counterpart to what Ruby on Rails was to the state-of-the-art in 2006" wasn't even *comprehensible* to that community.

What I find most peculiar about this is that software development is an industry where we generally don't go more than a few days without somebody pitching a new programming language, protocol, design philosophy, user interface design system, or other Way to Do Things.  Everybody wants to do more with the time that we have.  Developing web apps, though, doesn't seem to have changed much in fifteen years.

## It's Hard, Though

Of course, I get it.  *I* certainly don't want to write my own framework, and I don't have the resources to support it if I did.  But it's strange that there aren't a dozen "Rails, but better" projects at any given time.

It's surprising that nobody has taken Hobo a step further, integrated the offline-first features of Hoodie, and added the intelligence of a basic text editor.

If I'm tired of custom-styling every application just to make it look decent and fixing code warnings, then surely the sorts of people who dream of being able to say that a major technology company uses their software would be rushing to release something.

And yet...I *hope* this isn't my manifesto for a new framework.  I genuinely don't have the time for it, nor do I have the patience to support it.  So if anyone wants to become the next cult figure for developers, the ideas are all yours, and I'd love to see what you come up with.

 > 2004:Ruby on Rails :: 2021:________?

Somebody fill in that analogy!

* * *

**Credits**:  The header image is [Framework](https://www.flickr.com/photos/26170836@N05/4901169636) by [Steven Lilley](https://www.flickr.com/photos/sk8geek/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/) license.
