---
layout: post
title: Developer Journal, Indigenous Peoples Day
date: 2021-08-09 06:34:23-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Nama-man-greeting-us-3693359757.png
offset: -27%
---

![A Nama man playing a traditional greeting](/blog/assets/Nama-man-greeting-us-3693359757.png "A traditional Nama greeting")

Today marks the [International Day of the World's Indigenous Peoples](https://en.wikipedia.org/wiki/International_Day_of_the_World%27s_Indigenous_Peoples), which I admit is a terrible name, given that we're all indigenous to the *world*.  But with development occurring at a rapid pace and so many languages precariously close to going extinct, it's worth taking a day to think about the real cultural diversity that most of us never see.

Anyway, let's make some new culture with weird code...

## Ham Newsletter

It occurred to me after sending out the most recent [**Entropy Arbitrage** newsletter](https://entropy-arbitrage.mailchimpsites.com/) that the month names have been when I *send* the newsletters, rather than the month that the newsletter covers.  I don't know why I didn't notice that before, but [**Ham Newsletter**](https://github.com/jcolag/ham-newsletter) is now fixed, and I apologize to anybody who has been confused by the titles.

On September 4<sup>th</sup>, you will see the newsletter for *August*, as you should.  The newsletter marked for September will go out on October 2<sup>nd</sup>, and so forth.  Again, that's what it should have done all along.

## Entropy Arbitrage

Apart from the newsletter, I also updated the [**Entropy Arbitrage**](https://github.com/jcolag/entropy-arbitrage-code) code's verbiage for signing up to the mailing list *and* finally checked in the adjustments to the [Twitter roundup](/blog/tag/linkdump) post generation script to account for the new semantic plugins.

Unlike the pull quotes, I won't be going back through every Friday post to correct the quote citations, at least not immediately.  There's so many of them, that the only reasonable way to do the work would be to coerce [`sed`](https://en.wikipedia.org/wiki/Sed) to find the rogue headings and replace them with tags.  But that's likely to be ugly and error-prone, so I'm going to hold off until I have a day or two to mess around, especially since no post *legitimately* ever uses (or is likely to ever use) a sixth-level heading where the styling of them makes a difference.

Regardless, going *forward*, posts should never abuse headings again.

## Fýlakas Onomáton

I needed to overhaul [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton)'s activation code, after stumbling over a couple of conflicts between the website and the app.  Both interfaces should now be able to use the controller successfully.

Speaking of which...

## Doritís Onomáton

It currently requires a manual check---clicking a button on the activation screen to refresh, rather than working silently in the background---but [**Doritís Onomáton**](https://github.com/jcolag/doritis-onomaton) can now check the status of an activation code and retrieve/store the corresponding API key, like it should have *weeks* ago.

At least for the duration, I'm calling the app and server feature-complete.  I may mess around with the code organization, will need to fix any bugs that come up, and may try to figure out Flutter's internationalization feature.  But other than those issues, I don't expect **Doritís Onomáton** to change much, beyond this point.

## Next

This week, I'm going to take care of the styling on **Fýlakas Onomáton**, so that it at least looks somewhat reasonable, toss it up on a cheap server, and start looking into submitting **Doritís Onomáton** to the app stores.

Most of that has nothing to do with code, though.  So, while I'll mention progress in these posts, the final process will get its own Wednesday [tech tip](/blog/tag/techtips) post.  And for the rest of the week, I have some libraries to update, probably some old work that I've forgotten to check in, and maybe I'll try to throw in another project.

* * *

**Credits**:  The header image is [Nama man greeting us](https://commons.wikimedia.org/wiki/File:Nama_man_greeting_us_%283693359757%29.jpg) by Greg Willis, made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) license.
