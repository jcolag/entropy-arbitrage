---
layout: post
title: Developer Diary, Hıdırellez
date: 2024-05-06 07:13:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/5ccd9a194a62b5-33270460-IMG-0735.png
offset: -15%
teaser: This week's projects include newsletter updates, The Light's Edge, BASIC, Notoboto, Earburn, and the blog itself.
spell: Hıdırellez Notoboto Lydda Hydyrlez Bakhchisarai Nitery Earburn transmedia TCL countText pnl notearea nw llength Spoutible twtxt
proofed: true
---

Today, Turks and their neighbors celebrate spring in [Hıdırellez](https://en.wikipedia.org/wiki/H%C4%B1d%C4%B1rellez), though folk traditions describe it as honoring the meeting of two important Muslim prophets, and borrows a bit from the legend of [George of Lydda](https://en.wikipedia.org/wiki/Saint_George), celebrated around the same time in some other parts of Europe.

![Celebration of Hydyrlez in the Bakhchisarai region of the Republic of Crimea](/blog/assets/5ccd9a194a62b5-33270460-IMG-0735.png "Yeah, I brought Crimea into this.  What of it...?")

And on we go to the projects.

## Social Media

This probably doesn't qualify as social media, as such, but for the sake of cramming it somewhere that nobody will mistake for code or other published work, for the sake of [the **Entropy Arbitrage** newsletter](https://buymeacoffee.com/jcolag), Mailchimp had me jump through a bunch of hoops to set up their version of [DKIM](https://en.wikipedia.org/wiki/DomainKeys_Identified_Mail)---which somehow requires directing some of my DNS to their servers---so that the big e-mail providers won't immediately classify the newsletter as spam.

Note that they didn't bother to tell me about this until *after* I sent out the newsletter on Saturday, so anybody signed up will apparently need to check their spam folders.

I dislike everything about this process.  Companies like Mailchimp have enabled scammers to flood e-mail servers, so the e-mail providers built a system that excludes small domains like mine, forcing us to bend to the will of the companies that caused the problem in the first place.  And yet, newsletter content doesn't feel like it fits on the blog, for the most part, so I want it *somewhere*, with the best game in (the figurative) town owned by the same company that lobbies to make filing taxes difficult.

If we follow that trend, in another twenty years, then the big e-mail providers *probably* won't allow you to send any e-mail at all *unless* you send spam...

## The Light's Edge

{% codeberg jcolag/thelightsedge %}

Not much has changed, here, but the [main project page](https://www.thelightsedge.com/) now has a bit more organization to it to enable future expansion, and has cleaned up its verbiage for either better clarity or more directness.  Probably more importantly, the final section now links to what I think of as the prologues of the story, the transmedia aspects.

You'll also note that the Last Frontier Nitery's page now has an unpublished secondary page.  It borrows everything from its main page, and the main page hasn't changed, but it never quite felt right to keep everything on a single page, so I'll start breaking that up---probably removing or reducing the text on the index---and maybe give those pages a menu.

## BASIC's Anniversary

{% codeberg jcolag/basic-interpreter %}

I didn't do **any** work on this, at any point this week, but given how many people I know have had something to say about [the sixtieth anniversary of the BASIC programming language <i class="fas fa-copyright"></i>](https://arstechnica.com/gadgets/2024/05/the-basic-programming-language-turns-60/) passing on Wednesday, it seemed like a good time to remind readers that I recently published the source code for the BASIC interpreter that I developed for teaching a programming languages class, many years ago.  Buckle in for a story that I hope goes quickly enough.

In short---you can find the long version in the repository itself---I started teaching the class by taking each week's lecture and finding a handful of real-world programming languages for the students to write a minimal programming showing an aspect of the language reflected in the lecture.  For example, talking about expressions and typing would result in an assignment to use an even-old-then version of Perl that used addition for both adding numbers and concatenating strings; the expressions would also have the students find the result of an arithmetic expression in LISP and FORTH, demonstrating prefix and postfix notation.  To support this, the class website included a targeted "cheat sheet" on each language that I wrote, teaching exactly enough to get through the assignment, without covering the entire language.  I left those tutorials next to the download packages that I supplied.

Students...reacted badly to that.  Some got the idea, but the less-diligent and more-anxiety-ridden cohorts managed to ignore my tiny tutorials and panicked as they tried to learn how to develop software in a bunch of different languages in seven days.  Worse, it took a long time for me to *discover* this disconnect.  I had a reputation as a harsh grader, largely from students who expected memorization to get them through a more analytical class, so many students assumed that I intended the more difficult task.

Anyway, because I didn't want the language situation to cause any real frustration---I really only wanted the students to get experience with key features---I developed this interpreter, with configuration options that would provide the various features that I otherwise would have picked a "boring" language to showcase.  And that flexibility allowed me to add features that a student couldn't quickly find elsewhere at the time, such as a [`COME FROM`](https://en.wikipedia.org/wiki/COMEFROM) statement.

It could use some work to make it useful to anyone not solving one of my homework problems.  For example, the language doesn't yet support strings or functions...but it *could*.

### The Harsh Grading Thing

To quickly complete the tangential comment, above, for any curious readers:  My exams assumed that the students knew the material covered in class, and so asked them to work with it rather than parrot it back to me.  The overwhelming majority of students did extremely well, and for most classes, I would accept almost *any* relevant work as extra credit, for the students who couldn't get accustomed to the exams.  I had students do horribly on the tests, and still get an A-grade for the class by doing so much extra credit work...though I wouldn't have recommended that route.

If I truly became "harsh" at all, that happened once I submitted the grades.  I would accept no new work past that point, without evidence that I had made a serious mistake in earlier grades, or a student had a legitimate excuse for under-performing and not wanting to confide in me at the time.

By contrast, certain students---who all knew the grading criteria from the syllabus handed out on the first night, plus all their grades except for the final exam itself, and so could calculate pretty accurately what they'd get, and in later years, I'd send an automated e-mail before the final, with the range of grades that they could expect based on those same calculations---often wanted to wait until they received their grades in the mail weeks later to ask me for a better grade.  And while I understand and sympathize that tuition reimbursement and maybe more riding on getting a good grade, I also couldn't justify artificially boosting the grade of a student who didn't take the course seriously at the time, given how that behavior presents the work of the diligent students as irrelevant *and* could have jeopardized the school's accreditation.

That should provide enough background on the reputation of harshness to determine if it sounds credible...

## Notoboto

{% github jcolag/Notoboto %}

I believe that I've brought the note-editor up to date with everything that I had in mind a few weeks ago.

While I may have cleaned up an occasional line of code along the way, the window now has a functioning status bar.  For most users, this probably won't matter.  However, it now allows users to quickly see the note's title, the approximate number of words and characters in the note, and the position of the caret in the text.  Admittedly, I use most of it as an excuse to justify having the word-count, there, which I find important to tell me that a note has grown too long to make sense as a single note.

The actual counting doesn't really please me, hence my use of the word "approximate," but it didn't require much code and should provide sufficiently close results in most cases.

```tcl
proc countText {widget} {
  set text [.fr.pnl.notearea get 1.0 end]
  set words [regexp -all -inline {\S+} $text]
  set nw [llength $words]
  set chars [string length $text]
  return [list $nw $chars]
}
```

It looks for all groups of non-whitespace characters, and counts them.  It seemed less prone to frustration to count everything that way than trying to derive rules for when an apostrophe or hyphen separates words.

I should note that the code updates the status bar on the same schedule that it updates the formatting:  It waits until the user has paused typing, before doing any significant work that the user would make obsolete anyway.

## Earburn

{% github jcolag/earburn %}

Alas, I don't have anything new to report here.

I *did* install a screen recorder, [Blue Recorder](https://github.com/xlmnxp/blue-recorder/), which seems largely unobjectionable.  Now I need to figure out how to show the extension to people who don't seem to understand or care about any of the relevant concepts, but apparently want to pretend that they do their work well.

{% emoji crossed fingers %} Wish me luck...

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

I probably created this too late, given the impending closure of Post.News likely to trim down its utility, but to speed publishing everything for a post, I *finally* wrote a script to generate the little announcements that go out on social media.  Unimaginatively, I call it `post.sh`.

In essence, it does what I've done manually to create the announcements that go out on [my {% emoji latte %} Buy Me a Coffee page](https://buymeacoffee.com/jcolag), Cohost, Post.News (for the moment), and Spoutible.  It grabs the title and summary, figures out the eventual URL, grabs the teaser, and finally grabs the tags.  Not every platform works quite the same, so I still have *some* work to do beyond copying-and-pasting.  Specifically, the output works as-is for Spoutible.  Post.News and Buy Me a Coffee need me to add the URL as a link, to keep the announcement looking clean.  Cohost requires manual changes to turn the whole thing into Markdown.  And neither Cohost nor Buy Me a Coffee uses hashtags in the body of the post.

However, I *already* needed to do that work, after I tediously assembled the announcement from the Markdown file for the outbound post, so this streamlines the process dramatically.

And for the sake of saying so for completeness, Diaspora, Mastodon, Matrix, and twtxt have their announcements handled at the end of the *build* script, since I can post to those networks automatically via either the API or (for twtxt) appending to the log.  Or, rather, I *should* have the ability to post through Diaspora's API automatically, but I never got the authentication to work right, so the script generates the Markdown for me to paste.

## Next

This week, I hope to get to the end of the **Earburn** story.  And I believe that I've cleared away enough of my own backlog---and could use some lighter work---that I can finally start on work through the backlog of library updates that GitHub has nagged me about.

I'll probably also tweak that `post.sh` script for the blog, so that it also generates the Markdown for Cohost and Diaspora, moving or copying it from the build script.  They should look similar enough, except for the tags and headline.  I could probably also do something for the Cohost/Post.News headline, too, since I generally try to keep those consistent.

* * *

**Credits**:  The header image is [Hıdırellez in Crimea](https://glava.rk.gov.ru/articles/f66d6f79-9571-4d35-8ca8-8be5da1153fc) by Правительство Республики Крым (the Crimean government), made available under the terms of the [Creative Commons Attribution 4.0 Universal](https://creativecommons.org/licenses/by/4.0/).
