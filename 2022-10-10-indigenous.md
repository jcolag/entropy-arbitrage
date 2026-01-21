---
layout: post
title: Developer Journal, Indigenous Peoples' Day
date: 2022-10-10 06:48:05-0400
categories:
tags: [programming, project, devjournal]
labels: [globe, javascript]
summary: Progress on assorted projects
thumbnail: /blog/assets/New-Mexico-Indigenous-Peoples-Day-2019-03.png
offset: -18%
proofed: true
---

* Ignore for ToC
{:toc}

Because *please don't even get me started on Columbus*, the obnoxious, talentless kid, picked last in the national hero game on the world's playground, today, we celebrate [Indigenous Peoples' Day](https://en.wikipedia.org/wiki/Indigenous_Peoples%27_Day) in the United States...at least, in the parts of the United States who feel embarrassed represented by an "explorer" with a terrible sense of direction and such a murderous rampage that even European royalty put him in prison.  If you find "well, we'll celebrate his victims, instead" feeling uncomfortable, I also think that [Nanomonestotse](https://en.wikipedia.org/wiki/Nanomonestotse)---an autumn celebration of peace---and [World Mental Health Day](https://en.wikipedia.org/wiki/World_Mental_Health_Day) might deserve some attention, too.

![A celebration of Indigenous Peoples' Day, including people in a circle, watching a dance](/blog/assets/New-Mexico-Indigenous-Peoples-Day-2019-03.png "If white people had participated in this in the '90s, I can promise that they'd all go home focused on the grass-less circle and arguing about crop circles...")

On a personal note, I should say that, maybe if Americans had spent more time legitimately celebrating native cultures, I wouldn't have gotten stuck an endless sequence of cringe-inducing "authentic" ceremonies conducted and with exclusive participation by rich white people. 😬

And on a medium scale, I'd also like to wish a happy Thanksgiving to Canadian readers, and a happy Sukkot to Jewish readers.

And from there, we lurch into software as if we can see any relationship between the two.

## G.L.O.B.E.

{% github jcolag/g-l-o-b-e %}

You---yes, *you*---can now [play **G.L.O.B.E.**](https://jcolag.github.io/g-l-o-b-e/) in Chinese, Croatian, Dutch, English, French, German, Italian, Japanese, Korean, Persian, Portuguese, and Spanish.  The configuration panel has a drop-down list with those languages, which trigger a restart, much like the game-selection options.

The country data that I had already had translations into those languages, and I added a separate translation file for the user interface.  Note that the game *can* work in Breton, as well as the dozen languages listed above---each country has its name translated---but I couldn't find any service that would translate the user interface text.

Note that the game handles the localization in the most boring and least flexible way possible.  I looked at about a dozen libraries, hoping to not need to maintain this sort of infrastructure code, but they all had significantly different priorities to me.  Most of them want to install a library module, which I always have trouble with in a straightforward "serverless" web application; they generally require something like [webpack](https://webpack.js.org/), which increases the maintenance overhead.  Of those that remain, most take up a *lot* of space, with one dismissing this criticism on the basis that other software also takes up a lot of bandwidth, and---apparently secondarily---they designed this for large production systems, where they believe that size makes less of a difference.  Of the remaining libraries, most focus more on dynamically generating text and providing templates, rather than managing static strings.

Therefore, I gave up and, since the game doesn't need to worry about verb conjugations or plurals, it can get away with straightforward replacements of the "inner HTML" property of the relevant controls.  I wrote this to handle it.

```javascript
function translate(l) {
  const xlat = languages[l];

  Object.keys(xlat).forEach((k) => {
    const widget = document.getElementById(k);

    if (widget === null) {
      return;
    }

    widget.innerHTML = xlat[k];
  });
}
```

For each key in the language's translation object, find the HTML element with that ID, and if it exists, replace the element's `innerHTML` property with the supplied translation.  For small projects like this, it takes almost no time to update the entire page.  Add the error messages to the object, and this takes care of the entire process without much code.

I assume that some of these translations would fail miserably with even remedial speakers, if only because I seriously doubt that anybody put much planning into making sure that someone could copy-and-paste bidirectional text into a file and propagate it programmatically to HTML.  But the game has *something* to work from, and I'd happily look at pull requests from people who know better.

After all that, it seems far less interesting to mention cleaning up the configuration button and page, to improve readability on the page, but that happened, too.

## Next

Now that **G.L.O.B.E.** has translations, it seems silly to make everyone calculate distance in miles, so I may add another option.  I would also like to return to the idea of turning [**CPREP**](https://github.com/jcolag/background-generator) into a standalone web application like this.

* * *

**Credits**:  The header image borrows from [New Mexico Indigenous Peoples' Day 2019](https://twitter.com/RepDebHaaland/status/1183894892214398977) by [Deb Haaland](https://twitter.com/RepDebHaaland), in the public domain as the work of an employee of the United States government, Representative from the state of New Mexico, in Haaland's case.
