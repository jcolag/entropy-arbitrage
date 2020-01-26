---
layout: post
title: The Worst Programming Language?
date: 2020-01-26 07:09:33-0500
tags: [programming, programminglanguages, thoughtexperiment, quora]
summary: Thought experiments on what a terrible language might look like
thumbnail: /blog/assets/Friedrich_John_nach_Matthäus_Loder_Sisyphus_ubs_G_0825_II.jpg
offset: -45%
---

I'm trying something new, here, that I've hinted at [once]({% post_url 2019-12-08-greetings %}) or [twice]({% post_url 2020-01-12-quora %}), recycling some of the answers I have written on Quora and updating them for my current line of thinking.

![Sisyphus](/blog/assets/Friedrich_John_nach_Matthäus_Loder_Sisyphus_ubs_G_0825_II.jpg "Caution: Sisyphus at work")

To start off, I figured I would go with something fun---for me, I mean; you're on your own, dear reader---so this post is based on [<i class="fab fa-quora"></i> If you were given the job to make the worst possible but still usable general purpose language, what features would it have or not have?](https://www.quora.com/If-you-were-given-the-job-to-make-the-worst-possible-but-still-usable-general-purpose-language-what-features-would-it-have-or-not-have), which I originally answered on April 4th, 2014.  Obviously, it has been edited substantially to better fit the tone and format of **Entropy Arbitrage**.

## Excluding Irrelevant Choices

I believe that people can cope with just about any system, so weird mental models---for example, pretending that variables are people who are friends or enemies whose values are based on how close they are to friends---are off the table.  Those can be amusing, add to the learning curve, and make it harder to take the language seriously, but you only need to get accustomed to the core premise one time and it just becomes the way you work.

Another possibility that doesn't *quite* hold water is the concept of the [Turing tarpit](https://en.wikipedia.org/wiki/Turing_tarpit), where all but the simplest operations need to be explained.  You can see this when trying to work with [Lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus) or a [Turing machine](https://en.wikipedia.org/wiki/Turing_machine) (such as [PosTuring](https://github.com/jcolag/PosTuring), if that's your thing) and it can be a nuisance.  However, there are two aspects to programming that make this a bad move.

 * The pain doesn't come from *difficulty*, but rather from *tedium*.  So, we know how to multiply two numbers, but doing so means adding them repeatedly in a loop, and adding them requires incrementing them in a loop, and maybe incrementing them requires some bit-twiddling code.  Nobody really wants to do that, sure, but if you offered a low-end software developer's salary for someone to work that way, your company would still get candidates filling out the application.
 * Because we're talking about a difficulty that is *basically* just copying and pasting templates, the "tarpit mentality" also fails us, because we can just automate the pain away.  In other words, we can just write a compiler that turns a high-level language that people enjoy working with into a Lambda calculus expression or whatever the low-level language might be.

For the most part, we can probably also ignore unpleasant syntax.  Partly, that's because programmers will get used to the thing they see most frequently.  And partly, it's a lot like the Turing tarpit problem:  If it's bad enough, people will just write a compiler to translate around the pain.

Instead, what I think we need are language features that are difficult to control or make collaboration difficult.  If we can find features that do both, so much the better!

## Under the Rug

Some of the easiest wins, I think, come from ensuring that *all errors are logic errors*.  That is, a compiler or interpreter not only wouldn't warn about dangerous or obviously-wrong constructs, but **can't** warn about them, because they're legal and may even be sensible in some context.

### Typeless Type System

I want to be clear:  I'm not a "languages need strong typing or they're terrible" kind of person.  I have written and will still happily write code in Ruby, JavaScript, and other languages where we can write code like this:

```javascript
x = 4;
x = x.toString();
x = [ x, x ];
x = function() { return 4; };
```

It's not *terrible*, of course, but it immediately means that type-mismatch errors aren't going to make themselves known until much later when the variable is used.

### Orthogonality

