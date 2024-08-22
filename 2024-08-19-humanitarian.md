---
layout: post
title: Developer Diary, World Humanitarian Day
date: 2024-08-19 08:10:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/2995064256_853fd34d7c_o.png
offset: -8%
teaser: This week's projects include yet more updates to the blog, the (probably) last Fictopedia update for a while, and...toys?
spell: fictopedia MathJax Tootpick lightnesses img em es OpenSCAD Tri-L-One Superflu Harneis
proofed: true
---

* Ignore for ToC
{:toc}

Today, we recognize humanitarian personnel and those who have died working for humanitarian causes in [World Humanitarian Day](https://en.wikipedia.org/wiki/World_Humanitarian_Day).  Given the ways that anti-democratic, anti-rights forces have started acting like cornered animals over the last few years, lashing out at anyone they can, I can only expect that we'll need to talk more about the holiday in future years, unfortunately.

![Workers passing out nutritional supplements](/blog/assets/2995064256_853fd34d7c_o.png "Not the point, but I've often wondered why NGOs didn't sell the sorts of foods depicted, both to subsidize the projects and because low-income people everywhere could presumably benefit as well")

And on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Once again, I may have gone overboard, so I have a lot to talk about, here, some of which continues where [last week's developer diary post]({% post_url 2024-08-12-elephant %}) left off, and others felt like good opportunities along the way.

For the people itching to start skimming until you get to the toys---yes, *actual* toys---we have icons on the code snippets, a cleaner search page, assistance sharing a post to Mastodon, and an actual dark mode.

### Code Icons

As you'll see shortly in this post---and OK, last week's post, too---I took what I learned about annotating the outbound links with icons, and adapted it to making it easier to identify which programming language I want to present in a given situation.  For reference, so that you can follow how it works, the HTML produced by Jekyll for a code block looks like this.

```HTML
<div class="language-whatever highlighter-rouge">
  <div class="highlight">
    <pre class="highlight line-numbers language-whatever" tabindex="0">
      <code class="language-whatever">
        ...some code for me to present...
        <span aria-hidden="true" class="line-numbers-rows">
          <span></span>
        </span>
      </code>
    </pre>
  </div>
</div>
```

Briefly, and ignoring the line numbers, this wraps the `code` block element (containing the code itself) in a `pre` (pre-formatted) element, then by two containers.  The outer container, the pre-formatted container, and the code all get the class that names the programming language.  I want the `pre` element to show the icon, though other levels would probably also work.  As I've mentioned previously, [Prism.js](https://prismjs.com/) also uses those class names to highlight the code, but Jekyll places them based on how I annotate the code blocks in the Markdown source for the post.

Anyway, I mostly went through the same process as for the hyperlinks, setting up a default rule for "generic" code, then a series of language-specific rules to override the icon.

```CSS
pre {
  position: relative;
}
pre::after {
  content: '\eef7';
  font-family: 'Simple Icons';
  font-size: 3em;
  opacity: 0.25;
  position: absolute;
  right: 0.5em;
  top: 50%;
  transform: translateY(-50%);
}
pre.language-CSS::after {
  content: '\ec90';
}
```

Because I don't want short snippets of code to look sloppy, I want to vertically center the icon.  That means setting the container's `position` attribute to `relative`---which I imagine some part of the specification explains with some clarity, even though it always feels like a superstitious ritual that happens to work---so that the browser will accept the icon's position as `absolute`.  By default, code gets a generic <i class="fa fa-code"></i> code symbol, whereas languages with icons that I can access or can borrow some standard image to represent it get that icon, instead.

### Search

After the first few months publishing blog posts, I started to notice a minor irritation that I decided to live with instead of fixing, until now.  Because the "search index" looks suspiciously like a JSON file with the contents of every blog post shoved into it, it can take a while for [the search page](/blog/search) to finish loading, and it'll get longer as I write more.  When everything finishes, this makes searching effectively instantaneous, because the page already knows everything about the site.  However, the "signal" that the index hasn't loaded looks suspiciously like nothing happening when you try to search.

As I mentioned, I ignored the problem for years, figuring that nobody used the search except me.  It didn't really matter, I told myself, even though the problem gets slightly worse every week, since I knew enough to wait for the page to finish loading and everybody else probably uses a real search engine that can handle a `site:john.colagioia.net` operation or some equivalent, assuming that anybody besides me every searches the site at all.  Seriously, I can't remember ever seeing the search page show up in the analytics.

However, all the recent work with icon fonts reminded me of one of [Font Awesome](https://fontawesome.com/)'s bigger reasons for wide adoption had to do with "spinner" icons.  In text, it seems silly to call up an `fa-spinner` icon <i class="fas fa-spinner"></i> then apply the `fa-spin` class to it <i class="fas fa-spinner fa-spin"></i>, but on a slow-loading page, I can drop something similar on a full-screen `div` element that vanishes on loading, to produce the standard loading screen.

And the search can't work without JavaScript enabled---it literally searches the aforementioned huge JSON object---so it doesn't matter that I add JavaScript to the one page to hide that loading screen[^3].

[^3]:  Yes, every post has some JavaScript, but it only enhances the page---[MathJax](https://www.mathjax.org/), [Chart.js](https://www.chartjs.org/), the aforementioned Prism.js, and the like---rather than anything that you *need* in order to read the post.  The charts probably don't degrade gracefully, but I also don't use them often.

### Picking Toots

While I try to improve everything else, I decided to see what it looked like to help readers share a post to the Fediverse, these days.  As you probably know, most social media sites have a URL where you can send the text of a post as parameters, leading to a page where the user doesn't need to do anything more than press the button to publish, assuming that they've logged in.  Most Fediverse services have something like this, but because users publish on different servers (instances), you can't know where to send the user without a bit more help.

After a couple of false starts---code that outright didn't work, or which required me to write so much integration code that I could have done the rest of the job myself---I ran across [Tootpick](https://github.com/Juerd/tootpick), an all-in-one-file project that solicits your server name and forwards you to the instance's "share" page, filled in with post information for you to edit and send off.

If you don't want to type your instance every time, then *Remember* will stash it in your browser's local storage, and generate image-buttons that you can click on in the future, for as many servers as you might want to use.  As a result, neither Tootpick nor I know anything about your identity...until you post the message, I mean, at which point I'll have a small clue about the person who mentions me and posts a link to the blog.  But that clue has nothing to do with the method that you used to post.

Because it felt silly to send you to a page that then sends you to your Mastodon instance, I opted to host the thing in an `iframe` element at the bottom of each post, instead.  Then, to open the instance in a new window and to make it match the rest of the blog, I opted to run a local copy so that I could modify things superficially, instead of using [Tootpick's website](https://tootpick.org/) directly.

I assume that readers won't share posts often.  But I wanted to make it less onerous, in case somebody did want to share the posts, *and* it makes a good excuse to highlight a decent project if anybody wanted to do something similar for their site.

Related to the likely low frequency of use, I wish that it took up less space, but I suppose that the features do require the space, unless I want to play games with multiple "hops" to get to your server or squeeze out the preview of the text.  Also, I wish that it could handle more of the Fediverse, but I suppose that has more to do with everybody having a different API than anything else.

### Dark Mode, Finally...

Much like many of the other recent changes around here, I've wanted to implement a dark mode on the blog since fairly early on, if only to save myself some eye strain as we coast into winter.  As I've probably written about before, I run scripts that flip my computer to dark mode at sundown and back to light mode when I wake up, because I want the colors to match the ambient light, not some contrived image of what a "good programmer" would look at all day.  This means that I have a few months every year when working on my own blog after around five o'clock feels uncomfortable, because everything on the screen goes dark except the yellow page.

I usually assume that people know these things if they read these posts, but on the chance that you don't and if you run Firefox (or a derivative), then you can swap between light and dark mode in the developer tools.  Select the <i class="fas fa-bars"></i> hamburger menu, *More Tools*, and *Web Developer Tools*, then select the *Inspector* tab.  One of the panels will have little Sun and Moon icon buttons that you can click to switch the color scheme.  Don't panic if you see parts of the page flash as you move the mouse; the *Inspector* lets you poke at the HTML.

I won't retread the `light-dark()` function that I used to make this work, because I did that in more depth in [*Yet Another Dark Mode Post*]({% post_url 2024-08-14-dark-mode-again %}) on Wednesday.  Instead, I want to talk about the changes that I made to support this bigger change.

First, I swapped the background and text hues for dark mode.  I initially only changed the lightnesses of the colors---subtracted each lightness from one hundred---and discovered that I didn't care for bright blue text on a muddy "mustard" brown background.  As a result, we have the yellowish text on a dark blue background, which I think fits together better.  The light mode continues to use the same colors.

Second, because I can't set *images* to "dark mode"---I mean, I could probably select a secondary dark image for every other image, but that feels like pathological behavior that I don't feel like engaging in---I use a CSS filter to darken and desaturate them in dark mode.

```CSS
@media(prefers-color-scheme: dark) {
  article img {
    filter: saturate(0.3) brightness(0.5);
    transition: all 1s;
  }
  article img:hover {
    filter: none;
  }
}
```

Hovering over the image removes the filter, in case the image carries useful content or looks interesting, but you have control over it, rather than pushing the full brightness and color into your eyes.  I've actually used the same trick for myself in my RSS feed reader for at least a decade, partly for reading after dark, but there, it has the unexpected benefit that it makes it easier to ignore the unending photographs of obnoxious politicians and others frothing at the mouth for the cameras, since I've had my fill of people like that...

## Fictopedia Archive

{% codeberg jcolag/fictopedia %}

While the main project has (finally) finished until somebody finds more to do, I needed to update the documentation, which I admit feels like an overblown euphemism for the `README` file.

Regardless, the introduction of the file now points to [the deployed website](https://jcolag.codeberg.page/fictopedia/), so that people can...you know, *find* it.

I also added an overview of the work left to do and how to contribute help, in case people find the project through that route.

## Codeberg Pages for Me

{% codeberg jcolag/pages %}

I have no idea how to refer to this repository, as you can guess by my *spectacular* title for this section.  But Codeberg has a pre-defined `pages` repository for every user that, if you create it and fill it with HTML, it publishes the HTML files to the root of the Codeberg Pages site, sort of like GitHub's profile repository.

I created the repository back in the winter, I think, and then forgot about it.  This week, I added a [relatively bare profile](https://jcolag.codeberg.page/) with pointers to this website and the repositories that I have on Codeberg.  I generated the page from Markdown, which I also included in the repository, so that I don't lose track of it.

## The Light's Edge (Toys)

{% codeberg jcolag/lights-edge-toys %}

Everybody, I'd like you all to meet LLL-1.  You can also meet the random chunk of obsidian that I've had decorating a shelf since the '90s, since I wanted something else in the pictures for contrast.  I also used some insulated foil bubble wrap as the back wall, and a patch of felt for the floor.

![The LLL-1 action figure approaching a polished pseudo-monolith](/blog/assets/lights-edge-lll-1-a.png "Curious...")

Fear not, I doubt that the "character" will ever actually appear in **The Light's Edge**.  Rather, I use em[^1] as my "proof of concept" for developing the toys that I envision for this.  Standing at around 3¾ inches/9½ cm tall, e fits the target scale with five points of articulation and minimal assembly (yes, I used electrical tape for this version), meaning that I can use em to sit in seats of prototype vehicles or use em to judge the sizes of future characters and props.  I hope that explains why e looks more like a 1950s Hollywood robot prop than an actual character.

[^1]:  Early in the blog's life, talking about allyship, performative identities, and other related issues---not always in the best ways, I should say, and corrected myself later---I did some research on gender-neutral pronouns for [*We Are What We Do*]({% post_url 2020-03-08-are-do %}), and have decided that LLL-1 uses e/em/es pronouns.  I hate for good words to go to waste.

![Closer in on the LLL-1 action figure](/blog/assets/lights-edge-lll-1-b.png "Pondering the investigation...and yes, I put a tiny nose on the head so that it could have a front")

I did all the development in [OpenSCAD](https://openscad.org/), using it to create the model that you can find in the linked repository, with some pieces left out of the print because I didn't feel like assembling half-limbs.  E still has a way to go, since the pegs holding es arms in place don't fit the curvature of the torso, explaining why you can see that large gap across the shoulders, but as a *trial*---three *L*s in the name, Tri-L-One...?---I can change the shape of the torso to something more plausible, and build on the stick-limbs with more sophisticated arm and leg models later.

Why do this from scratch instead of using another Free-licensed model?  In short, I looked for action figures under an appropriate license that might do the job, and problems ranged from the figure [not working at small scales](https://www.thingiverse.com/thing:2887306), requiring [extra materials for assembly](https://www.thingiverse.com/thing:701051), [overcomplicated everything](https://www.thingiverse.com/thing:116571), or [had a weird shape](https://pinshape.com/items/15692-3d-printed-action-figure-open-source-snaps-together-prints-without-su) that wouldn't work as representative of a humanoid character.  One [seemed nice](https://sketchfab.com/3d-models/pilot-mechanic-action-figure-118-7fa66eb1cae04665b1e0becb2640d8b7), but the printer mostly created a mound of plastic when I tried to get a physical version.  Plus, this way gave me the excuse to finally learn OpenSCAD.

In this case, the arms and legs swing as I'd expect, and other than a clear lack of resemblance to the human form, looks decent for a first attempt at toy-making; child-me probably would have accepted LLL-1 into my collection, especially earlier on when it matched the scale of other common action figure lines[^2].  And no, the paper "figurines" that I cut out while talking about [diversifying the "business" of Free Culture]({% post_url 2024-01-14-diversify %}) don't count as prior attempts at making toys.  I still have them, though, and somebody will want to know that Superflu comes up to LLL-1's waist, so you'd probably need to double the size of everything on that page to scale it to fit, here.

[^2]:  In fact, I picked the 1:18 scale partly because it means that the characters should fit with [a certain famous toy line](https://en.wikipedia.org/wiki/Kenner_Star_Wars_action_figures)---a toy line that helped inspire a lot of how I imagine getting people interested in **The Light's Edge**---and also because I know from experience that the size turns a lot of household junk into dramatic-looking parts of toys...which I'll illustrate as I run out of things and have their packaging to display.

In the spirit of full disclosure for other people learning to use new tools, I should note that LLL-1 actually makes the first *viable* trial, suitable for getting limbs and a head.  Four prior attempts at printing a torso didn't leave enough space for the leg-pegs, and I also needed to experiment with the peg diameters.  This project *definitely* didn't go right the first time.  I kept the pieces, so maybe I'll write a full post on that evolution, at some point.

## Next

I *think* that I've exhausted the little things that I've wanted to do for the blog---at least for a while---so I'll probably clean up some smaller items and then head back to some of the many projects that I've neglected recently.

And expect to see LLL-1 and es successors---I feel like an egg-shaped torso might work better than cylindrical, for example---featured in future developer diary posts, modeling other toys for **The Light's Edge**.

* * *

**Credits**:  The header image is [Distributing high energy biscuits](https://www.flickr.com/photos/julien_harneis/2995064256/) by [Julien Harneis](https://www.flickr.com/photos/julien_harneis/), made available under the terms of the [Creative Commons Attribution Share-Alike](https://creativecommons.org/licenses/by-sa/2.0/) license.
