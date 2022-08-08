---
layout: post
title: Developer Journal, Indigenous Peoples Day
date: 2022-08-08 06:59:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Hornbill-Festival.png
offset: -20%
proofed: true
---

Today, we observe the [International Day of the World's Indigenous Peoples](https://en.wikipedia.org/wiki/International_Day_of_the_World%27s_Indigenous_Peoples).  While it originally revolved around awareness and the protection of native rights, it has increasingly shifted towards environmental preservation as indigenous populations have increasingly taken such roles.

![Naga people engaging in their Hornbill Festival](/blog/assets/Hornbill-Festival.png "")

On to the week's programming.

## G.L.O.B.E.

{% github jcolag/g-l-o-b-e %}

In the spirit of [**Mystic T-Square**](https://jcolag.github.io/mystic-t-square/) moving to hosting through GitHub Pages---in other words, making it a standalone page that can run every possible game---I decided to try the same for **G.L.O.B.E.**.  I always half-intended to do this, as you can probably guess.

While I don't mind generating the pages overnight, archiving them indefinitely doesn't accomplish much more than waste space, when the only difference between nightly files---from the perspective of the information that each conveys---doesn't extend beyond identifying the target country.

Most of the changes feel straightforward enough to not require comment, and you can skip all of it and [play the game](https://jcolag.github.io/g-l-o-b-e).  Most of it only required "rephrasing" code that generated something into code that initialized something analogous.  However, I did find a few points that required more significant work.

### Reading the Country Data

The original code embeds the countries in each file, which I don't consider *terrible*---the code needs to access it, to report on wrong guesses---but the file *does* contain more than 300 kilobytes of data, embedded into every day's game.  I could continue that, but if I want to generate things, I figure that I might as well keep the main page as "clean" as possible and move all the work to JavaScript.

Actually doing that proved the first wrinkle.  Reading local files in Node.js handles roughly as I'd expect, and I've used that API frequently, but browser-based JavaScript requires the [`fetch` API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).  Well, it requires that, then it requires dealing with the resulting `Promise`, which requires dealing with a second `Promise`.

```JavaScript
window.addEventListener('load', (e) => {
  fetch('./countries.json')
    .then(readJson);
});

function readJson(response) {
  response.arrayBuffer()
    .then(startGame);
}

function startGame(jsonBytes) {
  const decoder = new TextDecoder('utf-8');
  const json = decoder.decode(jsonBytes);
  countries = JSON.parse(json);
  // Three functions after loading the page, we *finally*
  // have the list of countries to work with.
}
```

The first `Promise` object semi-helpfully provides that `.arrayBuffer()` method, which (unsurprisingly) returns an [`ArrayBuffer`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)...but only through another `Promise`.  Handling *that* `Promise` provides a byte array, which we then need to decode into a string.  And then we can parse that string into an object for further use.

### Randomization

The core of the daily game, you probably realize, involves picking a random country for the day, from among the available countries.  For generating a static game, they couldn't make it easier.  Call `Math.random()`, produce the page, and everybody sees the same page until I replace it.  By contrast, if the game did that on initialization instead of generation, you wouldn't see the same game as me.  You wouldn't see the same game now as you would see one microsecond into the future, for that matter.

Client-side randomization doesn't give us anything consistent to latch onto.  In most cases, you solve that kind of problem by "seeding" the random number generator.  We actually call the generators "pseudo-random number generators," because they calculate each next number based on its history.  That doesn't quite qualify as random, but if you use the generated sequence sparingly and pick unlikely starting states (the "seed"), it becomes difficult to know the difference.

Unfortunately, we can't seed JavaScript's native random numbers.  If we want seeds, then we need to build our own generator.  You'll find the code that interested me in this [Stack Overflow answer about exactly this issue](https://stackoverflow.com/a/47593316/3438854), where someone neatly outlined generating the seed and several pseudo-random sequence generators.  I picked one and replaced `Math.random()` in the code without any fuss.  Using the date to generate the seed, the game now persistently shows the same page to everybody, every day.

### Archives

At this point in the story, the game builds a bespoke puzzle for the current date.  I maintain my [archive of old puzzles](/globe/archive.html), though, so you can probably guess that I don't *only* want a daily puzzle.  I like to also provide a way for someone to access the days that they've missed.  The most straightforward way to do this, you can probably guess, involves using the URL's query string.

I can figure out a decent user interface later, but I "only" need to test with `index.html?date=2022-08-07` or whatnot, to pull off a given date...well, *except* that JavaScript doesn't do that naturally, for some reason.  I need another utility function.

```JavaScript
function params() {
  var p = {};
  var parts = window.location.href
    .replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m,k,v) {
      p[k] = v;
    });
  return p;
}
```

The `.replace()` method can do some interesting things, including matching candidates based on a regular expression and calling a function for every match in the original string.  Often, I use that to make more sophisticated replacements that might require calculation or lookup.  In this case, though, that function builds and object that we can use as a hash table, mapping keys to values.  Then, I grab the date and declare victory. 🍾

...Well, all that works, *except* that it makes "strange" decisions about what day it actually found.  I happened to have tested this later in the evening, which I appreciate, because I otherwise wouldn't have caught the difference between "get today's date" and "what date did you parse?"  The solution, here, involves reversing the time zone's offset, conveniently provided in minutes.

```JavaScript
if (Math.abs(Date.now() - when.valueOf()) > 10000) {
  when = new Date(when.setMinutes(when.getTimezoneOffset()));
}
```

Basically, I compare the date/time that we've figured out to the current time.  If the difference between the two comes out to more than ten seconds---an eternity, if we actually plan to use the current date---then I replace the minutes in the time with the number of minutes difference between "here" and GMT.  That gets us (unless I missed something) to the correct date, because it rolls us over at local time.

## Iungimoji

{% github jcolag/iungimoji %}

Emboldened by the success with **G.L.O.B.E.** described above, I decided to start the same process for **Iungimoji**.  I won't talk about that as much, because it'll largely take the same work:  Creating a shell, converting generation to initialization, reading an external data file, replacing the random number generator, and handling the URL's query to choose dates and now sizes.

It requires slightly *more* than that, though, because this game involves more than one random choice.  But I haven't gotten there, yet.  "Watch this space," as they say.

## Next

I need to finish the work on **Iungimoji**, naturally.  And as mentioned earlier, the date selection needs a user interface.  While I do that---it'll surely require a configuration screen, like the modal panels on **Mystic T-Square**---I might as well add language configuration for **G.L.O.B.E.** and default size for **Iungimoji**.

Time permitting, I'd like to go through this same general process for [**CPREP**](https://github.com/jcolag/background-generator), so that I can stop worrying about that [Express](https://expressjs.com/), which doesn't add anything to the project.  It has a similar profile of a single page generated based on external data.

* * *

**Credits**:  The header image is [Hornbill Festival](https://commons.wikimedia.org/wiki/File:Hornbill_Festival.jpg) by [Dhrubazaanphotography](https://commons.wikimedia.org/w/index.php?title=User:Dhrubazaanphotography&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
