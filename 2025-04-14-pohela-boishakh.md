---
layout: post
title: Developer Diary, Pohela Boishakh
date: 2025-04-14 07:41:05-0400
categories:
tags: [programming, project, dev-journal]
labels: [blog, codidact, open-badges, ruby]
summary: Progress on assorted projects
thumbnail: /blog/assets/Mangal-Shobhajatra-in-Dhaka.png
offset: -30%
description: This week's projects include Open Badges and the blog's code.
spell: Pohela Boishakh Mangal Shobhajatra Codidact Logosophy MarkDownload alsoKnownAs jwt Cryptpad Forgejo Notoboto
proofed: true
---

* Ignore for ToC
{:toc}

Today, the Bengali people celebrate [Pohela Boishakh](https://en.wikipedia.org/wiki/Pohela_Boishakh) (পহেলা বৈশাখ), the new year.  It seems like a well-considered party, though Bengali folks in certain parts of India generally wait for tomorrow.

If you'd like something closer to home, we also celebrate [Pan American Day](https://en.wikipedia.org/wiki/Pan_American_Day), honoring the founding of the institution that would become the [Organization of American States](https://en.wikipedia.org/wiki/Organization_of_American_States), not the defunct airline.

![Mangal Shobhajatra one of the traditional Bangladeshi cultural events during Bengali New Year festivals](/blog/assets/Mangal-Shobhajatra-in-Dhaka.png "I wonder how many holidays that a person could squeeze out by only celebrating recognized new years...")

And on we go to the projects.

## Codidact

Not that I get involved *so* often that it would matter, but I always forget to note that I've asked or answered something over on the small community, opposed to lousy people, Free Software counterpart to Stack Overflow and Stack Exchange.  This week, I happened to remember before publishing.

- More than a week ago, but [Why is SQL usually written in CAPS?](https://software.codidact.com/posts/293677/293680#answer-293680)  I might have actually found the source.
- [What happens if those charged with enforcing judicial orders won't? (US, federal)](https://proposals.codidact.com/posts/293719/293722#answer-293722), where I break down an increasingly common question in the United States.  Surprisingly, I managed to find fairly explicit solutions, which most people have at least some familiarity with in another context.
- [How can I copy the ChatGPT answer as Markdown?](https://powerusers.codidact.com/posts/293774/293775#answer-293775) gets in a quick swipe at ChatGPT before walking through maybe my most-used browser add-on other than (invisible) ad-blockers, [MarkDownload](https://github.com/deathau/markdownload).

I should call out, given the broad spectrum of topics there, that unlike Stack Exchange, Codidact doesn't isolate its communities.  Whereas I'd never sign up for the [Logosophy](https://jcolag.codeberg.page/fictopedia/Logosophy.html) Stack Exchange---I don't have the patience to think of a real one---because of the added friction of creating and linking a new account, I have no problem checking out the open questions around Codidact.

## Open Badges

{% github jcolag/badging %}

After far too long in a holding pattern, my Open Badges work finally got some useful attention, taking up most of the week.  It still needs confirmation, but it *may* produce valid badges.

Actually, given the amount of progress and explanations needed for it all to make sense, let's split this into a couple of pieces, so that you don't need to swim through some massive blob of text.

### Proofs

It started with revising the keys to use RSA instead of ED25519 , after seeing the line buried in the documentation's section on [selecting proof methods and crypto algorithms](https://www.imsglobal.org/spec/ob/v3p0/impl#selecting-proof-methods-and-crypto-algorithms) after a bunch of ED25519 references scattered around elsewhere.

> JWTs with `RSA256` algorithm, with key material published as JSON Web Key (JWK).

Probably not coincidentally, that small architectural change means that it doesn't take much of any work to get the key into a form that the libraries can use, and it simplifies signing to this.

```ruby
jwt = JSON::JWT.new metadata
jwt.kid = key.to_jwk.thumbprint
signature = jwt.sign key, :RS256
```

That signature now creates a token that the [JSON Web Token Debugger](https://jwt.io/) identifies as valid, decoding the payload and verifying that it matches the public key.  Oh, right.  For the people who don't need to do this routinely, I should probably explain why we care about those two aspects.

#### We Actually Care

Oversimplifying a bit, a [JSON Web Token](https://en.wikipedia.org/wiki/JSON_Web_Token) or JWT describes the data that you'll embed it in.  In our case, it represents the issuer, recipient, and badge information.  You can then (use a tool to) decode the token and confirm that it matches the remaining data that it claims to represent.  If it doesn't match, then somebody edited the data.  The above snippet also signs the token with a private cryptographic key, which---if you confirm the signature with the issuer's public key---also verifies that the issuer wrote the original data.

If that doesn't make sense, think of it in everyday terms, like identifying yourself to get into some exclusive event.  You have a payload, *you*.  To verify your claim that you have permission to get in, you present your ID, the equivalent of the token, which---probably with some combination of a photograph and descriptive data---makes it possible to spot discrepancies, if you try to pass yourself off as somebody else.  And, at least modern state-issued IDs provide some measures so that, if needed, the event can confirm that you didn't tamper with the contents.  In the case of the badge, the reason for granting the badge becomes the payload, instead of a physical body trying to get into the event.  And except that you cram the token inside the payload, as if some frustrated DMV clerk stapled your driver's license to your forehead.

Therefore, if the "debugger" from a couple of paragraphs back can tell us that the key unlocks the token, and the token represents data that we put in, it means that somebody showing off a badge can't alter the contents without breaking something and exposing the lie.  Either the token won't match what the badge claims, or the supposed issuer's public key will prove that they didn't actually create the token.  It'll take more reading---or getting one of those Open Badge validators to work---but this *might* mean that the script now generates valid badges, provided that somebody feeds it sufficient information on the issuing organization and recipient.

### Profiles, Too

Along the way, the script also now has a `--profile` option, which generates a [JSON-LD](https://json-ld.org/) profile based on the organization data provided.

This will eventually prove controversial, I think.  You see, according to the specifications, specifically the [issuer quick-start](https://www.imsglobal.org/spec/ob/v3p0/impl#issuer-quickstart), the recommendations to present the profiles go far beyond creating a file, poor editing aside.

> - When a client requests `Accept: application/json` or `application/ld+json` or does not include an `Accept` header, a JSON-LD that includes the OB 3.0 context should be returned. It should include its own primary id, all required properties from [Profile](https://www.imsglobal.org/spec/ob/v3p0#profile), and a representation of the public key component of the keypair this issuer uses to sign credentials in selected `JWK` or `eddsa-2022` format. See [Dereferencing the Public Key](https://www.imsglobal.org/spec/ob/v3p0#dereference)
> - When a client requests `Accept: */*` or `application/html`, an HTML representation of the `Achievement` should be presented. This should express information about the issuer using [Open Graph meta tags](https://ogp.me/), including at least name, description, and image tags for easy rendering of preview cards when the `Achievement` URL is shared to social media platforms, for instance.

While it makes sense to suggest this at some level, it also presumes that Open Badges will only work on the web, and that organizations want to run servers to check the [HTTP request headers](https://developer.mozilla.org/en-US/docs/Glossary/Request_header) and serve different content depending on the request.

Again, it *makes sense*, but it also feels limiting, when this project aims to turn Open Badges into a lightweight process that anybody can use to give somebody else credit.  And that probably means trimming his down to the bare minimum.  In the case of a profile, that means creating a static JSON-LD file to drop wherever your organization's `id` or `alsoKnownAs` says to look for it.

In practice, I'd bet that nobody wants a human-readable HTML representation of the organization's data.  Software wants something that it can consume and process---the JSON-LD form---or they want the issuer's *website*, which the issuer should provide as the `url` field in the badge.

### Miscellaneous

You'll also see minor changes that won't have much immediate impact beyond providing a more consistent structure.  The description of the `--image` argument explains that you want a PNG image, at least until this adds SVG as a target.  More files have [REUSE](https://reuse.software/)-friendly licensing information.  Key (`*.pem`) files now get ignored, so that nobody tries to commit one.  And the [issuing organization YAML](https://github.com/jcolag/badging/blob/main/org.yml) does a better job of illustrating what some fields mean---such as using `issuer.example` as a domain instead of `example.org`---as well as including some optional-but-probably-useful fields, along with the URL for the profile definition.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

You *almost* got refactored SASS, so that the link annotation icon styles would live in separate files by icon font.  However, after spending about two days trying to get it to build properly, the style rules still evaluated in the wrong order, so that the generic link icon stomped all the domain-specific icons, rather than the other way around.  That'll need to wait for another day, then.

However, I *did* add links for [Cryptpad](https://cryptpad.org/) and [Forgejo](https://forgejo.org/), after mentioning them last time.

It almost seems embarrassing, given the previous update, now that I see the two...

## Next

Honestly, I don't know what this week will bring.  If I can get one of the Open Badge validators to work, then I'll know if the badging script requires more work.  If I can make sense of breaking up SASS files, maybe I'll do more work on automating upgrades to the icon fonts.  Or maybe I'll have a new crackpot idea for **Notoboto**.  The library updates have started backing up again, too.  And if all else fails, I actually have the germ of an idea for a new project that might enable other projects.

* * *

**Credits**:  The header image is [Mangal Shobhajatra in Dhaka](https://commons.wikimedia.org/wiki/File:Mangal_Shobhajatra_in_Dhaka.jpg) by [Abidhasan00](https://commons.wikimedia.org/w/index.php?title=User:Abidhasan00&action=edit&redlink=1), made available under the terms of the [Creative Commons Attribution Share-Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
