---
layout: post
title: Developer Diary, World Architecture Day
date: 2026-10-05 07:56:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, kabang, library-update, newsletter, social-media]
summary: Progress on assorted projects
thumbnail: /blog/assets/Himeji-Castle-The-Keep-Towers.png
offset: -26%
description: This week's projects include a newsletter reminder, (something like) a social media update, Kabang!'s release, the blog's code, and some library updates.
spell: Automattic kabang CPREP Fýlakas Onomáton Kanopy CXOHCk Pinebook JumpDrive Nura Glo Roku microSD Reggaeman
proofed: true
---

* Ignore for ToC
{:toc}

Today marks the (maybe surprisingly) unpopular World Architecture Day, backed by the {% wiki Australian Architecture Association %}.  Celebrating architecture seems reasonable...

![Himeji Castle's Keep Towers](/blog/assets/Himeji-Castle-The-Keep-Towers.png "I considered going for South American, here, but didn't want too new a building")

And as I have surely mentioned before, the first Monday of October also marks {% wiki World Habitat Day %}, with this year's theme *Adequate Housing for All*.  Housing figures into more of these than I would've guessed, actually.

And with that, on to the week's projects.

## Newsletter Reminder

On the chance that somebody needs or wants the additional nudge, the September [newsletter](https://www.buymeacoffee.com/jcolag) will go out tomorrow morning.

## Social Media

I suppose that these only technically qualify as updating social media, but I did want to point them out somewhere.

### Beeper

I can *no longer* recommend [Beeper](https://www.beeper.com/), and no longer use it.  Most likely, this became inevitable when {% wiki Automattic %} bought them out, but I tried giving them more chances.

For those unfamiliar, their software mostly looks like Matrix's [desktop Element application](https://matrix.org/ecosystem/clients/element/) (and mobile counterpart), but with "bridges" to proprietary services.  It then presents a LinkedIn, Facebook, Discord, or whatever kind of contact as another Matrix contact...but *not* your Matrix contacts, because you need an account on their servers.  A nice idea for getting off the proprietary websites, even if the application devours resources and makes some peculiar choices.  That said, I came here to *not* recommend them, because I needed to drop it.

You see, for the second time this year, they sent a perky message informing me that, overnight, their elves disconnected me from every service that they decided that I didn't use enough.  The first time, it didn't really sink in, so I asked why they would read my messages, and they responded with some hand-waving about only seeing that messages go in and out, not the contents.  Those connections cost them money, allegedly, and they can push that cost on me as labor to save themselves a few pennies per year.  I rolled my eyes and reconnected everything.

This time around, they did it again, and...I don't see the point of the application, at this point.  They run these purges---allegedly no outbound traffic over thirty days, in response to my "what the heck" inquiry[^CXOHCk], but that doesn't match what I see---seemingly whenever they feel like it and with no notice.  And while I considered finding bots on various services to send messages to every four weeks to get around their policy, it also dawned on me that the policy seems to exist to push people away, and I see fewer reasons to disagree.

[^CXOHCk]:  Infuriatingly, they also consistently respond to problems by thanking me for my feedback, as if I described problems in an advisory role instead of because I *need them fixed*.  I guess better that than fake empathy, though...

After all, I thought of Beeper as a tool to decrease reliance on proprietary messaging services, but they build it to increase such reliance, instead.  In fact, that occurred to me as I started dreading going through ever service to re-authenticate again, making ever single service far more prominent.  And if they make this a test every thirty days, then I'd need to think about those services every month, instead of letting them fade into the background until somebody tries to contact me on one.

Their website pitches it as one place for all messaging, but (a) you could say that about web browsers, too, and (b) Slack, Discord, Teams, and every other modern chat application claims the same thing, so we should assume the same eventual business where we'll need yet another unified inbox to account for Beeper in a few years.  But also, that message monitoring bothers me, especially when combined with their (and Automattic's) flightiness:  If they count the number of messages going in and out, then it only takes a couple of lines of code to harvest the actual messages or log everything on the machine, if the boss decides that he wants to sell user data to Midjourney and OpenAI like they already did with WordPress and Tumblr.  In that vein, it doesn't take much imagination to picture that "inactivity" guideline weaponized further, to pressure users[^HNgK7L] into using certain services.

[^HNgK7L]:  In fact, while support thankfully doesn't bring it up in conversations, it does seem clear that they do this to pressure users into spending the ten dollars per month for their paid tier to avoid their going out of their way to degrade service.

By the way, if you want another red flag, check out the footer of their website.  How can you connect with the team?  They have accounts on {% x %}, LinkedIn, and GitHub, nowhere else, not even Matrix, which they built everything on.

Anyway, all that to say that it didn't seem worth the effort of re-authenticating or running their heavy application to do it.  I outlined my concerns in a message for the support team to ignore, and closed it down.  If, then, you reach out to me on one of those services, then I'll get to it when I get to it...

*Maybe* I'll try to run it on one of my servers, but [the instructions](https://developers.beeper.com/bridges/self-hosting/) give the impression that this wouldn't distance me from their infrastructure, and I don't know if it'd work running on my local network.

### Itch

I'll get into more detail later, but I should note that, while I don't expect to socialize there, you can now [follow me on Itch](https://jcolag.itch.io/), where I have now released two things, and have started looking at other projects that would fit.  For any such releases, I'll only mention rehabilitated "old" projects in these Monday posts.  New projects---I started thinking a while ago about putting together an anthology of my short stories, for example---will get an announcement to the newsletter subscribers before here...provided that I remember.

Oh, and since I now have two things uploaded to Itch, I decided to add the link to my Mastodon profile.

## Mini-Server, Part 35

I have had some motion, after getting myself some micro SD cards, though not much to show for it yet.

First, it looks like the Pinebook does *not* boot from USB drives at all, only from a card, explaining my problems last week.  I flashed [NetBSD](https://www.netbsd.org/) to one card, since they build specifically for the Pinebook *and* released v11 during the week.  The laptop dutifully booted from the card, and...did...something.  It looks like a boot sequence, but it doesn't end up anywhere like an installer or a user interface, not even a login prompt.

Associating the SD card with a Pine-something reminded me that I had a forgotten PinePhone that I set a solid password on and immediately locked myself out of, because I couldn't guess my own password.  While I haven't touched it since then, I bought it with the intent of using it as a "computer of last resort," an ultra-low-power device that, with an optional external keyboard and bigger screen through the USB port[^KxJ2Gt], can keep me in contact with people and so forth.  With my in-house servers, that becomes even more compelling as a backup, since that backup device doesn't need to even consider supporting a podcast client, IDE, office suite, RSS feed reader, image editor, calendar, mail client, and so forth, for me to get back to (something like) normal.

[^KxJ2Gt]:  Pine actually sells probably their most valuable product, a USB3 dock/dongle with a USB3, HDMI, Ethernet, and two full-size USB ports out.

At the time, Pine had no way to "factory reset" the box---you can probably find me asking about it on the company's forums, if you poke around---but someone has since created [JumpDrive](https://github.com/dreemurrs-embedded/Jumpdrive).  I flashed that to a card, inserted it into the phone[^c13eVX], plugged the phone (USB3) into the laptop, and *wow* does their [list of PinePhone operating systems](https://wiki.pine64.org/wiki/PinePhone_Software_Releases) look daunting, but I believe that it shipped with postmarketOS[^U5TtYk], so I took that approach, at least for a first pass.

[^c13eVX]:  They don't make it at all clear, but the back of the case snaps right off from the tiny divot on the bottom-left corner, providing direct access to a lot of the internal components.

[^U5TtYk]:  postmarketOS rebranded itself to [Nura](https://nura.eco/) as of last week, and they build it on [Alpine Linux](https://www.alpinelinux.org/).  And yes, someone will want to know that [Nura does forbid LLM contributions](https://docs.nura.eco/policies-and-processes/development/ai-policy.html), I guess plus-or-minus the Linux kernel as with everything else on the list.

And...ugh.  JumpDrive actually does its job fine, to its credit.  However, I can't get my machine to recognize that it has a device connected, so I can't flash a new operating system or remotely log in.  I tried different cables and configurations, and nothing.  On a search or two, I get the sense that people have "cargo cult" approaches to solving this, like "have another computer with different USB3 hardware vendors," because I guess everybody else has a dozen modern laptops handy to play with?

I avoided flashing Nura to the SD card, because that eliminates part of the value of the device, trying the other operating systems without impacting the normal function.  For a compelling example that ties into another ongoing project of mine, [Glo-Droid](https://github.com/GloDroidCommunity/pine64-pinephone) provides a year-old Android port, which would let me test whether the apps that I'd need---Hoopla, Kanopy, PBS, and Jellyfin, as I discussed in my [Shopping Small]({% post_url 2026-07-19-shop-small-1 %}) post---will work when I eventually try to replace Roku as my streaming box with something closer to Free Software.

Anyway...ugh again, because the device wouldn't boot.  It went through a weird cycle of a green light and vibration, changing to white and starting the screen, but then repeating the sequence.  Checking the old wiki, I find a couple of troubleshooting items.  It doesn't describe what I see here, but, emphasis mine...

> If the battery is fully drained, *most operating systems and distributions won't boot anymore*. One of the exceptions which still boots is the utility JumpDrive, which can usually be used to expose the eMMC and microSD card as drives to a USB-connected computer. Mind that *JumpDrive won't expose the eMMC and microSD card* with a drained battery, but it still can be flashed and booted from microSD card to confirm that the phone still functions and boots up fine.

The phone has sat for probably six years without power, so a drained battery makes some sense.  And as described, JumpDrive boots but doesn't expose the drives, while another operating system doesn't boot at all.  I pulled out the old charging cable, and let it sit for a couple of hours.  And...nothing.  I assume that I'll need to replace the battery, but Pine has run out, meaning getting a replacement.  Lovely.

Other than that, with the SD cards, I picked up a USB keyboard.  If I remember correctly, I abandoned at least one laptop because the keyboard stopped working.  If I can get one of them running again, then I'll have more latitude in checking out alternative operating systems.

## Kabang!

{% codeberg jcolag/kabang %}

In terms of the code, you'll only see some cleanup, this time through.  The spacing layout of the main screen should look a bit better, and the game now has a version number of 1.0.

More interesting for most people, though, you can now find [Kabang! on Itch](https://jcolag.itch.io/kabang), playing it or downloading the built versions.  It looks like I can embed it here, too, the final-for-now version.

<iframe
  frameborder="0"
  src="https://itch.io/embed-upload/19476591?color=777777"
  allowfullscreen=""
  width="740"
  height="441"
>
  <a href="https://jcolag.itch.io/kabang">Play Kabang! on itch.io</a>
</iframe>

You can also now find and play [Kabang! in TIC-80's collection](https://tic80.com/dev/jcolag/kabang), if you'd prefer to find it there.

## Entropy Arbitrage

{% codeberg jcolag/entropy-arbitrage-code %}

I needed to patch the end-of-month newsletter blurb for a minor spacing error that almost got out last week.  And I also updated the [About page](/blog/about) to narrow my newish AI disclosure, as I have trimmed out and replaced most of what generated material that I had previously used.

## Library Updates

I needed to bump versions for [Bicker](https://codeberg.org/jcolag/Bicker), the [CPREP background generator](https://codeberg.org/jcolag/cprep-background-generator), my [morning dashboard](https://codeberg.org/jcolag/dash) generator (that'll get replaced soon), and [Fýlakas Onomáton](https://codeberg.org/jcolag/fylakas-onomaton).

## Next

I should get back to Scrawls, but I honestly don't know where the week will end up, especially since I have started eyeing an old project that I'd like to rehabilitate to post on Itch.

* * *

**Credits**:  The header image is [Himeji Castle The Keep Towers](https://commons.wikimedia.org/wiki/File:Himeji_Castle_The_Keep_Towers.jpg) by [Reggaeman](https://ja.wikipedia.org/wiki/User:Reggaeman), ceded to the public domain by the photographer, and the building's design surely no longer has any copyright.
