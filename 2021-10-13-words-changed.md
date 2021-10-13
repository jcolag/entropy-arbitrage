---
layout: post
title: Using git to Count Changed Words
date: 2021-10-13 06:40:23-0400
tags: [programming, techtips, blog, git]
summary: More semi-useful git tricks
thumbnail: /blog/assets/Chinese-counting.png
offset: -5%
proofed: true
---

![Chinese finger-counting system](/blog/assets/Chinese-counting.png "Hanging six doesn't sound as appealing, somehow.")

A while ago, in [a developer journal post]({% post_url 2021-09-27-hiv %}), I mentioned that I worked on a new feature for [the **Entropy Arbitrage** newsletter](https://entropy-arbitrage.mailchimpsites.com/) which, if you're a subscriber---and if not, where *have* you been?---you saw in action about a week and a half ago.  Specifically, as of this month, the newsletter includes a list of posts that I've updated, so that readers can see that I've modified a post and decide if it's worth revisiting it.

Making that feature work has a few moving parts, and uses [`git`](https://git-scm.com/) in a couple of ways that are novel, at least to me.

## Snore... 😴

If you're not a programmer, this might still be of interest to you, because it shows how the tools that programmers use can be pressed into service for more routine work by perfectly ordinary people.  I'll probably eventually do a full "version control for non-programmers, and why you should care" post, but the short version is that version control systems (like `git`) are sort of like sophisticated versions of Dropbox or an equivalent online service.  When you make a change to your files, you can "check it in," saving your changes as an official version of the file.

This works well, because on the (admittedly rare) occasions that you like the version from a month ago better, except for one change made recently, you can semi-easily make that happen.  And like [a Wikipedia history page](https://en.wikipedia.org/w/index.php?title=Tamak%27&diff=516257097&oldid=514723767), you can quickly see what was added or deleted at any step.

This post is a bit more esoteric, but it does build on that notion.

## A Month of Commits

Every commit in `git` gets a "hash value," a unique identifier that a person can use to investigate a change, roll it back, or send it to another version of the project.  To get a set of files changed during a particular month, we need to do some quick investigation of the project history.

```console
month=$(date --date='15 days ago' +"%Y-%m")
hashes=$( \
  git log --pretty='%ci %H' | \
  grep "^${month}" | \
  sed -n '1p;$p' | \
  cut -c27- | \
  paste -sd' ' \
)
first=$(echo "${hashes}" | cut -f2 -d' ')
last=$(echo "${hashes}" | cut -f1 -d' ')
```

The main command gets the history (`git log`), asking for specific formatting that looks like the following, a time stamp followed by the hash value that names the commit at that time.

```
2021-09-25 06:58:48 -0400 643cc4bcd00935f4609668bbd94ed04517c4f989
2021-09-24 07:09:00 -0400 c51c2579cae56349554fd26a63dbe2c11b0d9c0f
2021-09-04 06:45:50 -0400 6528fa2b5cc560379bd5bd884e89e327b7eef01c
2021-08-02 06:53:23 -0400 876a7a63828ed25e4b69144e05fe74c6b240da79
2021-04-03 06:30:52 -0400 a0abd7fbe0724cae18db1400553fcb4df38e641e
2020-10-24 06:38:49 -0400 ec45598e1222a2c75af30e0b0f903b0de6ccd93b
```

Each line is a date, a time, a time zone, and the unique values that we care about.

We than ask for the lines of the log (`grep`) that start with (`^`) the month that we're interested in.  For the example above, it might be `2021-04`.  We ask for the first and last lines (`sed`), ignore the first twenty-six characters (`cut`) that happen to include the time stamp, and join the remaining two lines together (`paste`), putting the values into the variables `$first` and `$last`.

## Get the Modified Files

Now, we need a list of files modified during that range of commits.  Conveniently, `git` does most of *this* automatically, even though the previous and next parts are pretty hairy.

```console
git diff --name-only "${first}^1" "$last" | grep -v "^${month}"
```

This asks for just the names of the files changed (`--name-only`) from each commit from the version *before* the oldest (`$first^1`; I'll explain that more later) to the newest (`$last`).  In my particular case, I want to filter out (`grep`) any blog posts *released* in the month that I modified them, since they were probably modified before release or, at most, I just corrected a typo.

## Count the Words Changed

For each of the files provided by the command in the previous section, we want the individual words that have changed between versions.

```console
changes=$( \
  git diff --word-diff=porcelain "${first}^1" "${last}" "$file" | \
  grep '^[+-][^+-]' | \
  wc -w \
)
```

The short version is that we ask for the list of words, filter (`grep`) anything that is actually a word instead of a heading, and get the word count (`wc`).

However, it's a *bit* more complicated than that.  The `--word-diff` argument says to mark the changed words inside the changed lines.  The reference to `porcelain` is a format that (among other things) separates the *unchanged* words on the changed lines from the changed words on those lines.  That gives output that looks something like the quick example a couple of paragraphs below, from a real change on this blog, last month.

Oh, unfortunately asking for the difference between the first commit and the second commit does exactly that, which means that all the changes from the first commit are assumed to be the starting point and *not* actually changes relevant to the question.  So, you might notice that the first commit is actually `first`**`^1`**.  The `^1` notation is a `git` shortcut that says to get the commit *before* the first commit that we're talking about.

Ignoring the notation, if the above explanation is confusing you do it with arithmetic all the time without noticing.  If you want to know how many numbers there are from 105 to 132, 132 - 105 = 27.  But that's wrong, because if you count them, there are *28* numbers in that range.  Subtraction doesn't count both ends, so you actually end up subtracting 104---one before the smaller number---from 132 to get the right answer.

In any case, here's the promised example, part of some minor changes to my post on [content advisories]({% post_url 2021-07-04-advisory %}).

```diff
 So, despite what right-wing pundits would prefer everybody to believe, when we talk about content advisories, content warnings, trigger warnings, or whatever other term might fit the bill,
-is
+are
  just
-a note
+notes
  that the work is going to include some content that may [stimulate a trauma response](https://en.wikipedia.org/wiki/Trauma_trigger) in a minority of the audience.  Specifically, people suffering from post-traumatic stress may find that the content reminds them of the traumatizing event in such a way that it produces flashbacks or other panicked reactions.
```

Lines that start with a space include unchanged text from a line.  Lines that start with a subtraction sign (`-`) include words that were removed.  And the lines that start with an addition sign (`+`) include words that were added.  So, we pick up the `+` and `-` lines and count the words on them to get a total.  In plain English, this syntax means that I fixed the subject-verb agreement in a sentence.

## The Final Result

All that's left is to set up some additional variables, get around from folder to folder---because `git` is picky about that sort of thing---and report the results.  Here's what the script looked like, in the end, so that you can see everything in context.

```bash
#!/bin/sh
rooturl=$(jq -r '.blogRss' < config.json | sed 's/\/feed.xml//g')
postdir=$(jq -r '.postSource' < config.json)
here=$(pwd)
month=$(date --date='9 days ago' +"%Y-%m")
cd "${postdir}" || exit
hashes=$( \
  git log --pretty='%ci %H' | \
  grep "^${month}" | \
  sed -n '1p;$p' | \
  cut -c27- | \
  paste -sd' ' \
)
first=$(echo "${hashes}" | cut -f2 -d' ')
last=$(echo "${hashes}" | cut -f1 -d' ')
for file in $(git diff --name-only "$first" "$last" | grep -v "^${month}")
do
  words=words
  changes=$( \
    git diff --word-diff=porcelain "${first}^1" "${last}" "$file" | \
    grep '^[+-][^+-]' | \
    wc -w \
  )
  if [ "$changes" -eq 1 ]
  then
    words=word
  fi
  target=$(basename "$file" .md | tr '-' '.')
  title=$(grep '^title: ' "$file" | cut -f2- -d':' | sed 's/^ *//g')
  postdate=$(grep '^date: ' "$file" | cut -f2- -d':')
  published=$(date --date="${postdate}" +"%A, %Y %B %d")
  url=$(grep "${target}" "${here}/blogurls.json" | cut -f4 -d'"')
  echo " * [${title}](${rooturl}${url}) from ${published}, ${changes} ${words}"
done
cd "${here}" || exit
```

Overall, that's not too bad, given the information that it provides.  The output is a Markdown-formatted, bulleted list, so it fits right in with the rest of the source for the newsletter issues.

* * *

**Credits**:  The header image is [Chinese finger-counting system](https://commons.wikimedia.org/wiki/File:Chinese_counting.jpg) by [Aljosa21](https://commons.wikimedia.org/w/index.php?title=User:Aljosa21), made available under the terms of the [Creative Commons Attribution-Share Alike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/deed.en) license.
