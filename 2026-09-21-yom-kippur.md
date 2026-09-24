---
layout: post
title: Developer Diary, Yom Kippur
date: 2026-09-21 07:53:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, library-update, mini-server, recipe]
summary: Progress on assorted projects
thumbnail: /blog/assets/Jews-Praying-in-the-Synagogue-on-Yom-Kippur.png
offset: -26%
description: This week's projects include general computer management, a recipe, an incubator, de-AI-ing old blog images, the blog's code, and library updates.
spell: de-AI-ing Maurycy Pinebook Guix ReactOS VrkXrs fs codepage Udoo Parallella miso endcook Kabang iCfGLV Nonogram Salavi
proofed: true
---

* Ignore for ToC
{:toc}

Today---from last night's sunset to tonight's---marks {% wiki Yom Kippur %}, the Jewish Day of Atonement, centered on (to nobody's surprise, given the term) atonement and repentance.

![Maurycy Gottlieb's rightly famous 1878 painting of a Yom Kippur prayer including the artist himself](/blog/assets/Jews-Praying-in-the-Synagogue-on-Yom-Kippur.png "For the curious, the guy in a headband and what looks like a Mini Metro sweatshirt pretending not to look at us also painted the scene...")

These days, I always forget to check the holidays on Lunar calendars[^0Q6mRZ], so I want to cycle more in, and what better an example than probably the most important?

[^0Q6mRZ]:  Because I went to a school and had a couple of early jobs that regularly put me in contact with people around the world (at a time when not many people had access to anybody overseas), I *used* to start the day checking every calendar that I could get my hands on, including Jewish calendars.  Then I stopped using calendars entirely for years, since I could schedule reminders for any big events without the structure, and that practice fell by the wayside...

And with that, on to the week's projects.

## Mini-Server, Part 33

The Pinebook has gone back into limbo for the moment, to my annoyance, because I have run out of viable options for a fresh operating system.  As I mentioned recently, when you rule out operating systems that have a policy allowing LLM-generated "contributions"---a time-bomb that'll either put Software Freedom at risk for everyone using the system or turn it into an unmaintainable mess---that doesn't leave me[^d41g0k] with many options.

[^d41g0k]:  Feel free to raise others, if I've missed something with a no-AI policy from kernel to UI.  Much as I have liked working with Linux, their embrace of LLMs puts every distribution on an unstable foundation

- GNU [Guix](https://guix.gnu.org/) with the [Hurd](https://www.gnu.org/software/hurd/advantages.html) kernel
- [Haiku](https://www.haiku-os.org/)
- [Inferno](https://www.vitanuova.com/inferno/)
- [NetBSD](https://www.netbsd.org/)
- [Plan 9 from Bell Labs](https://p9f.org/)
- [ReactOS](https://reactos.org/)

By the way, this list does *not* get to the second filter, the not-run-by-fascists-or-abusers rule.  I assume that they'd pass, because I don't hear anybody grumbling about them from that perspective, but I have only seen evidence that Haiku comes from a healthy community.

Anyway, sitting down to actually get the laptop going, Haiku and ReactOS don't support {% wiki AArch64 %} at all yet, from what I can tell, or at least don't provide a build for it.  Guix *technically* provides a download, but distributes it as a TAR file of the file system, which would require logging into the machine (therefore installing something else) to overwrite the drive with this; Hurd on 64-bit systems also sounds shaky, from what I can gather.  Neither Inferno nor Plan 9 has gotten an update in four-to-six years, and of the forks of each that do still get updates---[Inferno 64](https://inferno64.org/) and [Nix](https://nixos.org/)[^VrkXrs], respectively---both make room for LLMs; they (Inferno and Plan 9, I mean, not derivatives) both also seem to ship under the assumption that everybody runs their system as an application on some other operating system, rather than installing it directly to hardware.  That rules them all out, at least for this purpose.  For an {% wiki IA-64 %} machine (and I do have one that'll require an operating system, once I get it running again) that will probably change for at least some options.

[^VrkXrs]:  I know that my circle includes a disproportionate number of people using Nix, so I apologize for that revelation, if you hadn't heard it from someone before me.

The remaining option, NetBSD, *has* an explicit Pinebook download, but after writing it to a USB drive, I can't read the drive on my "normal" laptop that wrote it.

> Error mounting `/dev/sda2` at `/media/path/...`: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error

Oh, thanks for clarifying that, narrowing it down to *any possible error*.  {% emoji eyeroll %}

And unsurprisingly, the Pinebook ignores the drive.  Same results for another one, hoping that the first had somehow gotten damaged.  I don't consider that a *permanent* failure, but it does stymie getting the machine running at this point, unless I compromise and accept the LLM-generated code in the Linux kernel and go with something like [Elementary OS](https://elementary.io/), at least temporarily.

Meanwhile, I still haven't tried removing the heat sink from the other mini-PC[^2hTmhB], but I did unearth more single-board computers that I assume came from Kickstarter campaigns however long ago I still played around there.  Ah.  It looks like I [identified them in January]({% post_url 2026-01-26-duarte %}) (then immediately lost track of them again) as an [Udoo](https://www.udoo.org/) Dual and Quad, and two from [Zero ASIC](https://www.zeroasic.com/)'s Parallella project.

[^2hTmhB]:  If I haven't mentioned it before, I finally got to the side of the motherboard that houses the CPU and got the fan out of the way.  Now I see a copper sheet (slightly tarnished) with two copper "fingers" draped across it, which I *guess* makes a heat sink, but also don't see where I'd access the CPU underneath it, even to pry it off.

The former (for anybody interested in that sort of thing) seems to have a normal (if old) ARM-architecture (32-bit) processor with an Arduino---before they went mostly proprietary and fascist---and a GPU.  The latter seem to include an ARM-architecture (32-bit) processor and sixty-four [Epiphany {% cc %}](https://web.archive.org/web/20121020235739/http://www.adapteva.com/wp-content/uploads/2012/10/epiphany_arch_reference_3.12.10.03.pdf) cores for parallel processing.  I might see if I can find a use for them, even if nothing more than a backup...though I'd need more micro-SD cards to get them going.

## Recipe

We have a couple of interesting-to-me items, food-wise.

### Pesto

I have probably mentioned it before---probably in association with all my work over the summer working out reliable bread recipes---but as a recurring quick dinner, I'll often make an eggplant sandwich.  Fry or broil (depending on the temperature) slices of eggplant.  Drop them on a roll or hefty bread slices with crushed garlic[^Qm2XkU] and either (good) Parmesan cheese or (increasingly, not least because it takes much less work than grating cheese) white miso.  If I had the foresight to buy eggplant on sale, slice it, and freeze the slices, then it doesn't take much time.

[^Qm2XkU]:  You can also fry or broil the garlic alongside the eggplant slices, if you don't like the sharpness of the raw cloves, but watch it carefully so that it doesn't burn, flipping it or pulling it out when you see it turning golden brown.  I actually like to mix both raw and cooked.

I didn't write this to give you *that* recipe, because you can probably figure that out for yourself.  However, when I saw a different vegetable on sale during the week, a memory clicked of about twenty years ago when I experimented with {% wiki pesto %}, something that you probably know as basil and pine nuts, but plenty of people substitute ingredients.  Most commonly, you'll see people swap the (expensive) pine nuts with any convenient nuts and increasingly legumes, but the vegetable adapts without much trouble, too.

And then I realized that, since my eggplant sandwiches use a majority of pesto ingredients---oil when frying, garlic, and cheese or white miso---then I could make pesto and use it as a spread for the sandwich.  *That* recipe, you get.

{% cook 1|Asparagus Pesto %}
Grind @asparagus{5 cups} (chopped), @garlic{12 cloves}, @walnuts{¼ cup}, @olive oil{¼ cup}, @white miso{3 Tbsp}, and @lemon juice{1 Tbsp} to a smooth paste.  Thin with more oil if preferred.  Season to taste.
{% endcook %}

Now, it *looks* pretty sad---imagine the palest pastel green---but it makes a great sauce or even spread on...pretty much anything.  When I had the idea all those years ago, I especially used it on egg sandwiches and as a sauce for fish.

I used my food processor to grind everything together, but pesto definitely precedes the existence of such devices, so use whatever you feel like using to get paste out of it.  A significantly younger me would've happily spent a few hours trying to work through everything with my mortar and pestle, convinced that I bought it for that specific purpose, but I stopped finding that sort of thing fun over the years.  Oh, and this filled about two sixteen-ounce jars after making my sandwich.  I hope that the lemon juice will keep it from browning and (later) going bad.

Yes, you'll need to live with---how can I put this delicately?---the *adjustment* to the smell of your urine for a couple of days per serving.

If the sickly color bothers you, I used to add a handful of spinach to give it more of a green color.  I also added horseradish at one point, and liked that, so interpret "season to taste" *extremely* broadly.  Honestly, once you know what to look for and have a general sense of the ingredient proportions, you can add or substitute almost anything.

### DIY Incubator

Oh, and I think that I promised that, when the last of the equipment finally came together, I'd provide a picture of my incubator.

![An oven with a dimmed lightbulb hanging from a high rack](/blog/assets/diy-incubator.png "Please ignore the current non-pristine state...")

For the first version, it doesn't have much of a brain.  The incandescent bulb---leftover from years past---plugs into a lamp cord, with a chandelier-to-E26 converter, because they sent me the wrong cord.  Out of view, that plugs into a dimmer box.  On the bottom rack, I have my trusty pizza stone that I don't think that I've ever used *for* a pizza.  I have a probe thermometer that I can clip or tie next to what needs to stay warm, which should work well enough for *most* fermentation, as well as helping bread rise.

If this does the job---I didn't receive the socket adapter until the weekend, so it hasn't gotten a rigorous test---then I can optimize it by replacing the dimmer with an actual thermostat, and the light bulb can become one of those ceramic heaters used for small reptile enclosures, which would presumably last longer and burn less energy for the amount of heat, since *light* now represents the waste energy.  Similar to the lamp, if I run across someone tossing a broken dorm fridge, that would turn this into a standalone unit where I won't need to take any care using the oven.

And for the money-curious, only the dimmer cost serious money at twenty dollars.  A smarter person would've waited for someone throwing out a broken lamp to salvage its cord (I know that I've seen thrift shops throw them out routinely), but that and the adapter cost about twelve bucks.  And then however much the light bulb (the last bulb in a pack of six) and thermometer cost however many years ago when I bought them.

For a minimal test---light bulb on full blast and nothing else in the oven but the thermometer probe clipped to the pizza stone on a relatively chilly day---the temperature rose over about an hour to get up to ninety degrees Fahrenheit, then I cut the bulb's power to about half, where it held the temperature at 93°F for another hour, making me think that this should work fairly well until it burns out the remaining light bulbs.  With any luck, I'll report back next week on something more interesting.

## Entropy Arbitrage, the Posts

{% codeberg jcolag/entropy-arbitrage-posts %}

I finally returned to [replacing the old AI-generated images]({% post_url 2026-03-16-smugglers %}#entropy-arbitrage) that I experimented with in 2023.  I never resorted to that often, only a total of eight posts out of the nearly seventeen hundred on the blog so far.  Once it became clear that they'd never live up to the hype *and* the industry would never account for the massive problems that they cause, though, I have wanted to replace what I have.

Six months ago, I took care of [Developer Diary, World Freedom Day]({% post_url 2023-01-23-freedom %}), [Five Stages of AI Grief]({% post_url 2023-02-26-ai-grief %}), [Archive of Our Own, part 1]({% post_url 2023-07-15-ao3-1 %}), and [Archive of Our Own, part 2]({% post_url 2023-07-22-ao3-2 %}), replacing the garbage-from-prompt with either a stock image that could have equally fit the post or a reconstruction of what I had originally visualized when I handed the job to the bot.  This time through, I did the same for [Real Life in Star Trek, *Evolution*]({% post_url 2023-05-04-evolution %}) and [**Death off the Cuff**]({% post_url 2023-05-20-death-cuff %}), with the same pair of techniques, though the latter post slightly improves on the formula by using a digital painting---I hope made entirely by a human---instead of a random stock photograph.  I also replaced the mock-up "arcade cabinet art" for [Announcing **Kabang!**]({% post_url 2023-08-13-kabang %}) and found a font that fit my vision for the logo, though I should get a new melody for the game, since I let a chatbot generate the sixteen-or-whatever-note theme.

That leaves the post that presents the most annoyance, also the chronologically first of the posts, ignoring the remaining **Kabang!** work.  [*Whatever Happened to Social Media?*]({% post_url 2022-11-13-social %}) uses a bunch of fake headshots as fake social media profile pictures, which would take significantly more work to replace well (since they need to match the character concepts) with less value added to the post in making the change, due to the tiny size.  That'll require a lot more thinking than the images for the other posts, so don't necessarily expect it to change soon, but know that I do have it on my agenda.

## Entropy Arbitrage, the Code

{% codeberg jcolag/entropy-arbitrage-code %}

Some unnecessary code---some work in progress and some subtle[^iCfGLV] debugging code that has annoyed me for a while---got the boot, at least from the repository.  It shouldn't have gotten checked in yet, certainly, even though it deploys with the site.  The "stop calling the Book Club reviews" note should read more smoothly, too.

[^iCfGLV]:  In one of the plugins, returning some HTML somehow got a print command mixed in, as in `return p "<whatever><html><code>"`, so the rebuild log got clogged up with those results, *but* with only a one-letter (and one space) problem, it slipped past me every time I tried to track it down.

You'll also see annotation icons for the rare links to [Arch Linux](https://archlinux.org/), since that came up recently.

The "secret" feature that I've had in the works for a while---allowing readers to save pages to return to later---also finally has almost everything set in place.

## Library Updates

I needed to bump library versions for my [Morning Dashboard](https://codeberg.org/jcolag/dash), [Picture to Nonogram](https://codeberg.org/jcolag/picture-nonogram), and [Salavi](https://codeberg.org/jcolag/salavi).

## Next

I expect that this week will look a lot like last week, for the most part.

Although, even though I only worked with it indirectly, replacing the AI images convinced me that I should probably revisit **Kabang!**, especially since a new version of the TIC-80 dropped as I did it.

* * *

**Credits**:  The header image is [Jews Praying in the Synagogue on Yom Kippur](https://en.wikipedia.org/wiki/File:Maurycy_Gottlieb_-_Jews_Praying_in_the_Synagogue_on_Yom_Kippur.jpg) by Maurycy Gottlieb, long in the public domain due to expired copyrights.
