---
layout: post
title: Simple Build Scripts
date: 2022-08-17 06:29:02-0400
tags: [programming, techtips, build, interactive-fiction]
summary: Writing a script to avoid a flawed IDE
thumbnail: /blog/assets/zork-original.png
offset: -40%
proofed: true
---

About a month ago, I mentioned [working on a private project with Inform 7]({% post_url 2022-07-25-caracas %}).  Among my problems with doing so, the IDE takes enough resources that I can count on the first phase of the compiler---Inform 7 to Inform 6, or "Natural Inform"---to crash my aging laptop about half the time.  (I'll frame this post around dealing with Inform, but the [tech tip](/blog/tag/techtips) actually takes on some nice conveniences for shell scripts.)

![The original version of Zork](/blog/assets/zork-original.png "You might fall into bottomless pits, here; no grues will get belly-aches from eating you.")

I tried to ignore it.  Like I said in that post, the "game" that I worked on mostly amounted as a memory exercise for myself, so I could afford to limit the reasons to compile, waiting until I wanted to try something, rather than confirming that the code still worked.

Eventually, I looked at the build log, and noticed that they show the compiler commands, giving me the thoroughly opaque command-line flags to use on the two compilers.  And that gave me the idea of ditching the IDE and running scripts at the command line.  I started with the straightforward approach, creating `i7.sh` and `i6.sh` single-line scripts with the paths hard-coded.  After a few trials, I concluded that the scripts can still crash my system, but such issues became much less common, and I could reduce it further by shutting down unused applications.

And *that* brought me to iterating on a script to handle the builds completely.  Since I haven't written a "tech tip" post recently, I wanted to walk through this, since writing it led to discovering a few techniques that I'll probably need again someday, but also probably won't remember how.

```sh
#!/bin/sh
zmachine=gargoyle
back=$(pwd)
dir="."

if [ $# -gt 0 ]
then
  dir="${1}"
fi
```

We start with the initialization, with nothing particularly innovative.  If you want to use something like this, replace `$zmachine` with whatever interpreter/emulator that you happen to use.  I named the variable after the [Z-machine](https://en.wikipedia.org/wiki/Z-machine), which I associate with Inform, even though the ecosystem no longer uses it as a default target.

The last piece includes a "trick" that I've always used, but probably still worth pointing out:  The `$#` variable contains the number of command-line argument.  To make sure that we always have a target folder, then, I set the current folder as a default, then assign the first argument if supplied; `-gt` stands for "greater than."  I can call the script with `inform.sh` or `inform.sh path/to/game`, and it'll do the right thing, as long as the structure mimics what the Inform IDE creates.

```sh
cd "${dir}"
src=$(ls -1d *.inform)
ni=$(find "${dir}" -name "*.ni" -print | head -1)
```

I could---and probably should---find a better way of handling this.  However, for the other half of initialization, I move execution to the target folder and find the source file.

I call the name of that file---apparently, only one source file should ever exist---`$ni`, because Inform 7 started its development with the code name "Natural Inform."  Once I saw that, the name stuck with me better than "Inform 7" has.

```sh
if [ "$dir/$ni" -nt "$dir/$src/Build/auto.inf" ]
then
```

We have another condition, here, this one comparing the Inform 7 ("Natural Inform") input with the first phase's Inform 6 output.  The `-nt` operator stands for "newer than."  This prevents me from running the compiler if I haven't made any changes.

I *just* noticed a flaw, here, that I'll need to work out:  If the compiler output (`auto.inf`) doesn't exist, then the condition fails, which seems like exactly the opposite of how I would want this to run.  I don't have a solution yet, because---like I said---I only just discovered this problem.

```sh
  /usr/lib/x86_64-linux-gnu/inform7-ide/inform7 \
	  -internal /usr/share/inform7-ide \
	  -format=Inform6/32d \
	  -project "${dir}/${src}"
```

I copied this almost verbatim from the build log, calling the "first phase" compiler executable with the arguments that work.  As mentioned a few weeks ago, I couldn't find any documentation on those requirements.

```sh
  if [ $? -ne 0 ]
  then
    cd "${back}"
    exit
  fi
fi
```

When you learn a systems programming language---C, for example---you'll generally find out that you write the main program as a function, and that function must return a value.  A bad class never explains why, just tells you to do it.  But we organize things this way, because the UNIX-derived world has a tradition of returning a value to reveal the program's status when it ended.

A well-behaved program will return zero when it succeeds, and an arbitrary non-zero value to report an error.  Since you can use any integer as an error value, a program can even report different errors.  To the project's credit, the Inform compilers do this, so the script can compare the return value---shell scripts expose it with the `$?` variable, and `-ne` stands for "not equal"---to zero and, if it didn't report a success, restore the working folder and exit the script.

If the comparisons look silly, remember that characters like `<` and `>` see use as redirection operators, which confuses the parser if you try to use it in the middle of a condition.  Instead, we have these operators.

|Operator|Meaning|
|--------|-------|
|-eq|Equal to|
|-ne|Not equal to|
|-gt|Greater than|
|-ge|Greater than or equal to|
|-lt|Less than|
|-le|Less than or equal to|

We don't need to limit ourselves to numbers.  We can also compare strings, files---as described above---and even conditions.  But we don't need to think about that, here.

```sh
if [ "$dir/$src/Build/auto.inf" -nt "${dir}/${src}/Build/output.ulx" ]
then
  /usr/lib/x86_64-linux-gnu/inform7-ide/inform6 \
	  -wxE2kSDG $huge "${dir}/${src}/Build/auto.inf" \
	  "${dir}/${src}/Build/output.ulx"

  if [ $? -ne 0 ]
  then
    cd "${back}"
    exit
  fi
fi
```

The script then repeats the process for the second phase of compilation.  It compares the game file with the Inform 6 intermediate file.  If it needs to compile, then it calls the Inform 6 compiler with the arguments used by the IDE.  When the compiler exits, we check the status, and exit if it reported an error.

```sh
cd "${back}"
$zmachine "${dir}/${src}/Build/output.ulx"
```

Finally, the script returns to the original working folder and runs the game.

## Results

This basically does its job.  Distilling the above to the overall execution, the flow looks like this.

 * If the source file has changed since the last build, compile it.
   * If the first compiler failed, exit.
 * If the first compiler output has changed since the last completed build, compile it.
   * If the second compiler failed, exit.
 * Play the game.

This ensures that we never run more than we need, further reducing the chances of crashing my computer.

#### <i class="fa fa-terminal"></i>

* * *

**Credits**:  The header image is a screenshot of a session of the [original (mainframe) version of Zork](https://github.com/MITDDC/zork), released under the [MIT No Attribution](https://github.com/MITDDC/zork/blob/master/LICENSE.md) license.
