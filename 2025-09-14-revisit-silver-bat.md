---
layout: post
title: Revisiting the Silver Bat
date: 2025-09-14 08:58:12-0400
categories:
tags: [books, fiction, free-culture]
summary: A fairly deep dive into revising my novel and working with Quarkdown
thumbnail: /blog/assets/Seeking-Refuge-v2-Cover.png
update: [
  2019-12-14-seeking-refuge.md,
]
description: Some reminiscing, some talking technology, some adventures in writing, and yes, a soft sales pitch.
spell: quarkdown ePUB Blakeneys Eun-Ju CPREP Woosters Tè Qūşīyah Thayetmyo sapere aude docname doctype doclang pageformat GoogleFonts Comfortaa docauthors pagemargin currentpage tableofcontents maxdepth qd mktemp PixelsPerInch pdftk nohup rm Magick PDFtk Calibre SourceSansPro otf ttf sed Fodongo Lambot Marais Ardeco Chukina OFL
proofed: true
---

* Ignore for ToC
{:toc}

Shortly before I started this blog, I wrote and released [**Seeking Refuge**]({% post_url 2019-12-14-seeking-refuge %}).  The novel attempted to vaguely reinvent the superhero genre with a more modern sensibility.   I don't talk about it too much, because it could definitely use an edit after my haste in getting it out, but it exists, and I take *some* pride in having written a complete novel that...I think almost works.

![My book's cover, a dark, blurry picture of a corridor with a person running away from the viewer, with the book's title The League of the Silver Bat: Seeking Refuge](/blog/assets/Seeking-Refuge-v2-Cover.png "I still like a lot about this cover")

Over the past couple of weeks, I have revised the text.  And, by the way, you can *buy* it.  If you'd like to cut to the chase on that, you can buy it at the following spots.

