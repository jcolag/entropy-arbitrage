---
layout: post
title: Advice for Aspiring Career-Hoppers, Part III
date: 2020-04-26 08:02:42-04:00
tags: [quora, career]
summary: Hopping to a software career
thumbnail: /blog/assets/25392428253_f0416515b6_c.png
offset: -25%
---

As promised, this is the third part of a [short series](/blog/tag/career/) to provide some quick guidance for people who would like to reach out feelers into a possible software development career.  As I mentioned in the [first post]({% post_url 2020-04-12-career %}), a lot of this material is recycled from some of my old Quora answers, updated for current times and the tone of the blog.

![Discussing code](/blog/assets/25392428253_f0416515b6_c.png "Discussing code")

To be completely clear, I'm writing this because I know there are people out there who can use the distraction of picking up a new skill.  If you come out of self-quarantine with a marketable skill, that's great.  But if you don't, you're no worse off than you were, so it's also fine to not be interested or to give up part-way through.  This is entertainment, not recruitment.

This time through will continue the technological considerations, but from a more abstract perspective of the bare minimum you should *definitely* learn about programming to have enough of a foundation to be able to learn whar you need later.  Next time through, I'll dig into various non-technical issues.

## The Basics

There are a few areas you should be familiar with to get to the point where you can start dipping into a project without being at a total loss.

Specifically, we'll try to outline the set of things to learn so that, while you work, you have enough information to get some simple things done and---more importantly---have some sense of where to go for more information.  Since I don't know what specific technologies you are going to work with, I won't be giving you concrete details, but rather giving some idea of what to look for in documentation and tutorials before anything else.

### Broad Concepts

Most web application frameworks want you to structure your application in a [Model-View-Controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) (MVC) pattern.

![MVC Workflow](/blog/assets/MVC-Process.svg "MVC Workflow")

In broad strokes, this means that your application has three pieces.

 * The **model** is the representation and sometimes manager of your data storage.

 * The **view** shows the user results.

 * The **controller** takes user input, makes changes to the **model** when necessary, and then takes information from the **model** to hand to the **view**.

The boundaries between those three pieces can sometimes be a little bit fuzzy and a matter of taste.  If you have a list of names that need to show up in alphabetical order, for example, some programmers are going to see that as a job for the view (the order is part of the representation of the data), while others will consider it a job for the controller (the order is part of how the view needs the list), and you might even see an argument that it's part of the model (ordering is part of the request for data).  In other situations, the boundaries will be clearer.

If you put code in the "wrong" part of the pattern, keep in mind that there's no real harm done.  The pattern is a guide to help you structure your program, not a requirement.  The worst that will happen is that you'll find that code getting in your way when you make changes later; if that happens, you can always move the code around then.

In fact, it's best you learn this now instead of later:  With the exception of changing live data that you (or someone else) rely on, you're going to get a lot further by doing the wrong thing now than waiting to figure out what the right thing to do is later.  It's a lot easier to figure out what you need to do when you see the wrong thing happen and you can think more concretely about code.

So, with that in mind, let's walk through those three parts.

### Models

As mentioned, the application **model** is how the programmers think about the data involved.  Generally speaking, a model includes four pieces.

First, we have the *database management system* (DBMS), the software you're using to manage the storage, manipulation, and retrieval of data.  Rather than discuss that here, I'm going to save space and point you to the post I wrote [on this topic]({% post_url 2020-04-05-database %}) a couple of weeks ago.

Next, we have a *data definition language* (DDL), the interface you can use to describe and update the database tables and relationships your application uses.  For most web application framework, they don't actually call it a DDL, for some reason.  Instead, the term you want to look for is a *migration*.  Migrations include the list of all the changes you've needed to make to your database to support the application over the course of development, along with version numbers.  Because you're tracking the changes, you will be able to move backwards and forwards to test how the database used to work.

Hand in hand with the data definition language is the application's version of the model, code that mimics the structure of database records that your programming language can understand and use.  Some frameworks can generate migrations for you, based on your code's model.

