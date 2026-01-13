---
layout: post
title: Developer Diary, Coast Guard Day (belated)
date: 2024-08-05 07:23:05-0400
categories:
tags: [programming, project, devjournal]
labels: [blog, css, fictopedia]
summary: Progress on assorted projects
thumbnail: /blog/assets/Coast_Guard_Day_2013_by_Cory_Mendenhall.png
offset: -15%
teaser: This week's projects include visual hints on outbound blog links, updating blog posts, and the Fictopedia archive.
spell: Fictopedia Nelgrik ZRPG Lubion Wayback kerning Mendenhall
proofed: true
---

* Ignore for ToC
{:toc}

Yesterday, in the United States, we *vaguely* celebrated [Coast Guard Day](https://en.wikipedia.org/wiki/Coast_Guard_Day), the military's maritime humanitarian and security service, rather than---generally speaking, at least until the War on Terror---yet another fighting force.  Unfortunately, because they generally don't see combat unless transferred to the control under the United States Navy during wartime, we mostly ignore them except to complain about their response times to get out to boaters in distress in terrible weather...

![Drawing of a Guards-person in an old uniform looking across a divide at an officer in a modern uniform, with the claim of honoring the past, forging the present, and charting the future](/blog/assets/Coast_Guard_Day_2013_by_Cory_Mendenhall.png "Yes, I did briefly consider updating the end-year on that span...")

And on we go to the projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Since Thursday's post, some of you may have noticed another new addition to the blog's format, something that I have actually wanted from the beginning, but never occurred to me to quickly look up *how* to do it or give it the half-hour of thought required to come up with a solution.  That makes an absurdly long way around announcing that off-site links now try to give some indication of their destination, a bespoke icon---courtesy of the existing [Font Awesome](https://fontawesome.com/) font already deployed as a site asset, and which I should probably update, at some point---or a generic "outbound link" icon that you'll see for everywhere else.

For those who haven't seen the gimmick before, the code looks (something like) the following.

```css
a[href^="http"]::after {
	content: '\f35d'; /* The Unicode value for the external-link icon */
	font-family: 'Font Awesome';
}

a[href^="https://john.colagioia.net/"]::after {
	content: none;
}

a[href*="wikipedia.org"]::after {
	content: '\f266'; /* The Unicode value for the Wikipedia icon */
	font-family: 'Font Awesome 5 Brands';
}
```

All things considered, I don't really enjoy using Unicode code-points for non-Unicode characters, since I don't actually know how the Unicode Consortium might fill them up in the future, *but* it does the job in a way that people who have read Font Awesome's documentation will recognize.

In short, for the people having trouble following the mess, the first rule says that any `a` (hyperlink) element on the page whose `href` (address) property starts out (`^=`) looking like a URL should get the icon appended (`::after`) to the link, as a default.  I style mine to get them elevated and enlarge them on hover, but you can deal with that on your own time.  Then, the second rule says that, if the `href` property refers to this website---and I have other conditions, as well---then don't append anything.  Finally, if the `href` property contains (`*=`) Wikipedia's domain, use the Wikipedia icon instead of the default.

In this post, you'll see the Wikipedia rule applied in the introductory paragraph, the Font Awesome rule applied in the first paragraph of this section, and the generic off-site icon right in the next sentence[^1].  Because Font Awesome doesn't provide a huge array of brands relevant to the links that I've used, I haven't decided yet, but I may add a font like [Simple Icons](https://simpleicons.org/) to catch a wider variety, such as programming languages, crowdfunding payment processors, the Internet Archive, and so forth; I'll need to test to see if adding another font slows down the time before you get to read posts.  And honestly, further down that road, I could use custom icons for sites that I link to regularly, but don't show up in any of these semi-standard fonts.

[^1]:  I especially like this solution, because adding icons can happen silently and retroactively, whenever I add a rule to the list of websites, rather than my prior solution of manually inserting the Font Awesome glyphs in the rare cases that I could remember them.  Since all the work happens in the common stylesheet, and since it operates with a default rule (all hyperlinks) plus exceptions (per domain), then as long as a new font doesn't slow pages down, the icons don't need any more work than that.  I could also download the SVG images individually and serve them, but that seems worse for multiple images than one file.

Also, this doesn't tell the *entire* story.  For example, you'll notice that the links to the GitHub repositories on this page don't have the appended icons, since the context would make them redundant.  For a handful of select sites---such as GitHub and Mastodon, which I currently link to regularly and usually already with an icon in place---I have an additional rule eliminating the icon if the link element contains an italic-text element (`i`) with the relevant Font Awesome class.

```css
a[href*="github.com"]:has(> i.fa-github)::after {
  content: none;
}
```

That prevents this post, for example, from looking like I didn't pay any attention to things on the preview images to the right, similar to what you might see in the old [Social Media Roundup](/blog/tag/linkdump) posts that focused on Twitter, including [the first link dump in January 2020]({% post_url 2020-01-03-week %}), where the single-character links to my Twitter archive indicate show the original Twitter icon followed by a smaller GitHub icon, which has the virtue of making some sense once you understand the situation, but also looks bizarre to everyone who doesn't.  And since any links to no-longer-Twitter would now indicate that they go to &#x1D54F;---*if* I ever posted any, which doesn't seem at all likely---it didn't really seem worth carving out additional more specific cases for the much older posts.  Similar to adding another icon font, that decision may change in the future.

## Entropy Arbitrage...the Posts, Too

{% github jcolag/entropy-arbitrage %}

As I mentioned starting in [last week's developer diary post]({% post_url 2024-07-29-thai %}), I have continued adding Tables of Contents to old posts, accelerating the pace to quarterly instead of months.  At this time, I have finished the year 2022.

Along the way, I note with more than a little satisfaction that the contents only appear if the post has any subheadings.  For example, check out my 2023 post on [Normalizing Image Type and Size]({% post_url 2023-04-05-file-type-size %}) with other posts.  It doesn't have any table of contents, even though you can see the code for it near the top of [the post's source](https://raw.githubusercontent.com/jcolag/entropy-arbitrage/main/2023-04-05-file-type-size.md).

I had concerns about that, since a table of contents with no entries raises more questions than it could ever answer, so it pleases me that the Jekyll developers already worked that out.

## Fictopedia Archive

{% codeberg jcolag/fictopedia %}

I have finished updating the links on the individual pages for (I believe) the archive, though I have to imagine that I have overlooked something, given all this manual work.

Assuming that I somehow managed to not foul anything up, though, every page from [Ab'Nelgrik](https://jcolag.codeberg.page/fictopedia/Ab'Nelgrik.html) to [ZRPG](https://jcolag.codeberg.page/fictopedia/ZRPG.html)---and the couple of pages with names starting with numbers---should now have its internal links straightened out, the Fictopedia logo in the bottom-right, and a link to [their licensing page](https://jcolag.codeberg.page/fictopedia/00license.html) while specifying the Attribution license for their content.

I'll talk about the remaining work in a bit, but at this point, I'd call it "as usable as possible," given the amount of scavenging involved in restoring a project like this.  Many links still go into oblivion, because the target pages don't seem to exist anymore, not to mention that the Fictopedia community didn't exactly keep their categories clean.  However, within those constraints, if you want to refer people to the [Great Southern Railway](https://jcolag.codeberg.page/fictopedia/Great_Southern_Railway.html), the [Lubion Audio-Video Console](https://jcolag.codeberg.page/fictopedia/Lubion_Audio-Video_Console.html), [P. Barnaby Stanislaus](https://jcolag.codeberg.page/fictopedia/P._Barnaby_Stanislaus.html), [Trans-Fictional Vessels](https://jcolag.codeberg.page/fictopedia/Trans-Fictional_Vessel.html), or whatever else that might interest you in there, the pages won't go anywhere unless Codeberg has some catastrophe.

### Help?

The as-good-as-I-can-make-it milestone also makes this a good time to put out a call for help on this restoration project.  I can think of three major ways to help.

First, some of you might have access to pages that I don't.  As possible examples, you might have one of the following...

 * Your own little cache of pages that you spotted a decade ago.
 * An actual backup of the Fictopedia website, which would have made all this work pointless.
 * Better ability/luck than I had with the Internet Archive's Wayback Machine or Archive Today.
 * Knowledge of long-term web archiving projects that I haven't seen.

You get the idea.  If you can scrounge up original Fictopedia content that I don't have, get in touch, and we'll see about getting it into the same format as everything else.  The missing pages might have no content beyond a title, making this request a waste of everybody's time.  Or maybe we'll find out that we need *So You Think You Can Put Out A Fire* on our television schedules.

Likewise, I continue to not want to make any editorial decisions on the pages, so that I don't step on one of the larger community efforts in Free Culture history to turn the archive into my take on their universes.  And while I wouldn't recommend making significant changes to pages, if somebody wanted to go through adding categories or cleaning up some of the weirder phrasing, please file pull requests.

{% imgr [Fictopedia]|Fictopedia-Logo.gif|The Fictopedia logo, the name displayed in brackets %}

Finally, I have one more request, here:  Can anybody identify the font used in the Fictopedia logo, shown to the right?  Because of its tiny size and poor contrast against anything other than extremely light backgrounds, especially with the partial outline, I have wanted to replace it with (ideally) a vector image, but short of picking a modern font and not caring about how well it matches---which feels inappropriate and counter-productive---I can't find anything that comes close, except for one possibility[^2] where I need to play with the kerning to get even close, and that ends up looking like a mess.

[^2]:  [TT 2020, Style E](https://copypaste.wtf/TT2020/docs/download.html)'s serifs look too long on the lowercase-*i*, it doesn't quite have enough of a tail on the lowercase-*a*, and---as a monospaced font---doesn't pack together correctly, but it comes close on other points.  But also, the name suggests that it probably didn't exist at the time that people worked on Fictopedia.  A handful of other fonts that I've found have the right traits, but don't look at all right in practice.

## Next

This week, I'll wrap up the remaining issues that I have (and can fix) with the Fictopedia archive, and also should finish off adding tables of contents to old posts, plus finishing off the remaining issues with the site-icons.  After that, I should probably add a personal page of my own onto Codeberg Pages, and will also need another repository somewhere for some experimental work that I've hinted at for a while.

Depending on whether adding Simple Icons to the page bogs things down, I may also pull out another round of link-icons, and maybe do something similar for code snippets, like you saw in the first section.  Since I specify the programming language in the Markdown for each block of code to get the right highlighting, they get tagged with CSS classes, such as `language-css`, above, which [Prism.js](https://prismjs.com/) uses to highlight the code and whatever else it needs to do.  But I can do the same thing, using the same technique as above---but with the classes instead of element properties---to show a default "code" icon, and replace it with more specific icons for JavaScript, Ruby, CSS, and the other languages that I write...I think.

Oh, and time permitting, I may also consider one other major change to the blog, especially now that I've started thinking about performance and only now realized that I have probably ignored the most significant aspect of that, on a per-post basis.  But I want to make sure that, if I do so, I don't end up making much more busywork for myself.  Make much more busywork for myself *again*, I mean.

* * *

**Credits**:  The header image is [Coast Guard Day 2013](https://web.archive.org/web/20151006021308/http://allhands.coastguard.dodlive.mil/files/2013/08/Coast-Guard-Day-2013.jpg) by [Petty Officer Third Class Corey Mendenhall, United States Coast Guard](https://web.archive.org/web/20210416102556/http://allhands.coastguard.dodlive.mil/2013/11/22/the-drawing-board-remember-those-standing-the-watch/), in the public domain as a work of a United States employee made as part of their duties.