- [Stripe](https://buy.stripe.com/aFa4gzaPY9tx9KG17ubAs02), where you can give me three bucks, and I'll e-mail you the PDF and ePUB versions in a ZIP archive as soon as I can.
- [Buy Me a Coffee](https://buymeacoffee.com/jcolag), where I gather that *it* will handle delivery if you give it the three bucks, *or* you can join the membership program and download it free.

As I'll get to in this post, you can get the first edition on the Internet Archive or---if you want the Markdown source files to mess with---on Codeberg and GitHub.  I also plan to drop the paywall in six months, on <time datetime="2026-03-11">2026 March 11</time>.  If you have patience or don't mind old versions of the text, then you have no need to spend money on me.  But if you do have three bucks burning a hole in your pocket, I suspect that readers here will enjoy the story.

The rest of this post goes into why I chose to revisit the book now, and how I improved it, including a lot of documentation on keeping the process as automated as possible.  And soon---not *this* post, though, because it grew out of control---you can read the first chapter as a preview of the revised edition of the book, which also neatly serves as a short story.

## Concept

As a basis for the general idea, I took Batman as a broad archetype.  I grew up on Batman comics and the Adam West-led TV series, plus the character has one of the strongest trademarks in the world[^4], as I understand it.  And at the time, the movies had recently "rebooted" the character to fit the Superman films, and *already* started talking about the next reboot, giving the impression that I probably couldn't find a more mainstream inspiration.

[^4]:  In this case, by "strong trademark," I don't mean that Warner-Discovery or whoever will sue you (though they definitely will) for using their character, but rather that people around the world will most consistently recognize almost anything related to the character.

However, I wanted to modernize the character, less of an update than imagining how the superhero genre might work it we created it today.  In particular, I chose to replace the influence of [Zorro](https://en.wikipedia.org/wiki/Zorro)---a wealthy man turned unaccountable vigilante---with the [Scarlet Pimpernel](https://en.wikipedia.org/wiki/The_Scarlet_Pimpernel), a wealthy man turned *rescuer*.  I mean, sure, he starts out rescuing French aristocrats from the guillotine, which feels a bit silly for a modern role model where billionaires compete to do the worst possible things, but the "Pimpernel" name has also since applied to people aiding stranded Allied service personnel, refugees, resistance fighters, and political prisoners.  And while I believe that treaties have restored its copyright, for at least a while, [**Pimpernel Smith**](https://en.wikipedia.org/wiki/%22Pimpernel%22_Smith) sat in the public domain in the United States, where a descendant of the Blakeneys works to free prisoners of Nazi labor camps during the Holocaust, itself inspiring at least one real-world imitator who saved a dizzying number of prisoners.

Anyway, set against the backdrop of the first Trump administration's xenophobia and concentration camps, especially with the visceral images of kids in cages, it felt like I had something.

As a nod or two to the inspiration, Bertie Wooster---a convenient substitute for Bruce Wayne, complete with the wealth, image as a fop, valet, and even monogram---became the first Silver Bat after witnessing the deaths of his parents on the way out of seeing **The Scarlet Pimpernel** in its short-lived stage incarnation.  We meet his American descendant as he takes on the inherited role.

Anyway, after some setup, our protagonist takes a team into totally-not-Texas to liberate a secret labor camp from weirdos who love violence and Germanic languages. And most of it, in retrospect, I still liked, at least in my memories.

It also has a lot wrong with it. I think.  Let me present this sort of like one of the [Book Club](/blog/tag/book-club) posts, though without pulling *any* punches, because I can't hurt this particular author's feelings any more than I have whenever I thought about the book.

## The Good Parts

When I wrote it, the book had a lot that I liked about it.  It actually surprised me how much I enjoyed the story.  I don't *think* that any of what I have to say will give away too much information, but for those who want to skip it, feel free to click through to the [problems with the first edition](#what-went-wrong).

Starting the book with, in effect, a short story starring a retiring Silver Bat---which you can [read below](#just-another-night-in-the-life)---let me do a lot at once.  First, it starts the book with something exciting, little to no explanation, trying to grab the reader's attention in the same way that the opening sequence of a James Bond film does, though maybe not as successfully.  It also shows off the world's tone as both gritty and hopeful.  And, among other things, it sets up that these characters manage through plans and back-up plans, so that it feels natural for the protagonist's big project later in the book to feel like it has fallen apart.

I also love most of the cast.  To fit with the Free Culture ethos, I tried to give each character their own perspective, their own diction (probably not as successfully), and enough personality that you could imagine spinning almost anybody off into their own stories in their own context.  Most modern fiction feels terrible at this, where supporting characters either feel like an unneeded appendage to the protagonist or, if you could see them without their "patron," then you could probably only imagine them in the same kind of situations, with maybe some slight tonal differences.  Here, the investigative reporter, the forensic accountant, the hacker, the stage magician, the long-haul trucker, entrepreneur, and quite a few more feel like they have a few good stories in them waiting to come out that might have nothing to do with the League of the Silver Bat.  I'd genuinely love to see a story focusing on Bhang Eun-Ju's accounting work.

Oh, and speaking of the Free Culture ethos, I also love that the League of the Silver Bat feels like an idealized project.  You have a loose federation of strong-willed people individually acting to help people, sharing knowledge and labor for important initiatives.  We even have a major corporation setting themselves up in a leadership position, whose resources and support everybody appreciates, but doesn't really feel relevant to anybody else's activities.  They might not have released their project to the public for outsiders to improve, but you'll note the protagonist flirting with that idea on occasion.

You might also notice that we have a highly diverse cast, here, with the characters' names coming from around the world.  In fact, the book became the proving grounds for the script that would soon become [CPREP](https://github.com/jcolag/background-generator), my application for generating backgrounds for fictional characters.  I generated the characters in bulk, then other than the Woosters themselves, picked off the next entry whenever I needed a new character, to push the demographics closer to global averages.

I also at least tried to make the fights both comprehensible and fairly realistic.  Each of those scenes wants to clarify where to find everybody involved, and keeps the attention focused on one person.  Everything also *hurts*, and failing to prepare makes everything worse.

Oh, and I also like that I both use and subvert the Hero's Journey template.  For example, the book turns "the belly of the whale" into a trip to a secret human resources department in the basement.  And the story constantly reinforces that, no matter what the plot structure might suggest, you can only make significant change through cooperation.

## What Went Wrong

Despite all the patting myself on the back, most prominently in my eyes, I also took the Batman template too literally, trying to figure out how to turn a fictional billionaire into a progressive force in the world, despite the fact that you *really* can't find yourself with a billion dollars without exploiting a lot of people.  In that sense, the book looks like our world's wealthy people destroying millions of lives, then donating a few million dollars to museums to clean up their reputation.

Compounding the problem, I revisit the question several times to show the protagonist feeling uncomfortable with the situation, but always resolve it with an accidental metaphor for and defense of [access journalism](https://en.wikipedia.org/wiki/Access_journalism), where sure, we *could* do a good job.  We *could* put our efforts to exposing and breaking down unjust structures directly.  But what if doing a good job now made it more difficult to do a great job at some point in the future...?

Yet we know that the "great job" only ever comes too late to help anybody, often in the form of a tell-all book published near the journalist's death.  When they could actually help avert problems, they talk about their subjects as [clever tricks or shattering uninteresting norms](https://theconversation.com/why-journalists-are-reluctant-to-call-trump-an-authoritarian-and-why-that-matters-for-democracy-263778).

In addition, while I did fight---in the sense that I wrote software to make sure that I didn't take any shortcuts---for that diverse cast, the diversity has almost nothing to do with the story.  Their ethnicities get called out occasionally to highlight the racism in the various themes, once or twice, and I believe that it gestures at a couple of the agents getting involved with the League during an emergency in their countries of origin.  Some of them almost certainly grew up in the United States and have no ties to their parents' or grandparents' countries of origins, but it starts to seem improbable for all of them to have no traces of growing up in Korea, Brazil, Egypt, China, Belgium, Bangladesh, Spain, Myanmar, India, Nigeria, Pakistan, Venezuela, and other countries, or had families from those regions.

And speaking of the diverse cast, I also didn't get to or ignored many other kinds of diversity.  Of the generated profiles, Tè and Waleed *should* both have a social phobia of some sort, but you'd never know that from the story.  Likewise, Rajesh came out with Post-Traumatic Stress.  And I never made it far enough down the list to reach the two characters with independent living problems, which feels like a missed opportunity for representation.

The same goes for sexual orientation.  I sprinkled prospective romantic partners for the protagonist throughout the book, but in the first edition, pulled back on actually identifying them as such or even identifying that the protagonist might have any interest, and it came off feeling like when a creator extensively chronicles heterosexual relationships, but years after the fact tells fans that no, they totally included a gay character off on the sidelines, who happened to never have the opportunity for romance.  I can barely justify a lack of gender identity, because---apart from dealing with the bigoted folks, where inclusion would come off as mean-spirited---it seems like they would all see transgender folks as unremarkable, but I still regret not finding some way to usefully identify anybody as transgender.

Mind you, I did (some of) that intentionally, so that I wouldn't "other" any of the characters or find myself relying on ugly stereotypes in my ignorance of the culture in Al Qūşīyah or Thayetmyo, or in not finding a way to make a person's gender identity relevant after bringing it up.

In many ways, I feel like the story also down-played the enormity of its own main conflict.  We have a secret labor camp packed with refugees under an authoritarian government.  But the framing, in taking an exaggerated example for the sake of entertainment and not publishing anything libelous, feels like it gives the impression that this situation sits *aside* of culture, as if we don't have centuries of history filled with racism and xenophobia.

In a similar way---and I go into this in the *Credits* section of the new edition of the book---my original vision of the crypto-Nazis had them using a modified version of a foreign language.  I wanted to illustrate that the characters wouldn't successfully infiltrate the group, while also providing something that a reader could readily decipher without much prompting.  However, I ended up only making them look *foreign*, as if---much like the separation between fiction and reality---the United States doesn't have white nationalists.

Seriously, the United States took so long to join World War II, because we had so much support for the Nazis.  As for the Nazis themselves, they looked at Jim Crow laws across America as a central part of their segregation strategy.  The phrase "American as apple pie" comes immediately to mind.  And no amount of Russian misinformation, praise for Hungarian authoritarianism, religious fundamentalism that might remind some of Muslim fundamentalism, or similarity to the behavior of certain Brazilian or Korean leaders changes the fact that we need to get our own house in order, not merely remove these outside influences.

It also has these...moments of absolute pretense.  Poems show up at weird times.  The Latin phrase *sapere aude*, "dare to know," gets an entire page of its own like some insipid conspiracy theorist manifesto.  And probably other flourishes that *fit*, but I find at least mildly embarrassing.

Anyway, maybe most damning, I never gave the book a full read-through of my own, not even to proofread it.  I generally have enough confidence in my writing to assume that I didn't release the first edition with any horrific typos, but it also shows a lack of respect for the reader or even the work itself to not double-check.

Oh, and I have one more significant problem to mention, though this time with my experience in self-publishing, rather than your experience as a reader.  Because I didn't feel like learning LaTeX for a novel and insisted that I could do everything important in Markdown, I ended up with an ugly build process where I used [Pandoc](https://pandoc.org/) to generate styled text.  That output, I manually imported into [LibreOffice](https://www.libreoffice.org/)'s Writer, where set up the page size, the page numbers, the page breaks between chapters, and so forth.  I then manually exported *that* into a PDF file.  It felt silly to touch the text, if I would only need to then schedule some time to release an update, almost defeating the purpose.

## Fixing It

That last issue actually kicked off the current version of the project.  A few e-mail newsletters that I read recently spent some time highlighting [Quarkdown](https://quarkdown.com/).  Honestly, my initial reaction leaned more towards "this seems silly," because I shouldn't some a huge Java application to do what Pandoc already mostly does...and then also requires Node.js, [Puppeteer](https://pptr.dev/), and a browser, to actually get to the PDF file.  Especially since I found it when I had to work with an old, low-end laptop, that seemed like a *lot* of computing power needed to make something that looked slightly nicer than what I already had.

As I moved to a better computer, though, and the idea settled in the back of my mind, I decided to experiment with Quarkdown, creating the first couple of chapters of a "setting guide" for a fictional town that I have wanted to write for a few years, now.  And I'll admit that Quarkdown has some problems.

- It can't/won't create a full-page image, making covers difficult.
- It doesn't allow for "resetting" the page numbers, as far as I know.  This means that you can't get a traditional book with prefatory material enumerated with lowercase Roman numerals, main text enumerated with Arabic numerals, and a table of contents that includes both.
- Likewise, page numbers operate as an all-or-nothing proposition, so either pages such as covers or interstitial blank pages must have page numbers or no pages have page numbers.
- I would call the documentation *uneven*, some of it excellent, but some of it presuming that you already know how to solve the problem that it explains.
- Unlike other versions of Markdown, you get an em-dash with a hyphen surrounded by spaces, rather than three consecutive hyphens, the latter of which my writing uses...extensively.

However, within those constraints, the prototype started looking fairly solid fairly quickly.  It'll still take effort to finish the book, including finding a way to reliably draw maps, though, so I needed a cleaner test case.  I looked at some of the other books that I've thought about releasing---refreshing my old lecture notes into short textbooks, collecting my short stories, translating some Free Culture or public domain stories, and so forth---before realizing that I already had a complete novel, clocking in at about fifty-five thousand words.

Oh, and the book centers on a kind of heist liberating an immigrant labor camp under definitely-not-the-Trump-administration, inspired by *The Scarlet Pimpernel* books, in the face of the oligarchic corporate leaders propping up an authoritarian administration in the White House.  Given the oligarchy's new-found love of fascism for Donald Trump's second term, not to mention the massive expansion of...well, not "immigration enforcement," because they don't actually care about immigration so much as intimidating brown people, but you get the idea.  In any case, the book became topical again.

As mentioned, I even *enjoyed* the story, if not all the specifics, so I hesitantly started revising and proofreading the book.  I hesitated, because after six years, who could even guess whether the book would warrant the work?  Despite my fond memories, because I didn't carefully review it, it could have made no sense, or had all sorts of horrible ideas.  Usually, I trust myself while I work on something, but probably like most people, in hindsight I usually only see what I might have overlooked...

Anyway, I created a top-level file for the book looking like this, coming close to my original design.

```
.docname {Seeking Refuge}
.doctype {paged}
.doclang {English}
.theme {paperwhite} layout:{beamer}
.pageformat width:{4.25in} height:{6.87in} margin:{0.25in}
.font {GoogleFonts:Source Sans Pro} heading:{GoogleFonts:Comfortaa}

.docauthors
  - John Colagioia

.pagemargin {bottomcenter}
    .currentpage

.numbering
  - headings: none

.include {00-titles.md}
.tableofcontents maxdepth:{2}
.include {01-teaser.md}
.include {02-intro.md}
.include {03-ropes.md}
.include {04-underworld.md}
.include {05-threshold.md}
.include {06-plan.md}
.include {07-entrance.md}
.include {08-guests.md}
.include {09-jailbreak.md}
.include {10-escape.md}
.include {11-chase.md}
.include {12-mercy.md}
.include {13-recover.md}
.include {14-father.md}
.include {15-abyss.md}
.include {16-jeeves.md}
.include {17-party.md}
.include {18-reconcile.md}
.include {19-finale.md}
.include {20-credits.md}
```

Why 4.25 by 6.87 inches?  I envisioned the first edition as a cheap mass-market paperback, the sort of thing that teenage-me wouldn't have hesitated to grab at a used book store---back when those existed---or a garage sale.

Normally I don't use Google Fonts for anything, but since this doesn't expose readers *to* Google, and saves me the effort of figuring out how to convince Quarkdown to use locally installed fonts, this seemed expedient, working from the original Markdown files from the [book's repository](https://codeberg.org/jcolag/silver-bat-01-seeking-refuge).  Anyway, then I ran the magic words.

```
quarkdown c -p -w seeking-refuge.qd
```

This gave me...something.  It didn't generate the static book, despite the "compile" command, but provided a URL with a live-updating version of how the book should appear.  Had I read the *tiniest* bit further in the documentation, I would've noticed that the `--pdf` option "produces a PDF file," and saved myself the experimentation with printing the book from the browser.

### Curbing Bad Ideas

From there, I started revising.  Every turn of phrase that sounded awkward, I either improved, replaced, or deleted.  When something felt unclear---a few passages used too many pronouns---I restructured the description to clarify.  Passive voice had to go, across the board.  Because I overused it the first time, often accounting for the aforementioned lack of clarity, I reduced instances of the verb *to be*, though I didn't take as firm a hand there as I do for the blog, especially in dialogue.  Oh, and I updated the em-dash style for Quarkdown.  And when I had finished each chapter, I ran it through the same gamut of static-checking that each blog post gets before I publish it, which should drastically reduce typos from the first edition.

I also touched up certain aspects.  As mentioned earlier, I regretted putting potential romantic interests in place, but then avoiding calling attention to those relationships.  While I didn't add any relationships to the story, because I don't think that it has space for them, this version makes it clear that our protagonist previously dated both Yelena and Waleed---using the same comment about it not feeling awkward, but maybe it does, because that felt in-character to me---which makes inviting Marco to dinner near the end seem like a date as (I believe that) I originally intended, without actually touching that scene.

Another bigger change comes with the original...libertarian-ness of *especially* the handling of people under their protection who fear for their lives.  In the original version, I asked what a "good" billionaire would do in that situation, and decided that they would wave away the legal and ethical implications and drop that person in a new life with false credentials, a privatized vision of [witness protection](https://en.wikipedia.org/wiki/Witness_protection).  In hindsight, though, I see that the scene feels like it implicitly *endorses* privatizing critical government services, but also directly played into right-wing conspiracy theories about immigrants having falsified their citizenship---under the direction of some billionaire, no less---to sway elections.

I revised that to suggesting that they borrow a real person's identity with consent.  That doesn't seem nearly as bad, if the company pays their real identity a salary in their home country, that they then use to pay for groceries and housing while they need to hide.

Notably, I did *not* cut the embarrassing pretentious bits.  My opinion of those moments hasn't improved, but I agree with their inclusion as worth reading, and I call out the excesses in the new foreword.

Overall, I think that it confirmed that the story has potential, and this second edition improves it substantially.

### More Technical Issues

Anyway, back to constructing the book, I needed to resolve some issues that accumulated.  I could live with consistent page numbers everywhere, *except* for the cover and front-matter.  And as I thought about the presentation, I also realized that I wanted blank pages under the cover, to mimic an actual book.

Putting everything together, I separated the front-matter into its own bit of Quarkdown with no page numbers, and set to building the entire book, coming up with the following script.

```bash
#!/bin/bash
cover=$(mktemp --suffix=.pdf)
back=$(mktemp --suffix=.pdf)
blank=$(mktemp --suffix=.pdf)

convert xc:none -page 306x494.64 "${blank}"
convert 01-Refuge/assets/01-Refuge-Cover.png \
  -resize 637.50x1030.50 \
  -gravity center \
  -extent 637.50x1030.50 \
  -units PixelsPerInch \
  -density 150 "${cover}"
convert 01-Refuge/assets/01-Refuge-Back-Cover.png \
  -resize 637.50x1030.50 \
  -gravity center \
  -extent 637.50x1030.50 \
  -units PixelsPerInch \
  -density 150 "${back}"
quarkdown c --pdf 01-Refuge/front-matter.qd
quarkdown c --pdf 01-Refuge/seeking-refuge.qd
pdftk "${cover}" "${blank}" \
  output/Seeking-Refuge-Frontmatter.pdf \
  output/Seeking-Refuge.pdf "${blank}" \
  "${blank}" "${back}" \
  cat output output/Seeking-Refuge-v2.pdf
nohup evince output/Seeking-Refuge-v2.pdf &
sleep 1
rm "${cover}" "${back}" "${blank}" \
  output/Seeking-Refuge-Frontmatter.pdf \
  nohup.out
```

Oh, and I created a back cover for the book, too.

It creates a blank PDF page of the relevant size, plus single-page PDF files for the front and (now) back covers, all using [Image Magick](https://imagemagick.org/).  Then, it compiles the front-matter and main book into their respective PDF files.  Finally of the important parts, it uses [PDFtk](https://www.pdflabs.com/tools/pdftk-server/)---not a server, no matter what the name says, and available for most platforms through package managers despite their insistence on Windows downloads---to assemble everything.

For my own gratification, it then opens the final PDF and deletes most of the intermediate files.

### Other Formats

That leaves one problem:  Not everybody reads from PDF files, especially on portable and mobile devices.  Unfortunately, that "takes some doing."

For one thing, we don't have many decent PDF-to-ePUB conversions.  Everybody online points to [Calibre](https://calibre-ebook.com/), which requires that I do it manually---except for the hidden `ebook-convert` command-line utility---*and* it then does a miserable job[^1] by generating a bogus image per page of...an empty X-Ray, maybe?  I have no idea, but I can't release garbage like that.  Seriously, for every page of the PDF, it inserts a page-shaped blob with fuzzy images.

[^1]:  Also, I loathe the application, and don't understand the "hive mind" of people rushing to recommend something that looks terrible, demands control over your entire library, and has weird Victorian-era opinions on what a book should look like...

Therefore, for this, I need to make some compromises and step back to the Markdown source, and use the aforementioned Pandoc come up with this monstrosity of a command.

```bash
pandoc --from markdown \
  --output=../output/Seeking-Refuge-v2.epub \
  --metadata title="The League of the Silver Bat #1:  Seeking Refuge" \
  --metadata author="John Colagioia" \
  --toc \
  --css assets/epub.css \
  --epub-cover assets/01-Refuge-Cover.png \
  --epub-embed-font=fonts/SourceSansPro-Regular.otf \
  --epub-embed-font=fonts/Comfortaa-Regular.ttf \
  <(sed 's/<<<//g;s/^#/\n\n#/g;s/ - /---/g;s/^\..*//g;s/#!/#/g;s/^  //g' *.md)
```

I assume that you can follow the `--from` and `--output` parameters on your own.  Likewise, the `--metadata` items probably make sense without me explaining the idea of a title or author.  We add a table of contents, then a stylesheet to specify the fonts, which looks something like this.

```CSS
@font-face {
  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 400;
  src: url('../fonts/SourceSansPro-Regular.otf');
}
@font-face {
  font-family: 'Comfortaa';
  font-style: normal;
  font-weight: 400;
  src: url('../fonts/Comfortaa-Regular.ttf');
}
body {
  font-family: 'Source Sans Pro';
  font-size: 1.5em;
}
h1,h2,h3,h4,h5,h6 {
  font-family: 'Comfortaa';
}
```

Normally, I wouldn't bother to quote something so boring, *except* that you should notice that the `fonts` folder, to the ePUB file, lives in the hypothetical *parent* folder, even though that doesn't really make much sense conceptually.  If you unpack an ePUB file with fonts, though, you'll see that it won't work any other way.

Anyway, getting back to the `pandoc` call, we specify the cover image---I can't give it a back cover, as far as I can tell---and tell it to embed the two fonts used.  And then we have *nothing* more to talk about.  Nope.  Nothing after that.  OK, except for the part that says this.

```bash
<(sed 's/<<<//g;s/^#/\n\n#/g;s/ - /---/g;s/^\..*//g;s/#!/#/g;s/^  //g' *.md)
```

What on Earth, right?  Yeah.  You see, I can't directly give `pandoc` the files that I revised, because they now use Quarkdown's "flavor" of Markdown.  This tells the `bash` shell to give the `pandoc` command its input from the result of the specified command (`<(...)`), a series of `sed` commands separated by semicolons, which try to turn the Quarkdown-style Markdown back into something that Pandoc installs.

|Expression|What It Does|
|-------------|---|
|`s/<<<//g`|Remove manual page-breaks, not supported by Pandoc|
|`s/^#/\n\n#/g`|Make sure that headings have blank lines before them|
|`s/ - /---/g`|Put the em-dashes back|
|`s/^\..*//g`|Remove Quarkdown-supported directives, like `.box` and `.center`|
|`s/#!/#/g`|Remove the don't-show-this-heading-in-the-table-of-contents marks|
|`s/^  //g`|Pull all indented text (from the directives) to the left margin|

It probably still horrifies you, and I don't blame you, but after all that, it does create an ePUB book from the collection of input files with no immediately apparent defects.  Oh, and note that this only works because I make sure that the files have names that start in the proper order.  If I didn't have the foresight to prefix every name with its order, then I would've needed to replace `*.md` with each file in the proper order, or the chapters would show up randomly.

Whew...

OK, with that, this post has run far longer than I expected, so I don't want to try to cram in another couple of thousand words of preview.  But I'll definitely run at least the first chapter of the story---which again, serves as a standalone story to set the book's tone---in the next week or two, depending on whether I have something else ready for the twenty-first.

## Buy It...If You Dare

Because I have so many other books that I *want* to put together, I decided that I should probably see how much support exists for this sort of work, hence putting the book up for sale.

Again, you can get it at [Stripe](https://buy.stripe.com/aFa4gzaPY9tx9KG17ubAs02) and [Buy Me a Coffee](https://buymeacoffee.com/jcolag)[^2].  I have also added a [storefront](https://john.colagioia.net/store/) to the website, though it only has the one book, for now, using Stripe's button generator, which may or may not track you.

[^2]:  Also, I understand financial distress.  If you can't afford the money, genuinely want to read the thing before I give it a public release, and don't want to waste time with the original edition, then reach out.

The other books that I have in mind will *probably* come out no matter how well my little experiment in sales goes.  You all know me, after all, and I do all this mostly for myself.  However, the better the book sells, the more effort that I'll put into getting them out faster.

## Answers to Presumed Questions

I can't guarantee that people will have *frequently* asked these questions, but they seem like questions that people would ask.

### Why Now

The release of Quarkdown did get my attention.  Add in history rhyming in less than six years, and it seemed like an interesting idea to return to.

### Why Charge Money

In a lot of ways, I have wanted to run an experiment like this for a while.

While my book club posts *try* to err on the side of diversity, Free Culture---much as Free Software and other charitable, communal activities---has a bias towards privilege.  After all, who has the time to develop an entire fictional narrative in any medium, and few concerns about giving the results away?  People who have money and time can do things like that.  People who don't can't[^3].

[^3]:  Actually, due to the job-hunt that I keep trying to avoid mentioning, so that this blog doesn't become my personal trials, I could actually use the money, if people could spare it.

I want to see what---pardon the term---*business models* that I can strap to this idea, so that we can maybe find options that work well enough that they can help people who need it.  For this experiment, I adapt the model used by [**Fodongo**](https://fodongo.jectoons.net/), selling the book up-front, and making it available free after a fixed duration.  Everybody can get it eventually, but some people might pay for the temporary exclusivity.

Also, the pay-wall serves as a quick-and-dirty measurement of whether people care.  If people buy the book, or if they ask me to make exceptions for economic hardship reasons, that gives me a clear signal to keep working in a way that the Internet Archive telling me that the book's page has had "181 Views,  2 Favorites" doesn't, especially when I assume that *I* marked it as a favorite.

### Why Six Months

I picked a number out of an imaginary hat.  It takes carving out time to read a novel.  Almost-the-equinox seemed clever.  Experiments need to try new things.

Something like that...

### How I Maintain Exclusivity

I don't.

Seriously, if you want to download the book and put up a competing store, syndicate it on your website, or dump it on a server for other people to find, that becomes a result of the experiment.  Even if I *could* stop people from doing such things, I don't think that I would.  Plus, I doubt that anybody would do those things.

That all takes effort *after* spending three bucks, for a book that *maybe* nobody else wants to read.  Seriously, in the almost-six years since I released the original edition of the book, I have gotten exactly one piece of feedback on it, an acknowledgement from someone who I know personally that I did something with my time when I mentioned writing it.  And what, you want to put in effort to fight me for (potentially) that prize...?

As such, no, I have no interest in stopping owners from doing what they please with the book, within the bounds of the license.

### What Comes Next

I got into this a bit before, but I have a lot that could become a maybe-interesting book.  The speed at which I get to them, though, probably depends on how this experiment goes.  If people want this book, then they might want the next, and that'll give me some motivation.  If this lands with the same flop as my first release of the book, then work might progress about as fast as it has on the *second* novel, which I had in the works for about three years before I realized that I overcomplicated it.

Anyway, if this goes well, I have a translation of an old, obscure science fiction story that I tried to release something like twenty years ago.  I want to collect the short stories that I have released on the blog, maybe with a couple of new stories that I mostly have waiting for an opportune moment.  From many years of teaching, I have enough lecture notes that I could cover most of a computer science curriculum.  I have (I think) a clever idea for either a time travel story or a collection of short stories.  I often think about collating what we learn in the [Real Life in Star Trek](/blog/tag/star-trek) posts, working issue by issue, with clear citations for every conclusion.  For some quasi-abandoned projects, I have some background material that could work as a fictional guide.  That second novel has enough notes on it that you might even convince me to get back to that, too.

Again, I won't hold those projects hostage, but I also can't really prioritize them if nobody seems interested.

### Why No Question Marks

For purists---and tools that validate Markdown---headings shouldn't end with punctuation.  I assume that it makes URLs linking directly to the heading more difficult.

### Those Links Again

Sure.  To recap...

- [Stripe](https://buy.stripe.com/aFa4gzaPY9tx9KG17ubAs02).  When I get notified of purchase, I'll mail you the ZIP file with the PDF and ePUB versions.
- [Buy Me a Coffee](https://buymeacoffee.com/jcolag).  You can either buy the PDF or download it free if you become a member.
- [Internet Archive](https://archive.org/details/seekingrefuge), for the first edition.
- [Codeberg](https://codeberg.org/jcolag/silver-bat-01-seeking-refuge), if you want the first edition's Markdown source.
- [GitHub](https://github.com/jcolag/silver-bat-01-seeking-refuge), if you want the first edition's Markdown source and still spend your time on GitHub.

And if you don't want to spend the money or read the old edition, mark your calendars for mid-March.

## Watch This Space

This experiment will evolve, and I hope that you'll participate.  If you buy the book, that'll thrill me.  If you adapt my process, I hope that it works for you and you can improve it.  And if you have other models of making Free Culture sustainable, I'd love to hear from you.

Most of all, I did enjoy writing the book, and re-reading it.  And I hope that you enjoy reading it, too, and find new uses for the characters and concepts.

* * *

**Credits**:  The header image is **Seeking Refuge**'s cover, based on [An Alley in the City of Darkness](https://commons.wikimedia.org/wiki/File:KWC_-_Alley.jpg) by Ian Lambot, made available under the Creative Commons Attribution 4.0 International license, [dark, night, light](https://stocksnap.io/photo/dark-night-LXCKQ8LU32) by Etienne Marais, made available under the Creative Commons Zero license, and the [Ardeco](https://online-fonts.com/fonts/ardeco) font designed by Irina Chukina and made available under the terms of the OFL.
