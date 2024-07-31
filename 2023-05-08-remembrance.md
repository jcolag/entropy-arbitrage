---
layout: post
title: Developer Diary, WWII Remembrance
date: 2023-05-08 07:10:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/keitel-111-SC-206292.png
teaser: This week's projects include the blog's code and infrastructure, one of the scripts that manage my life, and my Mastodon Tool Trunk.
proofed: true
---

* Ignore for ToC
{:toc}

I apologize for mangling the name in the title, but the world generally sets aside today as the---take a deep breath for this one...---[Time of Remembrance and Reconciliation for Those Who Lost Their Lives during the Second World War](https://en.wikipedia.org/wiki/Time_of_Remembrance_and_Reconciliation_for_Those_Who_Lost_Their_Lives_during_the_Second_World_War), which...you don't actually need me to explain that extremely specific name, do you?  In Europe especially, it carries added meaning as the anniversary of the [Allies accepting the German surrender](https://en.wikipedia.org/wiki/Victory_in_Europe_Day).

If you find that too mainstream, you can celebrate a holiday that also involves death *and* ideas closely associated with Nazis, [White Lotus Day](https://en.wikipedia.org/wiki/White_Lotus_Day), the anniversary of the death of [Helena Blavatsky](https://en.wikipedia.org/wiki/Helena_Petrovna_Blavatsky), founder of [Theosophy](https://en.wikipedia.org/wiki/Theosophists).

![Field Marshall Wilhelm Keitel, signing the ratified surrender terms for the German Army at Russian Headquarters in Berlin. Germany, May 7, 1945](/blog/assets/keitel-111-SC-206292.png "I always assumed that pop culture exaggerated the monocle affectation...")

Sure, kind of a downer.  I'll try to say something amusing about programming, to balance it out.

Oh, it occurs to me that I should mention the [**Entropy Arbitrage** newsletter](https://www.buymeacoffee.com/jcolag), in that the next issue goes out through Buy Me a Coffee tomorrow morning.  The April 2023 issue includes a discussion on the various new social media platforms, an extended grumbling about the missed potential of **Star Trek:  Picard**, the month's media diet including eighteen shows/films/books/comics, links to the twenty posts published in April, links to six older posts that I updated in some way, the four most popular posts on the blog, over 150 links from the month that struck me as worth reading, and over twenty websites that I thought worth bookmarking.  I figure that I should *probably* announce when they go out...

If you sign up today (the eighth), then it'll show up in your inbox tomorrow at half-past seven my time, which equates to...early afternoon UTC, I think.  If you don't catch it in time, and can't read the post in the archives, tell me, and I'll figure out what went wrong with the permissions.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

It rarely comes up, so most people probably won't notice the difference, but largely because of [last week's developer diary post]({% post_url 2023-05-01-workers %}), the furthest background of a syntax-highlighting block has become transparent.  In writing that post, I discovered that the width of that container ignores visual interruptions, meaning that code blocks alongside something else, like a GitHub preview, would have a distracting, brightly-colored empty panel running along the background.  I don't believe that the container serves any visual purpose, so making it transparent shouldn't have any other effects.

And you actually won't see this in the code, because I store it with the [blog assets](https://gitlab.com/jcolag/entropy-arbitrage-assets)---and I'd use the preview to link there, but I never got around to writing a GitLab preview plugin...---but I upgraded the emoji set used by the blog, bringing me up to Unicode 15.0.  Therefore, I should now have the ability to display such classics as the shaking face {% emoji shaking face %}, moose {% emoji moose %}, jellyfish {% emoji jellyfish %}, pea pod {% emoji pea pod %}, the Sikh Khanda {% emoji khanda %}, pushing hands {% emoji leftwards pushing hand %}, and more.  It also includes the larger batch of new emoji from Unicode 14.0, maybe most prominently (because it horrified the bigots until they forgot about it) the pregnant man {% emoji pregnant man %}.

## Mastodon Tool Trunk

{% github jcolag/tool-trunk %}

I fixed a bit more of the code formatting on the *Rummager*, making ESLint fairly happy.  While there, I also fixed a bizarre typo that I should have spotted long before last week.

The code has also begun displaying more content, improving the layout of the headers, and supporting boosts.

And speaking of displaying things, more for my convenience than anything else, the *Rummager* now shows the media in each toot as a single row, resizing everything to fit.  I probably could have found better solutions, but it annoyed me to find my timeline getting overwhelmed by full-sized pieces of media.

## Periodic Scripts

{% github jcolag/periodic-scripts %}

By request of a couple of people, I have started extracting some parts of scripts for public use---tasks that don't rely on my specific infrastructure---and moving them to a repository of their own.

While doing this allows other people to build on what I have created over the years like any other project, it also gives me the opportunity to refactor some of this mess, and make sure that everything still has some relevance.  For one example, I run one script every night with a few hundred lines of code.  That code handles a variety of tasks, both periodically overnight, then another batch of tasks to set myself up for morning.  And while that mostly works, it could stand some modularity, so that the same script doesn't have responsibility for both taking notes overnight *and* setting up to publish the next day's blog posts.

This week, I only got around to extracting one piece, the code that generates the template for my nightly journal entries, as I described in my post on [Things That Worked in 2022]({% post_url 2022-11-27-worked %}).  I wanted to start there, because the [**Morning Dashboard**](https://github.com/jcolag/dash) increasingly uses the entries as data, and I have more potential to do so as I create a more structured format.  It could also probably stand some improvement that a reader might want to contribute.

### The Journal Structure

I should talk about the pieces that go into these journal entries, for people who want to work with or adapt the format.  On the programming side, it does a lot of its work with so-called here-documents.

```sh
cat >> "$journal" <<HERE
Everything between the "HERE" above and the "HERE" below
acts like a single input string, no matter how long,
convoluted, or otherwise messy.

HERE
```

This saves me needing to overload the script with unnecessary commands.

You'll probably also notice that it all comes in Markdown.  At this point, I write almost *everything* in Markdown, since---as I mentioned in my [post about plain-text data formats]({% post_url 2022-04-27-plain-text %})---that makes it straightforward to process in the future, if I need to do so.

Each starts with a quick question assessing how the day felt, with a choice of three emoji equating to bad, nothing special, or good.  I couldn't think of a more direct way of charting overall sentiment over time than ask.  Then, we have a section that changes with the day, asking weekly---and highly experimental to me---questions that range from gratitude exercises to adaptations of mental health check-ins.  It makes that choice by checking the day of the week.

```sh
weekday=$(date +%w)
# ...
if [ $weekday -eq 0 ]
then
  # ...
elif [ $weekday -eq 1 ]
then
  # ...
else
  echo "" >> "$journal"
fi
```

We then dig into, for lack of a better term, the memory exercises, starting with anything that I (not always intelligently) work on before getting out of bed, when I got out of bed, and why I chose that time, such as what distracted or delayed me.

Following that, we hit the most formal piece, a table of shows and movies that I watched on that day.  It includes the name of the show, the service that I used to watch it, a "gut reaction" in the form of a single emoji, a quick "review" of or other reaction to the show, and---for the season finale of ongoing shows or the series finale of older shows---whether I hope to see more like what I've seen.  I have provided some sample emoji that I'd typically use for my own notes, so that I can typically remove all but the one I want, but some cases warrant different emoji.  A sample media table (using Free Culture shows) might look something like this, with some simplistic reactions.

|Title|Service|Gut|Reaction|Renew?|
|-----|-------|---|--------|------|
|**Journey to Thelio**|System 76|{% emoji thumbsup %}|Interesting concept||
|The **Where Are the Joneses?** finale|PeerTube|{% emoji sparkling_heart %}|Excellent ending|{% emoji thumbsup %}|
|**Your Face Is a Saxophone**|YouTube|{% emoji thumbsup %}|Pretty funny||
|**Hamilton Live**|Voice of America|{% emoji satisfied %}|I should listen to the band more||
|**Valkaama**|Emby|{% emoji thumbsup %}|Great premise, if a bit muddled||

Because this section has such a rigorous format, it makes it fairly good for parsing.  For example, from the Linux command line, I can extract lines that start with `|**` or similiar---sometimes I need to preface the title for specifics, like the reference to a finale, above---using `grep`, take the various components using something like `cut -f3 -d'|'` (getting the service, in this case), and using that for processing.  With a few more commands, I can estimate which streaming service has provided me with the greatest and least value, over a given period, based on how much I watched it and the average sentiments.

In any case, the journal entries then go on to describing what I ate during the day.  I list breakfast and dinner, because I rarely eat both lunch and dinner, nor do I typically snack, so if you use the script or format, you'll want to update especially this part, based on your eating schedule.  If I do snack significantly, I write a sentence about that after the list.

The non-morning portion of the day comes next, typically nothing more than a list of things that I accomplished.  Sometimes, I'll separate the items into contexts---such as differentiating errands, housework, projects, books read, and so forth---but more typically, I'll list them in the order that I remember them and *might* reorder them into something resembling chronological order.

Finally, I have a section that looks more like a traditional journal or diary, where I can write out anything that weighs on my mind, tasks that I should take care of in the near future, possible project ideas, and anything else that crosses my mind.

## Next

I imagine that the **Mastodon Tool Trunk**'s *Rummager* will take up most of my time, this week, again.  It needs to start storing the seen toots, so that it doesn't show the same material.  And once I have anchors to historical reading, each session should pull all toots since the last session.

* * *

**Credits**:  The header image is [Field Marshall Wilhelm Keitel, signing the ratified surrender terms for the German Army at Russian Headquarters in Berlin. Germany, May 7, 1945](https://catalog.archives.gov/id/531290) by a United States Army Lt. Moore, in the public domain.