Following onto the (lack of a) type system, in my experience, authors of programming language textbooks like to talk a lot about [orthogonality](https://en.wikipedia.org/wiki/Orthogonal_instruction_set)---the idea that every tool (instruction) should plausibly be usable with any material (data type)---and, especially in older books, can be inclined to call out examples of where famous languages "fail," because the programmer needs to learn an exception.

The orthogonality fetish, then, is one of the top features on my priority list.

Imagine a language where everything can be treated as syntactically compatible with anything else.  Intuitively, the sum of a structure and a loop doesn't mean anything, and any sane language would dismiss it as an error.  But if everything has *some* sort of value that can be added?  Then it must do *something* and it should result in something different than multiplying or dividing them.

The **PL/I** language had orthogonality as a guiding principle, so the assorted data types were all compatible.  Meanwhile, languages like **LISP** include the idea that code is just a kind of data.  Combine the two, and we have something very close to having a language that's "error-free," in that it's more difficult to write code that, from a mechanical perspective, will fail.  Instead, failure merely does the wrong thing.

### Homoiconism

The **SNOBOL** language deals with string data in a surprising way.  Specificially, any undefined name represents *itself* until it's defined otherwise.  To make things more interesting, assignments are really just chains of equivalence.

So...

 * Using the variable `abc` without doing anything else, it refers to the literal string `"abc"`.
 * If `abc = def`, then `abc` refers to `"def"`.
 * If `def = ghi`, then `abc`, in referring to `def`, refers to `"ghi"`.
 * And so on...

Whew!

It's not hard to see how this not only continues the theme of camouflaging errors, but also introduces a theme---that we'll get back to later---of not being able to trust operations without a *lot* of communication to avoid misunderstandings.

By the way, I should mention that **SNOBOL** is probably the most important programming language you've never heard of, because it laid the groundwork for [regular expressions](https://en.wikipedia.org/wiki/Regular_expression) with its *patterns*, a first-class data type with a bit more flexibility than modern regular expressions have.

### Defaults

Default values are the last of the easy ways to pretend there's nothing wrong.  But there are a few different kinds of defaults, after all.

 * Default values for variables aren't that interesting, but we want orthogonality (remember *that*...?), after all, and homoiconism (remember *that*...?) is a kind of default we're already including that makes it much more interesting.
 * Default values for function parameters are more interesting, primarily because most languages make those parameters optional.  So, in this case, we can call just about any function with any number of parameters.
 * Default methods are probably the closest to the chaos we want, though, assuming this is an object-oriented langauge.  **Ruby**---I hope you didn't think that all the features would come from obscure languages---allows developers to take action when an incorrect method is called by implementing the `method_missing` method.  Here, the `Object` class would include a (default) `method_missing` class that does nothing, but can be overridden in child classes.  Or maybe it **can't** be overridden, because that would make it easy to report and handle errors...

All three of these produce the same approximate effect, of course:  There is no such thing as a "wrong" variable name.

## Mistrust

As mentioned under *homoiconism*, above, a great way to make a language harder to use is to make it more difficult to trust what operations will do unless the lines of communication between developers are extremely clear.  And there are a few features besides homoiconism that fit, here.

### Positional Security

The discovery of this idea is pretty entertaining, so indulge me for a bit:  In one of the first years I taught the [client/server programming]({% post_url 2020-01-19-teaching %}#clientserver-programming) class, one of the more ambitious students wanted to learn **Java** along with working on their project.  Since I wanted to keep everybody learning similar material from the perspective of the class, I didn't want them to use the high-level classes that separated protocols and roles.  So, we dug into the API documentation and followed the inheritance tree to find a class that looked almost perfect.

The problem?  The class was marked something like `private` and `final`, so we couldn't instantiate it directly or create a subclass to work with.  Asking around, we got advice that sounded like a wild goose chase, but turned out to be exactly what was needed:  Extract the library class from the archive to copy it inside the application directory.

I have to assume that the **Java** ecosystem no longer does this, but the idea that `private` turns into `public` if you're in the same folder is a feature as interesting as it is baffling.  Imagine doors that unlock as long as the person trying to get in is...in your neighborhood.

So, while this is an idea that definitely needs more work to be something that isn't just hand-waving or a specific implementation, the idea of program components moving around in a simulated physical space, with security restrictions changing depending on proximity, seems to be the most general version of the idea and one likely to make those restrictions difficult to use.

### Grave Reservations

While it borders on syntax, some languages such as **PL/I** don't have any reserved words in the language, meaning that variables can have almost any name.  Because of that decision, we can write code that looks like...

```pli
if
  if = then
then
  then = else
else
  else = if
```

Similar but distinct ambiguity is in very early versions of **FORTRAN**.  Because code would often be written out by hand by engineers and typed ("keyed in") to [punch cards](https://en.wikipedia.org/wiki/Punched_card) by someone in a more clerical role, compilers would completely ignore white-space.  I have never found confirmation of the reasoning, but it seems extremely likely that the choice was made in order to prevent a secretary's intuitive inseration of spaces into a compound-word variable name wouldn't cause the compiler to fail the program back when running software had a significant per-minute cost.  But either way, it meant that a variable assignment such as...

```fortran
DO I = 1
```

where the variable is named `DOI`, and the first line of a loop...

```fortran
DO I = 1 TO 10
```

take a while to figure out.

Granted, syntax highlighting solves most of these problems for us, so they wouldn't be the most exciting aspects, certainly.  But it adds a potential difficulty in reading code that doesn't need to be there.

### Look *That* up in Your Funk & Wagnalls

Since reserved words (or their lack) is largely a matter of naming, it may make sense to introduce a related idea from **FORTH**, the *dictionary*.  There, programmers define functions and insert them into the language runtime's dictionary, essentially a list of definitions.  When parsing, the interpreter searches the dictionary for every name that it finds, only resorting to inbuilt language features if the dictionary search fails.  There is also no uniqueness restriction on the dictionary.

This means that both existing functions and inbuilt features can be spontanously redefined.  The old definitions are still there, but the search begins with the most recent entries and moves backwards, so the most recent version is the version that will be found.

But it gets even better (worse), because variable names and even *numbers* are part of the dictionary search, so that the parser doesn't need anti-orthogonal exceptions.  And many **FORTH** programs take advantage of this by ending with a list of constants used.

```forth
:0 0;
:1 1;
:-1 -1;
```

If a number is used frequently in the program, finding it near the last definitions means that it will be found faster than if it needed a more thorough search.  And because the function body is partially compiled when created, the return values are the real versions, increasing the speed of the probram significantly.

But if a developer on the team makes a typo or is trying to be clever?

```forth
:1 12;
```

Uh-oh...

### Jumping Around

I could, of course, just spend some time here explaining the context problems with a statement like `GOTO`, such as every line of code suddenly being the potential next statement from *any other line of code* and needing to be potentially written with that in mind.  I could just do that, but we can find a couple of features more troubling than that.

As a response to Edsger Dijkstra's famous [*GO TOs Considered Harmful*](https://homepages.cwi.nl/~storm/teaching/reader/Dijkstra68.pdf) in March of 1966, a **Communications of the ACM** April Fool's issue in the 1980s recommended the `COME FROM` statement as an alternative, a command which would pull execution away from its current position and to the statement.

It was created as a joke, of course, but it *does* manage control flow.  And notice how this has all of the same context problems as `GOTO`, but now any code can be run in such a way that it doesn't complete, until control gets pulled to another location.

Oh, and just for good measure, the **C** standard library has `setjmp()` and `longjmp()`, which allow the programmer to set jump/goto targets at runtime and refer to them through variables that can be passed around the program.

Presumably, barring any behavior that might emerge from *orthogonality*, as described above, these jumps---yanking control away from "breadcrumbs" placed by the program and spread from a variable---should be the only control flow in the program.

### Watchdogs

Some versions of **COBOL** had a `WHENEVER` statement, essentially an event handler based on an arbitrary condition to execute a single statement.  In other words, now you have something watching your code, ready to take action in some way that may or may not be visible.

For example, new code could include something like...

```cobol
WHENEVER FIELD-A GR 99 OR FIELD-A LE 1
  FIELD-A = 50
END-WHENEVER
```

Now, any time that `FIELD-A` hits one of the limits, its value is bounced to the middle-value with no indication of what happened.  Now imagine a loop counting down (using `FIELD-A`) from 75 down to 0...

### Pass-by-Name Parameters

**Algol 68**---and the **C Preprocessor**'s macro system---use(d) pass-by-name semantics, executing subroutines (or macros) by substituting the text of the actual parameter for the formal parameter.  The traditional example is using a swap routine to switch an array element and its index.

```c
swap (a,b)
  ta = a;
  a = b;
  b = ta;
arr = { 3, 3, 3, 3, 3, 3 };
i = 4;
```

One direction works fine.

```c
swap (arr[i], i); /* - Good! */
  ta = arr[i] = arr[4] = 3;
  arr[i] = arr[4] = i = 4;
  i = ta = 3;
```

The other changes the index, which changes where the final replacement occurs.

```c
swap (i, arr[i]); /* - Bad! */
  ta = i = 4;
  i = arr[i] = arr[4] = 3;
  arr[i] = arr[3] = 4;
```

Note that pass-by-name routine parameters have *legitimate* uses, too, the most famous being [Jensen's Device](https://en.wikipedia.org/wiki/Jensen's_Device), a metaprogramming technique that passes entire expressions as parameters to leverage simple code into performing complex actions.

## Anti-Collaboration

For any significant project, software is written by a team.  A good language, in this context, is going to be one where it's easy to coordinate with fellow developers, where failure to make that easy is the core of the so-called [software crisis](https://en.wikipedia.org/wiki/Software_crisis).  Resolving the software crisis is the core premise behind the adoption of object-oriented and functional programming.

These features, then, are designed to stymie teamwork.

### Parser Manipulation

From **Python**, we can steal access to the `parser` object.  Actually, we could go a step or five further.  We could conceivably allow a program to redefine the entire language syntax for its run, so that every programmer can work the way he wants.

However, in doing this, working with other programmers is difficult, since every module---every block of code---could conceivably be written in what seems to be an entirely different language!

### Modules

Especially because of the parser changes described above, I would strongly recommend having any module system based on the **C** pre-processor.  That is, `#include` merely imports the entire text into the main source file.  In *actual* **C** programming, that's not what this is designed for; `#include`s are generally used to import metadata, while the *linker* handles the actual module management.

However, it's entirely possible to write **C** programs where `#include` handles all the module management, and that's what I recommend, here.

Watch out for those rewritten syntaxes, not to mention (a real problem in **C**) header files that stupidly include each other...

## Miscellaneous Features

While I have a couple of other possibilities, below, these are all the remaining features, that don't really fit anywhere else.

### Pointer Arithmetic

A worst-case scenario seems like it would be to allow pointer arithmetic like **C**, but not to (necessarily) have the pointers map to hardware addresses, instead treating them more like **Java**'s hash value handles.  So, yeah, you can add five, but we can't guarantee that the result means anything.

### Non-Orthogonal Minimalism

While I previously suggested that minimalism wasn't *entirely* a fruitful route, there is a way to introduce the concept.

We could, for example, trim down certain kinds of the remaining features to an absolute minimum, because "we're not here to over-complicate things."  So, addition is worthless, since you can just subtract negative numbers, and you can just get negative numbers by subtracting from zero.

This isn't quite the same as a *Turing tarpit*, because we have already seen some very high-level features.  This is just cleaning out some redundancies...

### Syntax

Yes, I promised that syntax wasn't going to figure in.  But there are a couple of special cases that come to mind as almost pathologically bad.

 * As mentioned, you can't have an irritating language without special handling of white-space, whether it's in the style of **FORTRAN** (indents represent the continuation of the previous line *and* must be of a specific length), **make** (older versions require indentations to always be a single tab character), or **Python**.  Special white-space is arguably important in an era where many editors try to "fix" white-space on every save.
 * **APL**'s expression handling has equal operator precedence and strict right-to-left associativity, which is just syntax, but never fails to baffle people.  For example, `1 + 2 * 3 - 4` is `-1`, because we start with `3 - 4 = -1`, then `2 * -1 = -2`, then `1 + -2 = -1`.

### Comment-Free

We had to know this was coming, eventually, and is also self-explanatory...

### Take-Aways

It's obviously tempting to add features from obscure programming languages that were *intended* to be problematic.  For example, **INTERCAL** includes the ability to activate and deactivate each class of statements while the program runs.  But (other than `COME FROM`, which I can't resist and *did* appear in a major trade publication) I think it's more troubling to consider that all of the features listed above originate in *real* programming languages that many developers have used to create software and/or have been highly influential.  For example, you've probably never heard of **SNOBOL** before today, but it was used to create many compilers and---as I mentioned above---it has been extremely influential.

On top of that, other than the syntax and commenting issues, each feature also exists for a good reason and has important uses in the right context, so it's not immediately clear to someone what a disaster combining them might be.

## References

Since we clearly need *more reading* after all that, here are some references to the languages discussed above...

 * **Algol 68**:  [ALGOL 68](https://en.wikipedia.org/wiki/ALGOL_68)
 * **APL**:  [The APL Programming Language Source Code](http://www.computerhistory.org/atchm/the-apl-programming-language-source-code/)
 * **C**:  [HowStuffWorks "The Basics of C Programming"](http://www.howstuffworks.com/c.htm) and [The International Obfuscated C Code Contest](http://ioccc.org/)
 * **FORTH**:  [Forth Interest Group Home Page](http://www.forth.org/)
 * **FORTRAN**:  [Fortran](https://en.wikipedia.org/wiki/Fortran), [FORTRAN I](http://www.paulgraham.com/history.html), and [FORTRAN IV Reference Page](http://www.math-cs.gordon.edu/courses/cs323/FORTRAN/fortran.html)
 * **INTERCAL**:  [The INTERCAL Programming Language Revised Reference Manual](http://www.muppetlabs.com/~breadbox/intercal-man/)
 * **Java**:  [Oracle Technology Network for Java Developers](http://www.oracle.com/technetwork/java)
 * **make**:  [Simple Makefile Tutorial](http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)
 * **PL/I**:  [PL/I](https://en.wikipedia.org/wiki/PL/I) and [What is PL/I?](http://members.dodo.com.au/~robin51/pliwhat.htm)
 * **Python**:  [Welcome to Python.org](https://www.python.org/)
 * **Ruby**:  [ruby-lang](https://www.ruby-lang.org)
 * **SNOBOL**:  [SNOBOL4 Resources](http://www.snobol4.org/)

I don't envy the person motivated to pull all of this into a coherent language specification.  Don't be a hero, kid...

#### <i class="fab fa-quora"></i>

* * *

**Credits**:  The header image is [Sisyphus, Copper Engraving](https://commons.wikimedia.org/wiki/Category:Sisyphus#/media/File:Friedrich_John_nach_Matth%C3%A4us_Loder_Sisyphus_ubs_G_0825_II.jpg) by John Freidrich, in the public domain.
