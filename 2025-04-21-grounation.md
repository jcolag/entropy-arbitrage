---
layout: post
title: Developer Diary, Grounation Day
date: 2025-04-21 07:13:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/Flag-of-Ethiopia-1897-1974.png
offset: -30%
description: This week's projects include the blog's code and Open Badges.
spell: Grounation Haile Abu Ye Cryptpad Disroot chardet canonicalization canonicalized Oren neu
proofed: true
---

* Ignore for ToC
{:toc}

Today, at least Rastafarian folks celebrate [Grounation Day](https://en.wikipedia.org/wiki/Grounation_Day), honoring Haile Selassie's 1966 visit to Jamaica, which has become the movement's most important holy day.  Even after reading the Wikipedia article, I admit that I don't really understand the connection, but given how many European holidays exist to absorb some local festival, I don't need to make sense of anything to offer an *Abu Ye* to those who celebrate.

![The flag of the former Ethiopian Empire with the Lion of Judah in the center](/blog/assets/Flag-of-Ethiopia-1897-1974.png "When people talk about flags, they don't talk nearly enough about the era when people put extremely fussy national symbols on them for people to sew...")

Anyway, let's check out the week's projects.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Mostly, I added link-annotation icons.

- [Cryptpad](https://cryptpad.org)
- [Disroot](https://disroot.org)
- [JWT](https://jwt.io)
- [Nextcloud](https://nextcloud.com)

They now show up in CSS and the YAML file to generate the CSS.

However, I also made a quick change to my asset-management script.  When the script can't convert something to an [AVIF](https://en.wikipedia.org/wiki/AVIF) image---probably because I didn't feed it an image---it previously copied the base-name into the assets folder without any conversion, which works *except* that the base-name doesn't include sub-folders, which breaks linking.

## Open Badges

{% github jcolag/badging %}

Once again, I spent most of my time on the Open Badges code.  I did some minor-but-actual work on it that I'll get to in a bit, but first, let's talk validating these monstrosities.

If you'll recall, the script *might* produce a valid badge, at this point, with useful metadata that verifies itself embedded into a badge image.  However, I can't tell you that it produces a valid badge, because Open Badges has an entire ecosystem of applications that include issuing, reading, storage, and so forth.  Therefore, the badges need validation, to prove that they conform to the standard.

### Validation Woes

I continue to have trouble validating the badges, and it looks suspiciously like the problem lives on their side, regardless of any hypothetical problems with the badge.  For example, it consistently crashes when fed any image.  But more importantly, when fed the JSON-LD-with-signed-JWT discussed at length [last time]({% post_url 2025-04-14-pohela-boishakh %}#open-badges), it drops the following error.

> Invalid JSON-LD syntax; @context property values must be strings or objects.

What does *that* mean?  I honestly don't know, considering that my `@context` property has an array of strings in it, exactly like every example, and that sounds like "strings or objects" to me.  However, I found [this issue](https://github.com/digitalbazaar/pyld/issues/99), which identifies the error message as coming a prior version of the library not covering the modern JSON-LD specification.  The same error (I think; their output makes me dizzy) also indicates this.

> Could not expand input before compaction.

Now, I didn't actually *believe* this, because the [JSON-LD Playground](https://json-ld.org/playground/) mentioned last time can expand and compact the data.  But searching for the message turned up [another issue](https://github.com/1EdTech/openbadges-validator-core/issues/257), this time on the validator itself from last year, which shrugs off the issue as something also related to not keeping up with library versions, then allegedly solves the issue...two or three times.

Maybe they haven't kept their servers up to date, then.

However, that last repository claims to provide a command-line tool for validation.  I follow its directions, and...get a screenful of exception dump, amounting to this.

> Import Error: cannot import name 'Mapping' from 'collections'

It does this with arguments, with no arguments, and for requesting help information.

A quick search suggests that this has to do with a malformed import statement, rather than libraries, which makes this something of a dead end for me.  You could convince me to write Python in an emergency, but writing Python to update a poorly maintained validation tool, to test the output of a one-off project?  That doesn't seem like a fun way to spend a week.

Except that maybe---like some down-voted-to-oblivion answer suggests---I can upgrade all the outdated Python packages running around on my machine.  It might break a bunch of other things, but *sure*, I try it.  And that gets me slightly further.

> Requests Dependency Warning: urllib3 (2.4.0) or chardet (5.2.0)/charset_normalizer (3.4.1) doesn't match a supported version!

And the handling of that exception throws another exception.  Whee!

Oh, right, I almost forgot the next natural question.  Can I run the tool from source, now that I've found the repository?  [One last issue](https://github.com/1EdTech/openbadges-validator-core/issues/247), this one suggesting that it'll only run with specific versions of Python, and...no.  I have even *less* interest in installing a bunch of obsolete tool-chains on the off-chance that provides slightly better results than the other versions of the tool run by people who should know far better than I do.

At this point, I don't know where to go, because apathy and atrophy seem to have cut off every avenue to validating these things.  I'll keep looking, but don't see much cause for optimism on that front.  Honestly, given that I have nothing to show for it, I probably wouldn't have even mentioned it, except that I want to stay transparent on these issues, and maybe some reader, one day, will spot a solution and help push things along.

### Code Changes

Back to making things work.

Now that the code can output a JSON-LD profile of the organization, the repository ignores JSON files, so that nobody tries to commit one.

With the shift to RSA-256 for encryption and signatures, the ED25519 libraries no longer help, so say goodbye to them.

The badge metadata and JSON-LD profile now (both) include the organization's public key, so that people can compare them (or use what they find in the profile) to validate the source.  And the metadata now appears in---pardon the ugly and self-redundant term, here---*canonicalized* form.

Who cares about canonical anything?  When you digitally sign files or other data, you need to make sure that anybody, using the same process and the same keys, will get the same signature.  Because you can reorder JSON (among other changes) without damaging the contents, some implementations will convert objects to JSON in different ways, meaning that your version of the object might not match mine, and so you'll get a different signature than me.  A canonicalized version, inexplicably "an object that has gone through the process to make it canonical" and not *canonical* (but the JSON people never asked me), has rules on ordering, types, and so forth, so that your object looks like mine.

Ruby has a library to do this work, as do most languages, but...the badging code sometimes uses Ruby's "symbols" instead of strings as JSON keys for convenience, and the library doesn't like that.  Therefore, to get a canonical JSON object, we need to pointlessly convert to-and-from JSON to get all strings.

```ruby
json = obj.to_json
o_parsed = JSON.parse json
o_parsed.to_json_c14n
```

We convert the object to JSON, JSON to a new object, and the new object to canonical JSON, which gets the signature.

Anyway, other than that, you should also see slightly cleaner code, with obsolete comments and variables removed.

## Next

I should file an issue with the badge validator, to see if anybody over there even cares, at this point.  If they have solutions, then the badging script may need more work.  I also have those library updates backing up, and still want to break up the blog's SASS files.  We'll see, I guess...

* * *

**Credits**:  The header image is [The Flag of Ethiopia (1897–1974)](https://commons.wikimedia.org/wiki/File:Flag_of_Ethiopia_%281897%E2%80%931974%29.svg) by [Oren neu dag](https://commons.wikimedia.org/wiki/User:Oren_neu_dag), in the public domain as "official text of a legislative, administrative or of legal nature," by the [Copyright and Neighboring Rights Protection Proclamation No. 410/2004, Ethiopia](https://www.wipo.int/wipolex/en/legislation/details/5306).
