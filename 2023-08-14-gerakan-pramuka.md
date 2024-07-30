---
layout: post
title: Developer Diary, Gerakan Pramuka
date: 2023-08-14 06:56:05-0400
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Gerakan-Pramuka-Indonesia-Scouts-8th-Indonesian-National-Rover-Moot-2003.png
teaser: This week's projects include Notoboto (my new note-taking app replacement) and not much else.
spell: Gerakan Pramuka Notoboto Anakmadiun Unported Tcl Tk pnl kabang
proofed: true
---

* Ignore for ToC
{:toc}

While more recent than I would generally prefer, today marks the 62<sup>nd</sup> anniversary of the founding of the [Gerakan Pramuka](https://en.wikipedia.org/wiki/Gerakan_Pramuka_Indonesia), Indonesia's home-grown youth scouting organization, founded to overhaul the prior scouting movement to erase its British influences.  I wouldn't say that I find these organizations comfortable or devoid of criticism, but I do appreciate the sentiment of wanting to decolonize the institutions that affect the youth.

![Indonesian Scouts at the 8th Indonesian National Rover Moot July 8-17 2003](/blog/assets/Gerakan-Pramuka-Indonesia-Scouts-8th-Indonesian-National-Rover-Moot-2003.png "See, I would've called epaulets and a cloak too much, but he makes them work...")

Since I occasionally notice in the blog's analytics that I have more Indonesian readers than I would generally expect, I'll also take today as an excuse to greet them and encourage them to tell us in the comments whether "decolonized" makes sense, here, and any experiences with the movement that they'd like to share.

And with that out of the way, I'll talk about a few projects.

## Notoboto

{% github jcolag/Notoboto %}

This week has gone entirely to note-taking.

Granted, it doesn't rate as anything like a fully functioning application yet, but it does have a window layout that mostly matches my target.  In that code, you can see Tcl's peculiar-but-maybe-satisfying user interface layout code.  Rather than syntactically nesting the controls in a tree, or---*ugh*---manually placing every widget with `container.addChild(button34)` nonsense everywhere, it names the controls with nested names such as `.fr.pnl.choose.reload` for the reload button in the choose panel in the side panel in the main window.  Then, each widget can have a `pack` directive to specify where in the container it should sit.

The window also has a title and (mediocre) icon, which doesn't *sound* like a huge step, but given the fact that [Proton/Valence Native](https://github.com/valence-native/valence-native) never added the ability to do that before everybody (apparently) walked away from the project, so it feels like a meaningful milestone to me.

I've also started fleshing out the first bits of the handlers for the widgets, though not much.

## Next

I'll continue with **Notoboto**, for the most part; since I need to take notes.  And at some point, I need to consider whether to continue with the Markdown-embedded-in-CSON note files, or convert them as I make changes and export them to something easier to parse, such as Jekyll's Markdown-with-metadata.  Doing so would make them easier to maintain, but it would create a discontinuity in the history in version control and leave me to decide what to do with the original files.

Thinking about it, I should also mention that, despite the age of the overall Tcl/Tk platform, or maybe because of it, the widgets seem significantly more mature than what I've found on most platforms where one can build an interface without much trouble.  For example, it seems [possible](https://tkdocs.com/tutorial/text.html) to format the text in-place, so that the application doesn't need a separate preview of the Markdown, for example.  Because of that, you might see this program outgrow its original specification and become a more comprehensive system, as long as it doesn't bog down the machine.

Oh, and as I wrote yesterday, I need to stash the [**Kabang!**]({% post_url 2023-08-13-kabang %}) code somewhere, so you might expect a repository for that, as well.

* * *

**Credits**:  The header image is slightly adapted from [Gerakan Pramuka Indonesia Scouts 8th Indonesian National Rover Moot 2003](https://commons.wikimedia.org/wiki/File:Gerakan_Pramuka_Indonesia_Scouts_8th_Indonesian_National_Rover_Moot_2003.jpg) by [Anakmadiun](https://en.wikipedia.org/wiki/User:Anakmadiun), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
