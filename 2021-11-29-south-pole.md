---
layout: post
title: Developer Journal, Byrd Antarctic Expedition
date: 2021-11-29 06:42:03-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Bundesarchiv-Bild-102-09158-Expeditionsschiff-Byrds.png
proofed: true
---

* Ignore for ToC
{:toc}

Again, this time of year is short on holidays, due to people being busy with the bigger days of the year.  So, maybe slightly late, depending on how you count them, yesterday or today marks the ninety-second anniversary of the launch of [Richard Evelyn Byrd](https://en.wikipedia.org/wiki/Richard_E._Byrd)'s first Antarctic expedition.

![The Byrd expedition ship in heavy pack ice of the South Pole](/blog/assets/Bundesarchiv-Bild-102-09158-Expeditionsschiff-Byrds.png "Watch out for that icy patch.")

Let's go get trapped in whatever the code equivalent of pack-ice is...

## Ask INTERN

It took [asking a question on Stack Overflow](https://stackoverflow.com/q/70085210/3438854), but [**Ask INTERN**](https://github.com/jcolag/ask-intern) now uses **INTERN**'s configuration file, so that the two programs can share the communications port number.  Opening and parsing the configuration file more than doubles the length of the small program, but that's more a testament to how concise the language is for the rest of the program.

Parsing JSON with the [Poison](https://hexdocs.pm/poison/Poison.html) library is easy enough, but the current version of the library doesn't work on Ubuntu's default version of Elixir.  So, I needed to install and set up the horribly named [Asdf](https://asdf-vm.com/), which allows for different projects to use different versions of the infrastructure.

The other key to this change---provided in the answer to the aforementioned question---is the following line.

```elixir
:filename.basedir(:user_config, "intern")
```

The [`:filename.basedir()`](https://www.erlang.org/doc/man/filename.html#basedir-2) function retrieves one of a number of default paths for the current user---`:user_config` in this case, for the user's configuration directory---for the `intern` application.

## INTERN

While updating **Ask INTERN**, it only seemed reasonable to update [**INTERN**](https://github.com/jcolag/intern) to also take the server IP address and port from the now-common configuration file.

I don't know if it's a new version or just code updates that I didn't pay much attention to, but Clippy had some complaints, so most of them are fixed.  I left the unused reference, the complaints about functions with too many parameters, and the issue that causes an error when I fix it.  The last one will require some investigation to get rid of the underlying error.  The rest will mostly just take time.

In addition, the documentation should now reflect everything that the project currently needs to run, and reports errors a bit more cleanly.

## Entropy Arbitrage

For an upcoming small project, [this blog](https://github.com/jcolag/entropy-arbitrage-code) needed a new feature, specifically to create a plugin that will display a block of text in a font that looks hand-written.  An example follows.

{% hand %}
While I won't generally use it for routine text like this paragraph, there are narrow cases where I personally think that it's far easier to convey a particular mood with cursive writing.
{% endhand %}

To make that work, I just have a `hand`/`endhand` tag handled by a plugin.

## Next

Time permitting, I should put more work into **INTERN**.  While it currently handles the bare minimum of what I want---the server maintains a searchable index of most of my working files---I could certainly improve the output.  Many of the files, such as these blog posts, my [**Miniboost**](https://github.com/jcolag/Miniboost) notes, and others, have a formal title that I could display as a clue for which file has a better chance of having what I want.

Likewise, it might be excessive in terms of the size of the index, but it *could* be worth pulling my browser history and indexing the contents at each URL.  Such a thing could be scheduled overnight and spaced out over hours, so that it doesn't slow down my computer.

It might also be nice to make it easier to *open* the files.  Whether it's from **Ask INTERN**'s interface or a separate command, that may require changes especially to **Miniboost** to auto-open a specific note.

Of course, I may decide to do something entirely different, too.

* * *

**Credits**:  The header image is the [Byrd's South Pole expedition in the pack ice](https://en.wikipedia.org/wiki/File:Bundesarchiv_Bild_102-09158,_Expeditionsschiff_Byrds.jpg) by an unknown photographer, made available by the [German Federal Archive](http://www.bundesarchiv.de/) under the terms of the [Creative Commons Attribution Share-Alike 3.0 Germany](https://creativecommons.org/licenses/by-sa/3.0/de/deed.en) license.
