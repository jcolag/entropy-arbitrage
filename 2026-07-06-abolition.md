---
layout: post
title: Developer Diary, Abolition Commemoration Day
date: 2026-07-06 07:34:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [artificial-intelligence, blog, library-update, recipe, social-media, scrawls]
summary: Progress on assorted projects
thumbnail: /blog/assets/corinthian-hall-interior-1860.png
offset: -26%
description: This week's projects include finding myself In the Weights, a recipe, my Scrawls editor, and the blog's code.
spell: miso koji KIMI Goodfellas endcook frico Uxuyu
proofed: true
---

* Ignore for ToC
{:toc}

Reviving the former Emancipation Day/[Fifth of July](https://en.wikipedia.org/wiki/Fifth_of_July_%28New_York%29), New York celebrates the first Monday of the month as Abolition Commemoration Day, marking the state's 1827 abolition of slavery.  While the state declared Emancipation Day to coincide with the country's Independence Day on the fourth, fears about violence from white people---legitimate, given that anti-abolitionist riots would rip New York City apart about seven years later---convinced many Black people to celebrate a day later.

[**What to the Slave Is the Fourth of July?**](https://en.wikipedia.org/wiki/What_to_the_Slave_Is_the_Fourth_of_July%3F) comes out of such a celebration.  In fact, let's listen.

<iframe
  allowfullscreen=""
  frameborder="0"
  height="45"
  mozallowfullscreen="true"
  src="https://archive.org/embed/nonfiction037_1503_librivox/snf037_whattotheslavejulyfourth_douglass_pga_128kb.mp3"
  webkitallowfullscreen="true"
  width="740"
>
</iframe>

Why celebrate a holiday *not* listening to the words of Frederick Douglass when we have that option, right?  If you don't have an hour, increase the playback speed.  The reader speaks deliberately enough that you probably won't lose too much until it goes by too fast for you to process.

![The approximate-period interior of Corinthian Hall in Rochester, NY](/blog/assets/corinthian-hall-interior-1860.png "I would hope that this gives a better sense of what it might have looked like to watch Douglass speak")

And with that, on to the week's projects.

## Social Media

...OK, but not really.  Any other label that I smack on this would sound like a new project, and I guess that "new" does qualify, but I had nothing to do with it.

Apparently, you can find me [in the weights](https://intheweights.com/p/john-colagioia)---as nobody but this website says---that LLMs have apparently scraped enough of my work to put me in the top-ten-percent of people who the various models claim to "know" about.

![My assessment from In the Weights, identifying me as a software developer and blogger, with some numerical data](/blog/assets/in-the-weights-jc.png "Honestly, I worry less about LLMs training on my posts than most people might, because it introduces the possibility of laundering my weirdest ideas to an audience already receptive to buying anything. It may not improve the world, but it might make it a bit weirder...")

As I check through the different "reports," I notice that they get further afield.  Normal-GPT guessed right, but mini-GPT introduces the idea of "community work."  Grok recognizes me from the Perl community, while Gemini knows that I worked on the GIMP.  KIMI (never heard of it; don't care) knows my similarly imaginary programming-based USENET posts.  DeepSeek claims that I created the Bitwise language, and GLM makes me a BSD developer.

The three "hallucinations"---I hate the term; the auto-complete guessed nonsense---make me a conspiracy theorist (I suppose not *entirely* inaccurate), former soldier, a political science professor in Harrisburg (Pennsylvania), and a prominent actor in **The Godfather** and **Goodfellas**.

I don't know.  It seemed worth mentioning, and the tool does a decent job of illustrating that these companies waste all these resources on scraping all human output, but uses them in the silliest way possible.  Presumably, someone wanted to know that it exists.

## Recipes

I have a long story, here, because I don't really have the vocabulary for the intermediate step.  Try to stick with it, at least skim, if this sort of thing generally interests you.

Back when I had late nights teaching, if I needed to eat, I got into the habit of making a grilled cheese sandwich.  Makes sense so far, right?  Well, at one point, I didn't have bread handy and had a bizarre idea:  I could toast rolled oats in the pan, as if making a (boring without the fruit, nuts, or sugar, and lacking cohesion without sugar) granola, and add shredded cheese to that, like a slice of bread.  You could think of it like granola, but with cheese replacing the sugar.  Or you could think of it like nachos, but with toasted oats instead of tortilla chips.

Yeah, I invented some horror-flick cross between granola and nachos.

Over time, that became a regular part of my breakfast rotation, adding seeds or chopped nuts to the oats, along with spices.  A couple of tablespoons of cheese get mixed in with the toasted oats to get them to bind together, then a layer or two of cheese goes into the bowl alternating with the oat mixture.  I find it filling and almost always good, so it feels like it either *shouldn't* work or that people have made it for centuries, but not neither.

I didn't come here to provide that recipe, though.  No, instead I mention it as the aforementioned "intermediate step" to explain my motivation, here.  As you might guess from the other sorts of recipes that I mention, I don't think of myself as vegan or vegetarian, but increasingly find myself pushing away from meat and meat products.  I rarely eat meat other than fish, these days, and when I start running out of ingredients, I start looking for alternatives, instead of automatically replacing what I have.

This week, I ran low on the shredded cheese that I mix in with the oats.  And I wondered if a convenient alternative existed that might pass muster, not necessarily an exact replacement for cheese---I have always hated every "health food" trying to pass itself off as something conventional, instead of leaning into the best aspects of the ingredients---but something that has that general flavor profile, and would (more importantly) serve to bind the oats so that I don't find myself trying to shovel individual flakes of oat.

Discarding the more classic cashew-based recipes, because they require soaking, and I didn't want to make this a production, I found a few possibilities with recurring ingredients.  They all have some non-dairy milk base (coconut seems popular), nutritional yeast (which I like a lot), some sort of starch, and a handful of spices, generally garlic powder, onion powder, salt, and smoked paprika.  One recipe called out using tapioca flour, because it sets with a stretchy feel resembling cheese.  As it turns out, I usually have most of that in my pantry, so I didn't need to do much shopping, and decided that it could benefit from an additional kick.

{% cook 1|Vegan Cheese Sauce %}
Bring @coconut milk{7%oz} to a boil.

Stir in @nutritional yeast{3%Tbsp}, @tapioca flour{2%Tbsp}, @white miso paste{½%tsp}, @onion powder{½%tsp}, @garlic powder{¼%tsp}, and @smoked paprika{¼%tsp}.

Simmer, low to medium heat, for ~{1%min}, stirring constantly.
{% endcook %}

I happened to have a couple of cans of coconut milk to pad out some online grocery order, and used about half of one can, freezing the rest for next time.  The "kick" that I mentioned comes from the white miso (replacing the salt), because (a) I bought a tub of it and (b) it tastes a *lot* like high-end Parmesan cheese.  It seems worth noting that I have had "brain fog" problems with soy, but also enjoy soy-based products a lot, so I try to limit my use.  Eventually, I'll probably buy koji and experiment with miso made from other beans, a story for another time, I suppose.

Now, as expected, nobody will mistake this for cheese, as in nobody would ever want to serve a sauce on crackers...although as it cools, it actually does have a similar texture, so maybe don't discount the idea.  Anyway, after toasting the oats, seeds, and spices (remember that part of the story?), I set them aside in a bowl and made the sauce in the same pan.  I stirred some in, then poured the rest---too much, because I can still *feel* it...---over the top with a sprinkling of smoked paprika.  It actually tastes significantly more like cheese than I would've expected, and while it doesn't/can't produce the crispy granola-like clusters that cheese "frico" does, the sauce does a more consistent job of holding the oats together, since I don't need to wait for anything to melt.

And this comes together in only a couple of minutes, which might mean that it exceeds my requirements.  I don't know if this will *replace* cheese in my diet, and it doesn't need to[^C49Nof], but the convenience---assuming that I remember to keep some non-dairy milk (and in theory, I could make oat milk), tapioca flour, and onion powder around as they run out---seems compelling for a lot of cases where I might've reached for cheese intended to melt anyway.  I'll definitely want to halve the recipe (or figure out how to store half) for future versions of the oat bowl, though.

[^C49Nof]:  On the other hand, if you follow the dominoes falling from the attacks on Iran to closing the Strait of Hormuz, and closing the Strait slashing available fertilizer supplies, the current and upcoming growing season(s) will need to choose between growing plants for human consumption and growing plants for animal feed to produce much less food.  By that measure, the possibility exists that decent dairy products become more difficult to source.

## Scrawls

{% codeberg jcolag/scrawls %}

Probably most important, here, the application has a `lib` endpoint, to serve library files however makes the most sense for the browser.  If the server has [Code Mirror v5](https://codemirror.net/5/) downloaded, this turns the default `textarea` element into a text editor with line numbers, syntax highlighting, and code-folding.

It also has a stub for saving the file, but I haven't connected it, since it actually only copies the code from the load-file handler.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

When I first put the blog together, I left thirty pixels of space at the top (and bottom) of every page.  In all likelihood, I *intended* for the heading/menu to stay in place at the top of the screen as the user scrolled, giving pages that "headroom" so that it could slide underneath the menu without cutting anything off.  As evidence, I point to the fact that the page layout has always mimicked exactly that behavior, except for the persistent menu itself:  The padding at the top mostly gets "eaten" by the menu, and without it, the page title smacks right into the bottom of the menu.

Now, my storytelling falls apart at this point, because I didn't leave any notes about the visions for specifics about the site layout unless they make it into a Monday post like this.  Maybe I couldn't figure out how to make it work---unlikely, given that a quick search turns up multiple approaches and always has---or forgot about it.  But as I look at how I'd do it today, a picture forms, in that the [`display: sticky`](https://caniuse.com/css-sticky) style did already exist at the end of 2019 when the blog launched, but with only partial support on Chrome, Edge, and Opera.  And while I don't always get it right (for which, see the various times that I overlooked Firefox <abbr title="extended support release">ESR</abbr> in adding something like the site's dark mode), I have spent over twenty years begging colleagues to test their web apps with a wider variety of web browsers.

And then you can see the story unfold normally from there.  Everybody got support for "sticky" headers by late 2021, but eighteen months after spending time on this, I had forgotten any plan that might have existed.

All that to say that, during the week, trying to think through how I want the menu to behave in the future, I realized that I had a few problems that I could solve all at once with a sticky header.  Therefore, I set the property and marvelled at how it looks like I planned to do that all along.

Oh, and one more---I hope invisible to anybody not using a screen reader---change on the core HTML work, the index pages now use a second-level heading element (`h2`) instead of third-level (`h3`), since the latter looks like somebody forgot the intervening heading between the big one at the top and the eight little ones.  Both headings should have identical styling on those pages, so (again) you shouldn't notice the difference without a screen reader, but I'd still consider it a significant improvement.

## Library Updates

I needed to bump library versions for [Library Twitter-bot](https://github.com/jcolag/library-twtterbot), my [Mastodon Tool Trunk](https://github.com/jcolag/tool-trunk), and [Uxuyu](https://github.com/jcolag/Uxuyu).  Granted, I would all but guarantee that the Twitter thing no longer exists, since I believe they wiped out the API long ago, but why *not* keep the libraries up to date, right?  Likewise, Uxuyu uses an unfinished and abandoned user interface framework, and I haven't touched Scuttlebutt in years, so I have no idea how well it works at this point.

## Next

I'd like to finish the code to save files in Scrawls.  I doubt that it'll take much effort, but have avoided it since I mostly test the editor on the repository, and I don't want to go through the hassle of corrupting the code.  Beyond that, I'd also like to set up a user interface to open files, and ideally opening them in "tabs."

Oh, and even as I describe it above, I may have to mess with the "sticky header," because apparently in 2026 we *still* haven't built a consistent way for page up/down to work.  Apologies to anybody who got caught in the half-baked version that went out (I believe only) yesterday.

And now that I have the menu always visible, I should also return to a [feature that I built]({% post_url 2024-12-23-ghent %}) a while ago and never hooked up to the interface.

* * *

**Credits**:  The header image seems [unnamed](https://www.libraryweb.org/rochimag/roads/map4.htm) with no credit to the artist, long in the public domain due to an expired copyright.