Finally, we have the *query language*, the interface you can use to request and update data from the database.  Most databases have one of their own (most relational databases support something called SQL), but more often, you'll work with what's called an *object-relational manager* (ORM), a library that converts the ideas of an object-oriented programming language (I'll talk about objects later) to and from the ideas of a relational (or other kind of) database.

For the query language, you'll want to understand how to create, retrieve, update, and delete records, what are referred to as "CRUD operations."  Like I discussed in that database post linked a few paragraphs back, retrieval may require joining two or more record types together, filtering out uninteresting records, and possibly ordering or grouping the results.

So, if you look up what your code models should look like, how to create migrations, and how your object-relational manager handles CRUD operations, you should have the model part of your application handled pretty well.

### View

There are probably some exceptions I'm not aware of and there will certainly be exceptions in the future, but for now, all web applications require writing some HTML to display information.  Everything the user sees needs to be presented in HTML.  So, you should be able to create HTML pages with forms, at the very least.  You can learn that in a wide variety of places, but [Wikiversity's course](https://en.wikiversity.org/wiki/HTML) looks decent on a superficial inspection and has been made available under a free license.  But feel free to ignore that link and find somewhere more comprehensive.

In addition, anything you see on a page that you would like to understand, you can right-click on (almost) any webpage and select **Inspect Element** on the context menu.  That will bring up the actual HTML code for that section of the page where you can read it.

The pages you create with just HTML are going to be boring and you'll eventually want to learn [CSS](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) to style your page, but that can wait until later.

Beyond that, web application frameworks generally have three additional things you'll need to learn.

The piece that's almost always trivial is embedding "components" into your page.  Most web applications have multiple pages and many of those pages share a look.  You might have a menu on every page or a footer with copyright and contact information.  It's silly to copy that to every page that needs it, when you can write it once and include it into your page as if it was an HTML tag.

Often just as easy, but not always, is how you're expected to accept information from the **controller** and insert it into the page.

Finally, the **view** needs some way of sending user input back to the **controller** for processing.

## Controller

Whereas some of the above might not feel like programming to you, processing data is much more traditional and happens using your programming language of choice.  So, this will be sort of the treasure map equivalent of an introduction to programming class.

Briefly, programming is about taking real-world processes and converting them into steps that are straightforward enough for a computer to follow without any ambiguity.  You know that person in everybody's life (it might even be you) who, when asked to "take a seat," picks up a chair and asks where they should take it?  Computers are like that *all the time*, so this is largely about making sure there is no possible way that your program can be misinterpreted.  Because, if you leave it to the computer to guess what you meant, the computer is going to guess wrong.

I won't teach you *how* to program, because that would take up too much time (though I'm willing to give it a shot, if there's interest), but instead will trust you to pick up the general philosophy while you're looking for the following language features.

 * **Variables** are where you store data in the program.  You can think of them as boxes that can only hold one thing at a time.  When you change the value of a variable (say, by "assigning" 5 to it), the old value is gone forever, unless you assign that value to another variable.  Some programming languages require that each variable have a *type*, limiting the kind of data it can hold to---potentially---blocks of text, certain kinds of numbers, or entire parts of the program.

 * **Objects** are, essentially, little programs that operate inside your larger program.  They have data of their own (*properties*) and code that they run (*methods*, for more on which, see below), but the packaging makes them easier to manage or share with another program.  Objects are generally created from templates called **classes**, so you'll have a class and create a new object of that class.  In some languages, the value of every variable is an object, but other languages distinguish objects from "primitive data types" like numbers.

 * **Conditional Statements** are ways to select between two or more choices.  For example, a good performance review might be ignored for managers, automatically trigger a promotion for low-level employees, and require further analysis for mid-level employees.  That's a choice where the condition is based on the hypothetical employee's role in the company hierarchy.

 * **Loops** are ways to repeat parts of a process conditionally.  For example, we're probably all familiar with the instructions on shampoo bottles:  "Lather.  Rinse.  Repeat."  The last step tells you to do everything again, and it's implied (if nothing else, by the fact that you have a limited amount of shampoo) that you should only lather and rinse twice in total.  But that's not **explicit**, so a computer would constantly hit that last step and repeat until the system dies.

 * **Functions/Methods/Procedures** are similar to Objects (above), in that they allow you to package up parts of your program, but they're usually just code to be called from somewhere, rather than independent objects that respond to input.  Methods, specifically, are parts of classes that let an object of that class respond to messages.

You'll also need to find out how a **controller** is expected to package up data for the **view** to consume.

For some basic context, each page in your web application is going to be represented in your controller by a class.  An object of that class will be created when a user accesses the page, and the user's request will go to a method in that object.  Similarly, your data models will be classes representing each table, with each record represented as an object of that class.

So far, so good?  Good, because if you can get a handle on those five things, you'll be able to at least write simple programs with some direction.  And if you can do that, you can start practicing and learning what works and what doesn't.

## Next

Giving you some time to learn the specific versions of these key ideas that relate to your chosen technology stack, we'll end here for now.  If you track down the above information, you *should* be able to read through a tutorial for your chosen web application framework and not feel too overwhelmed.

Next time, we'll pick back up with some tools you should probably know how to use to make your life easier.

#### <i class="fab fa-quora"></i>

* * *

**Credits**:  The header image is [Untitled](https://www.flickr.com/photos/wocintechchat/25392428253/) by [WOCinTech Chat](https://www.flickr.com/photos/wocintechchat/), made available under the terms of the [Creative Commons Attribution 2.0 Generic license](https://creativecommons.org/licenses/by/2.0/).  The [MVC Worklow Diagram](https://commons.wikimedia.org/wiki/File:MVC-Process.svg) has been created and released into the public domain by [RegisFrey](https://en.wikipedia.org/wiki/User:RegisFrey).
