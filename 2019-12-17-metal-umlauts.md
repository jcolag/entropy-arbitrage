---
layout: post
title: Metal Umlauts, Searching, and Other Unicode Fun
date: 2019-12-17 17:01:12-0500
categories: programming
tags: [javascript, unicode, programming, technology, techtips]
summary: Re-normalizing strings for improved user experience and entertainment
thumbnail: /blog/assets/writing-book-vintage-antique-texture-old-629962-pxhere.com.jpg
recommend: Messing around with Unicode
---

* Ignore for ToC
{:toc}

![Header Image](/blog/assets/writing-book-vintage-antique-texture-old-629962-pxhere.com.jpg "Writing with diacritical marks")

[Unicode](https://en.wikipedia.org/wiki/Unicode)---the computer "alphabet" that includes all the characters you see on this page, plus most modern writing systems in common use (∂), plus punctuation and currency (௹), plus arrows and mathematical notation (↛), plus drawing symbols (✵), plus emoji (🐣), and more---has a lot going on in it beyond the obvious complexity of multiple formats (UTF-8, UTF-16, GB18030, UTF-32, BOCU, SCSU, UTF-7, and probably others) and [byte orderings](https://simple.wikipedia.org/wiki/Endianness).  The part that has grabbed my interest, recently, is the idea of [Normal Forms](https://en.wikipedia.org/wiki/Unicode_equivalence#Normalization), of which we have four.

 * **NFD**: Canonical Decomposition
 * **NFC**:  Canonical Composition
 * **NFKD**:  Compatibility Decomposition
 * **NFKC**:  Compatibility Composition

Specifically, Normalization Form Canonical Decomposition interests me, because it represents each accented letter in a string as the base letter followed by any accents.

Better yet, in JavaScript, it's easy to change normalization forms.  Specifically, for these purposes, we want:

```JavaScript
    str.normalize('NFD');
```

The decomposed letters have some nice uses.

## Sorting

At least in English, diacritical marks are usually a marker for either history (fiancée, über, soupçon, Māori, piñata) or pronunciation (naïve, coöperate), rather than as an element of spelling.  This is especially true of names, where we generally want a person's name to be represented properly (Karel Čapek, Charlotte Brontë, Beyoncé Knowles), and that name can come from anywhere in the world, but English treats it more as an affectation than a critical element of the name.

Of particular importance, here, is that we generally wish to sort a name with accented letters as if the accents don't exist.  So, we want piñata to sort identical to "pinata" and Čapek to sort like "Capek."

The decomposed form allows us to do this by stripping the diacritical marks out of the string when we sort it.

```JavaScript
    const sortedStrings = strings.sort((a,b) => {
      const aNorm = a
        .normalize('NFD')
        .replace(/[\u0300-\u036f]/g, '');
      const bNorm = b
        .normalize('NFD')
        .replace(/[\u0300-\u036f]/g, '');
      return aNorm < bNorm ? -1 : 1;
    });
```

That admittedly looks a bit complicated, given the regular expression, but the entire process boils down to decomposing the strings, stripping off the diacritical marks (Unicode codepoints 0x0300 to 0x036f), and comparing the results.

In other words, by normalizing the name, the computer represents "Čapek" something like

```
[C] [caron] [a] [p] [e] [k]
```

Then, we remove any diacritical marks (the [caron](https://en.wikipedia.org/wiki/Caron) or **ˇ** &nbsp;&nbsp;in this case) by replacing them with nothing, leaving us with only the Latin letters.

## Searching

More so than with sorting, it's a better experience to search without regard for diacritical marks.  For example, an increasing number of laws intended to suppress minority votes are posed as "exact match" measures, which require that handwritten voter registration documents be identical to personal identification documents, meaning that the *exactness* of accents and diacritical marks relies primarily on the comprehension and interest of an underpaid data entry clerk.

By the same token, even something with much lower stakes like searching an employee directory shouldn't rely on the person searching for Beyoncé realizing that she has an acute accent in her name *or* that Human Resources input her name properly.

And neither of those even touches on the problem that a standard keyboard for English doesn't have an easy way to type accented characters.  So, even if a user has cleared the above hurdles, it's still a waste of the user's time to make them hunt down the exact spelling with diacritical marks.

We can solve this problem in a way similar to the sorting, normalizing and stripping both the target string and the corpus being searched.

## Metal Umlauts (or M͇ͭeţal Um͆l̼a͍u̓t̨s)

It's a bit before my time, but one of my favorite television shows growing up (via re-runs and now streaming) is **Mission: Impossible**, in no small part because of the signage in their fictional foreign countries.  Especially in earlier episodes, to make foreign countries seem both exotic and approachable to American audiences, show creator Bruce Geller had the idea of creating signs written mostly in English, but a version of English with clever misspellings representative of stereotypes of certain parts of the world, often including bogus diacritical marks.

For example, if you pay careful attention, you'll spot both *Zöna Restrik* (for Restricted Area) or *Prıziion Mılıtık* (for Military Prison).

And, of course, if you're a heavy metal music fan, you're undoubtedly familiar with the similar but distinct [Metal Umlaut](https://en.wikipedia.org/wiki/Metal_umlaut), though its use seems surprisingly limited to the diaeresis (**¨**) mark.

If we wanted to do something like transforming English text to Gellerese, you're on your own figuring out how to change the base spelling in a reasonable way.  But adding bogus diacritical marks?  That, we can definitely do.

```JavaScript
    let output = '';
    str = str.normalize('NFD');
    for (let i = 0; i < str.length; i++) {
      const c = str[i];
      output += c;
      if (c.match(/[a-z]/i)) {
        const rLen = Math.floor(Math.log2(Math.random() * 3));
        for (j = 0; j < rLen; j++) {
          const rCh = 0x0300 + Math.floor(Math.random() * 0x006f);
          output += String.fromCharCode(rCh);
        }
      }
    }
```

Again, we normalize the input string.  But instead of removing diacritical marks as we've been doing, here we visit each character and, if it's a letter, we pick a random-but-small number of diacritical marks to add (using `log2()` pushes the numbers lower and biases the distribution towards the lower end), and then selects the necessary diacritical marks from that same 0x0300 to 0x036f range we previously needed to remove.

If desired, this can easily be made more "intelligent" with lists of diacritical marks that are more appropriate to that letter, so that you don't end up with implausible combinations like what you see in the above section heading.

In either case, it might be a good idea to call `output.normalize('NFC')` at the end to set the characters back to their "composed" forms.

## Exception

One place where normalization has no effect is the Polish *L-with-stroke* (Ł or ł).  It turns out that, as far as Unicode is concerned, those are letters unto themselves rather than modified letters.  So, if you're planning on using any of these techniques, you will want to take that into account.

## Other (Programming) Languages

The above sample code snippets are all in JavaScript, but the Windows API supports [`NormalizeString()`](https://docs.microsoft.com/en-us/windows/win32/api/winnls/nf-winnls-normalizestring) and .NET has supported [`String.Normalize()`](https://docs.microsoft.com/en-us/dotnet/api/system.string.normalize?view=netframework-4.8) for quite some time.  Ruby supports [`string.unicode_normalize()`](https://apidock.com/ruby/v2_5_5/String/unicode_normalize).  It shouldn't be hard to find the equivalent for other languages, now that we know the key words to search for are "unicode normalize," maybe throwing in "nfd" or "decomposed" to make the context clearer.

Happy umlauting!

* * *

**Credits**:  Untitled header photograph [from PxHere](https://pxhere.com/en/photo/629962), made available under the [CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
