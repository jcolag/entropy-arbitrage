---
layout: post
title: Developer Journal, Hugo Gernsback's Birthday
date: 2021-08-16 06:32:23-0400
categories:
tags: [programming, project, devjournal]
labels: [doritis-onomaton, flutter, fylakas-onomaton]
summary: Progress on assorted projects
thumbnail: /blog/assets/blythe-hugo-gernsback.svg
offset: -54%
---

* Ignore for ToC
{:toc}

Today has a variety of interesting anniversaries, such as what was then [Tōhoku Imperial University](https://en.wikipedia.org/wiki/Tohoku_University) becoming Japan's first university to admit women as students or the [Battle of Plymouth](https://en.wikipedia.org/wiki/Battle_of_Plymouth), but what caught my eye was the 137<sup>th</sup> birthday of [Hugo Gernsback](https://en.wikipedia.org/wiki/Hugo_Gernsback), often called "the father of science fiction."  Gernsback was often a clumsy writer, but he pioneered many ideas that either predicted technological developments or became established tropes of the genre.

![Hugo Gernsback](/blog/assets/blythe-hugo-gernsback.svg "Sadly, the picture of him wearing television-goggles is still under copyright...")

Especially if you enjoy stories about adventurers who overcome overwhelming odds with the help of gadgets that sound semi-plausible, as long as you don't think about them too hard, then you probably owe Hugo a moment of thanks on his birthday.

However, you're probably here for code, and Gernsback didn't do much of that, as far as I know...

## Fýlakas Onomáton

Remember when I said that [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton) was basically finished...?  It turns out that I *may* have spoken too soon.

*This* time, while going through [Rubocop](https://rubocop.org/)'s advice, I stumbled through a variety of bad practices that were bugs in the cleaner version.  The lesson being that you should *start* with the cleaner version to maximize the bugs found early, not that I shouldn't have improved my code.

Not counting stock Rails code or non-manual code, the only issues that I have remaining are one over-long controller and one over-long function that Rails generated.

The page styling now *also* doesn't look terrible.  It's still not perfect, but it has a distinctive color scheme and takes advantage of [Bootstrap](https://getbootstrap.com/).  I may regret this later, after I realize that I should have just used a [Material Design](https://en.wikipedia.org/wiki/Material_Design) library to match the app, but that's future-John's problem.

## Doritís Onomáton

Likewise---speaking of the app---it looks like the library that I decided to use to store the API key in [**Doritís Onomáton**](https://github.com/jcolag/doritis-onomaton) doesn't *actually* create any permanent storage.  It persists when reloading the app, but not when stopping and restarting it, which isn't useful.

So, I decided to retreat back to [Shared Preferences](https://pub.dev/packages/shared_preferences).  I finally found a tutorial---why can't Flutter just document things instead of having developers post full-app tutorial articles on Medium?---that doesn't stuff all the code into asynchronous functions, then leave it as an exercise to figure out how to access those functions from the synchronous app.  It's probably not worth going into the details, but those directions were for later versions of the SDK.

So, that meant updating **Doritís Onomáton** to the latest Flutter, which in turn required the latest HTTP library and some code updates for NULL-safety.

And the result?  The app *still* won't persist data between sessions.  Hot-reloading, yes.  Quitting and restarting, no.  But...maybe that's OK.  You see, when inspecting the app in Chrome, I notice that the app has a local port number associated with it, which *changes* every time I run the app.  So, it's possible that the "problem" is just that the minimal documentation doesn't bother to say "different runs in the debugger are actually different apps, using different local storage," and I basically wasted a few days' of work.  The theory needs deeper investigation to confirm, but it explains why nobody mentions this problem in documentation or tutorials, and all the relevant Stack Overflow questions or GitHub issues seem to be from people who either aren't particularly invested in the ecosystem or have a much more specific problem.

So, I'm going to save that issue for testing on real devices.

### Preliminary Flutter Assessment

I should mention that I originally looked at Flutter, because there were rumors that [Ubuntu](https://ubuntu.com/)---which I happen to use---has been considering making Flutter an "official" way to create desktop applications.  So, the idea of dipping my toe into the mobile world *while* possibly learning how to develop my next desktop software was compelling.

I don't know how valid that rumor is, by the way, so don't take that as anything official.  I am one of the least "plugged-in" people actively using Linux...

Anyway, this week seems to have hit all the frustrations in working with Flutter.  Basic development is easy enough, if you've already worked on user interfaces in other systems.  However, official documentation will sometimes just link to a Medium post that only *barely* mentions the topic.  Or the documentation will be vague, and tutorials rely on specific versions of libraries---past or future, since your app may have been generated with an earlier version---with breaking changes.  Many tutorials only solve half their problem, assuming (probably rightly) that the other half is easy, *but* ignoring the part where someone bridges between the two worlds.  And there are issues like this persistent data situation, where nobody gives a straight answer.

And on top of that, since Flutter actually runs in a Chrome---or Chromium, I didn't actually check---window, with Dart compiled to JavaScript, so it's all *more* resource-intensive to run than an Electron app.  My laptop can only barely handle testing, and it's currently the most likely task to force a reboot.

## Next

For this week, I'll pick fonts for the **Fýlakas Onomáton**, take another pass adjusting the colors for tables, and probably wire up small things like the JavaScript to change between light and dark modes; I tossed in the styling to handle it, but didn't bother to finish.  After that, the top priority is to get it running on Heroku.

Testing **Doritís Onomáton** is also a priority, especially making sure Shared Preferences does actually retain data, if the user's phone/tablet reboots.  Oh, and I need to find and package up device information, when activating a device.

Otherwise, library updates are piling up, again, so that should take care of the week.

* * *

**Credits**:  The header image is [Hugo Gernsback c.1929](https://commons.wikimedia.org/wiki/File:Hugo_Gernsback_SWS_2911.jpg) by William Edward Blythe, apparently in the public domain for failure to renew the copyright.
