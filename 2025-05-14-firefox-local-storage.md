---
layout: post
title: Firefox's Local Storage
date: 2025-05-14 07:44:05-0400
categories:
tags: [programming, tech-tips]
summary: Accessing browser local storage without the browser
thumbnail: /blog/assets/2821064805_1c7c996ebd_o.png
offset: -38%
description: Exploring the storage behind local storage, including the most C code that John has written in at least a decade.
spell: stenotype Typey Codidact topSpeedPersonalBest whateverKeyWeCareAbout LevelDB Snappy-ing infile feof getc printf lessonsProgress unsnappy jq gcc DNDEBUG fPIC lstdc sed
proofed: true
---

* Ignore for ToC
{:toc}

In [Monday's developer diary post]({% post_url 2025-05-12-nurses %}), I mentioned exploring browser local storage, and hinted why, but I figured that---now that I've had some success---I should document the entire story, both for my notes and for anybody else who might need this.

![A bed with two pontoon-like drawers pulled out from beneath](/blog/assets/2821064805_1c7c996ebd_o.png "The lamp trying to peer into the drawer really makes this...")

I won't get into how [local and session storage](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API) work from the web application perspective, but it probably won't matter.

## Motivation

You can skip most of this if you only care about working with local storage, but as I've mentioned for a couple of weeks, I recently decided to take learning the stenotype keyboard more seriously.  For this, I started using [Typey Type](https://didoesdigital.com/typey-type/), the equivalent of the old typing drills where you might type lines such as the following.

> as add all ask dad fad lad sad lad as sad fad dad add all ask

The idea goes that, by repeating drills like this, your fingers build the muscle memory to distinguish between different parts of the keyboard as you type, in that example taking common short words using only the "home row."  Later drills would add the {% key G %} and {% key H %} keys as well as including longer words, then adding more keys over time.  Stenography relies more on 

Anyway, to keep myself practicing, I decided to start including a *Stenotype Corner* section in the developer diary posts, where I acknowledge what lessons that I've worked on, along with my speed and accuracy.  And it occurred to me that I should maybe try to partially automate this, so that I don't forget to include the section and (ideally) give it a data-driven basis.

## By Hand

Cracking open the developer tools and flipping over to the *Storage* tab, *Local Storage* entry, and select the website, we can get a sense of what the application stores.

![The developer tools open in Firefox, showing five key/value pairs for https://didoesdigital.com](/blog/assets/typey-type-local-storage.png "As of earlier this week, in my case")

And sure, a person could do this, or whip up a [bookmarklet](https://en.wikipedia.org/wiki/Bookmarklet) to do this on a click.  For example, create a bookmark with a URL that looks like this.

```JavaScript
javascript:alert(localStorage.getItem('topSpeedPersonalBest'));
```

And clicking on that bookmark would create a pop-up message giving me something like `{"wpm": 24}`.  But...why tie up the browser and probably myself, to do this?  Even if I quasi-automated this with a browser automation tool, it'd still need to open the page in the browser that I use---which *I use*, remember---to grab the information.  Surely, Firefox stashes this information *somewhere*.

## First Explorations

As mentioned, I've written a bit about *wanting* to solve this a couple of times, including mentioning on Monday that I submitted [Extracting Firefox Local Data](https://software.codidact.com/posts/293929) to Codidact, and this section will borrow a *lot* from there, since it does tell mostly the same story.

It seems like an uncommon topic, but I managed to find a [comment on an answer](https://stackoverflow.com/questions/7079075/where-does-firefox-store-javascript-html-localstorage#comment132431297_72580890) that provides the first step, here.  Poking around under the profile and looking for that `ls` (local storage, remember) folder, I find that every site has one, so the data lives somewhere along the lines of this path.

```console
~/.mozilla/firefox/${profile}/storage/default/${site}/ls/data.sqlite
```

The site looks something like `https+++didoesdigital.com`, for Typey Type.  The browser locks the database (at least) when it has the page open, but we can copy it off to a temporary version to work with it.

The name gives a fairly clear sign of the [SQLite](https://www.sqlite.org/) format, but the `file` command confirms that.

> SQLite 3.x database, user version 80, last written using SQLite version 3049001, page size 1024, file counter 45, database pages 7, cookie 0x2, schema 4, largest root page 5, UTF-8, vacuum mode 1, version-valid-for 45

Opening the (copied) database in SQLite3 then shows two tables.

- `database` mostly only describes the site.
- `data` holds what we find under the Developer Tools.

The schema for the latter looks like this.

```SQL
CREATE TABLE data(
  key TEXT PRIMARY KEY,
  utf16_length INTEGER NOT NULL,
  conversion_type INTEGER NOT NULL,
  compression_type INTEGER NOT NULL,
  last_access_time INTEGER NOT NULL DEFAULT 0,
  value BLOB NOT NULL
);
```

Remember that we have it, here.  As some foreshadowing for the database people, it'll become important later...

Querying `SELECT value FROM data WHERE key = 'whateverKeyWeCareAbout';` produces results, so far, so good.  For example, using the aforementioned `topSpeedPersonalBest` as the key returns the JSON that we'd expect.

However, while the "something" that we get from the `value` column *might* come through as plain JSON---it looks like this happens when the browser serializes a smaller object, such as the `topSpeedPersonalBest` example---or it might come through as something more complicated, which resembles small fragments of the expected JSON interspersed with opaque binary sequences.  Take a look at however the blog will display an example.

```
ª{"has":27,"part":28,"set":19,"war	so3,"pe1,"spo/ 0,"stop":ha3,"wBhers":1_	C0W
```

Actually, that doesn't carry over well in HTML.  Let's try a dump.

```
00000000  aa 03 80 7b 22 68 61 73  22 3a 32 37 2c 22 70 61  |...{"has":27,"pa|
00000010  72 74 22 3a 32 38 2c 22  73 65 74 22 3a 31 39 2c  |rt":28,"set":19,|
00000020  22 77 61 72 09 1c 04 73  6f 05 1c 10 33 2c 22 70  |"war...so...3,"p|
00000030  65 01 13 14 31 2c 22 73  70 6f 01 2f 20 30 2c 22  |e...1,"spo./ 0,"|
00000040  73 74 6f 70 22 3a 01 14  04 68 61 01 13 0c 33 2c  |stop":...ha...3,|
00000050  22 77 01 42 01 1c 18 68  65 72 73 22 3a 31 01 5f  |"w.B...hers":1._|
00000060  09 43 05 30 05 57 0a                              |.C.0.W.|
```

There.  Now, you can probably see what I mean.  We definitely have *pieces* that look like they came from valid JSON, but they don't form a coherent whole, and have all that binary nonsense in the way.

Typey Type creator [Diana MacDonald](https://didoesdigital.com/about/) released the application as Free Software, so I double-checked to make sure that the code doesn't do anything weird with its local storage data, in hopes of stealing the logic from there, but [you can see](https://github.com/search?q=repo%3Adidoesdigital%2Ftypey-type+localstorage.setItem&type=code) that it doesn't get any more complicated than serializing the object to JSON before storing it.

### Chrome and Chromium

Oh, good luck with that...

Actually, I probably only need to discover the right tool for this job, which *surely* exists.  But for the sake of completeness, I traced the Chromium---I don't have actual Chrome installed---local storage database to this folder.

```
~/.var/app/org.chromium.Chromium/config/chromium/Default/Local\ Storage/leveldb/
```

The path tells us that we have a [LevelDB](https://en.wikipedia.org/wiki/LevelDB) database.  Inspecting the (mostly binary) manifest shows that the browser throws all sites together into the same database...which feels like a security problem waiting to happen, but people with more direct security experience should probably deal with that, not me.  I *will* note, however, that LevelDB "has a history of database corruption bugs," as the Wikipedia article puts it.

At this point, I slam up against a wall, because I can't find a tool that will let me run queries against the database to extract the data.  I didn't look *hard*, here, because I don't need any data from Chromium, but if I did, I'd need to pick up the story there.

## Getting Lost

Searching from there, I found suggestions that Firefox might use [Message Pack](https://msgpack.org/index.html) for this part-binary storage, but none of the `value` columns would decode with that assumption.  Elsewhere, I found one suggestion that Firefox could potentially use the internal representation of the [structured clone algorithm](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm), but I couldn't find any corroboration for this, nor could I find any code or tool to decode/validate that claim.

That left me with one verifiably false claim, one unlikely and untestable claim, and no other relevant search results that I could spot.  It seemed like time to call for help, so I wrote up what I knew---pretty much this and the previous sections, minus the Chromium material---and posted to the software development community on Codidact.

### Refreshing Everybody's Memories

If you haven't run across it and don't remember my mentioning it a couple of times over the past year or so, [Codidact](https://codidact.org/) grew out of a [series of catastrophic moderation failures](https://meta.stackexchange.com/questions/337097/how-can-we-help-monica-cellio)---many further links in the replies, exposing this as part of a pattern and not an isolated incident, and seemingly [accelerated by the company's embrace of AI <i class="fas fa-copyright"></i>](https://arstechnica.com/information-technology/2024/05/stack-overflow-users-sabotage-their-posts-after-openai-deal/)---on Stack Exchange and a desire to do better, in terms of building and moderating the community.

They currently have eighteen communities---plus a general "incubator" space for proposed communities---and you can catch me contributing to a handful and regularly reading on about half of them.  They have a much smaller community than Stack Overflow/Exchange, but that sometimes seems like a benefit.

I recommend it.  And especially if you've had trouble with "the Stacks," such as whining if you didn't find exactly the right way to present your question, insistence that they don't handle your kind of question, or people explaining that you solve your problem by doing something entirely different that they know how to answer, then you might want to poke around.

## Missing Puzzle Piece

Sometimes, the smaller Codidact community means that it takes time to get a response.  However, in this case, it took about a day for a Derek Elkins‭ to take the step that I stupidly didn't, [checking to see what Firefox does](https://software.codidact.com/posts/293929/293932#answer-293932) in its source code.  And I thank him profusely for that.

In his answer, he makes some points that I can probably safely ignore---though I appreciate the thorough job, since someone else probably can't ignore them---but he did find the key.  The code to store data has a compression type, either uncompressed (`0`) or [Snappy](https://en.wikipedia.org/wiki/Snappy_%28compression%29) (`1`).  Go read the full answer.  I won't quote it here even though he released his answer under the same terms as the blog, but if you need more than the compression algorithm's name, he does a terrific job.

## Snappy-ing to It

Knowing what to look for, finally, changes things substantially.  Search indices haven't kept up to date, causing some detours, but at the end of the search, we find [Google's Snappy page](https://google.github.io/snappy/), describing the point of the exercise.  More importantly, though, it links to a variety of implementations, code in different languages to compress to and decompress from Snappy.

From here, I grabbed the [implementation in C](https://github.com/andikleen/snappy-c)---had I glanced further down the page, I probably would have gone with [Rust](https://github.com/BurntSushi/rust-snappy), but C will suffice---built the package, and...couldn't get their utilities to work.

I could see two reasons for this.  Most clear, they didn't build their user interfaces for "loose" data, like piping the output of `sqlite3` into it.  But off in the fringes, it might have also dawned on you---as it finally did me---that, if you'll recall or double-check the schema for the `data` table above, Firefox stores data as a `BLOB`, a "binary large object," rather than as a string.  That makes sense, because we have compressed data and not a string, but it means that we need to amend the query slightly.

```SQL
SELECT hex(value) FROM data WHERE key = 'whateverKeyWeCareAbout';
```

Using the same example of the maximum speed, that gives `7B2277706D223A32347D` instead of the JSON seen above.  And while we might expect two hexadecimal digits per character in most cases---hexadecimal covers sixteen values in each place, so two (0-9, A-F) digits gives us sixteen times sixteen, or two hundred fifty-six (256) possible values, the size of a [byte](https://en.wikipedia.org/wiki/Byte) or an [ASCII](https://en.wikipedia.org/wiki/ASCII) character[^1]---I note with satisfaction that `hex(value)` runs significantly more than twice the length of `value` for those part-binary values, meaning that we *did* lose parts by not accounting for the non-text nature.

[^1]:  Unicode sets its first 256 characters to the ASCII set, and UTF-8 representation of Unicode makes them one-byte characters.  In most cases that we'll run into with stenotype, then, we can *probably* assume two hexadecimal digits per character, even though that won't always hold true in most modern and important cases.

Note, by the way, that *if* we had a convenient way of reading LevelDB to extract local storage data from Chrome/Chromium, LevelDB uses Snappy directly, as part of its storage.  Therefore, this part of the process probably mostly holds, if you need to work over there.

## Unsnap

Anyway, that insight of selecting `hex(value)` gives us out final piece, because I can hack together a quick program to (a) turn the string of hexadecimal digits into a series of bytes, then (b) use the aforementioned Snappy C code to decompress the blob, and (c) print the result *if* it decompressed.  They provide a [library API](http://halobates.de/snappy.html) description, which chops down that research work to only finding the one function that I need.

```c
#include "snappy.h"
#include <stdio.h>
#include <string.h>

int main(void) {
  int
    err = 0,
    i = 0,
    index = 0;
  FILE *infile = stdin;
  char
    buffer[8192],
    in[8192],
    out[8192];

  /* Read from standard input. */
  while (!feof(infile)) {
    in[index++] = getc(infile);
  }

  /* Convert the hexadecimal input to a binary buffer. */
  for (i = 0; i < index; i++) {
    sscanf(&in[2 * i], "%2hhx", &buffer[i]);
    buffer[i+1] = '\000';
  }

  /* Decompress the buffer. */
  err = snappy_uncompress(buffer, index + 1, out);
  if (strlen(out) > 0) {
    /* Decompression succeeded; print the result. */
    printf("%s", out);
  } else {
    /* Decompression failed; print the blob as probably not compressed. */
    printf("%s", buffer);
  }

  return err;
}
```

I wouldn't call this code *quite* up to my standards.  It does what I want it to do, but...

- I hard-coded the program to always use `stdin`, with no way to configure that.
- It should probably check to see if we have valid text *first*.
- As Elkins (and the database schema) points out, Firefox *might* store the `value`s as UTF-16 strings, meaning that every four hexadecimal digits should become a character, rather than two, I think, in some cases that I don't check for.  Or maybe we care about that after decompressing; either way, the code doesn't handle that, but should in the general case.
- I played fast and loose with data types for readability, such as treating arrays like pointers, which *usually* works, but could go wrong in edge cases, or using integers (which can have positive or negative values) in place of sizes (which only have positive values), to say nothing of mixing and matching pointer types.
- As mentioned, I probably should've used the Rust implementation, so that it can take advantage of more modern programming practices.

In other words, I wouldn't want to put this into a product that I expect other people to use, but as a quick hack for me to use behind the scenes of the blog (and for the example), it'll more than suffice.  It works well enough for me, but the part of me that programmed in C for work for about a decade feels mortified that I'd ever show this to anybody.  Specifically, at this point, I can run something like this.

```sh
sqlite3 temporary_copy.sqlite \
  "SELECT hex(value) FROM data WHERE key = 'lessonsProgress';" \
  | unsnappy | jq .
```

And that gives us what we expect, valid JSON.

### You Might Want to Build That

Oh, for those of you who don't work with C much, I compiled the code with the following.

```sh
make
gcc -Wall -g -O2 -DNDEBUG=1 -fPIC -shared unsnap.c -c
gcc -lstdc++ unsnap.o snappy.o map.o util.o -o unsnappy
strip unsnappy
```

The first line builds Google's Snappy project, so that we don't need to worry about getting the pieces together manually.  The second compiles, but doesn't "link" the code, producing a not-quite-executable file that still requires the libraries strapped onto it[^2].  Then, we link that intermediate "object" file with the libraries to produce the final executable.  Finally and optionally, the `strip` command removes unused debugging information from the executable file, which usually shrinks it down substantially, at the cost of a far less pleasant experience if you ever need to inspect the program as it runs.

[^2]:  Think of linking like the process for getting a hypothetical technical book ready for printing or other distribution.  You have a version that says something like "see page XX for details," with the intent to replace *XX* with a real page number once you know how the layout comes together, ideally with some program, rather than catching them all by hand.  The linker does that for code, along with packaging together anything else that you think that the program will need.  It *links* the references to the thing that they refer to.

I stole a lot of the command-line options to `gcc` from the project's `Makefile`, for consistency with the other parts of the project, rather than giving any thought to what they actually do.

## And Beyond

From here, I need to sift through the information available, to see what metrics that I can and want to talk about in the developer diary posts.  A script can then call the SQLite-to-unsnappy-to-[jq](https://jqlang.org/), using the last piece to tease out the details that I want.  The script can then plug that information into a template.  For a quick example, consider the following.

```sh
wpm=$(sqlite3 "${tempdb}" "SELECT value FROM data WHERE key = 'topSpeedPersonalBest';" | jq -r .wpm)
echo "This week, I hit a speed of ${wpm} words per minute."
```

The script could then insert that result, along with whatever else I can pull out of the data, into the next relevant post, probably using `sed` to put the *Stenotype Corner* section in front of the first `##` heading.  And with that in place, I can then edit the post to highlight the aspects that I find interesting or otherwise alter the text to feel less formulaic from week to week.

I mean, it already looks formulaic, because I copy and edit the section from week to week by hand, but I don't want it to get *worse*.

* * *

**Credits**:  The header image is [The Hull Bed - concealed storage](https://www.flickr.com/photos/25186605@N04/2821064805) by [Jeremy Levine](https://www.flickr.com/photos/jeremylevinedesign/), made available under the terms of the [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) license.
