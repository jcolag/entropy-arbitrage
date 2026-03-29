---
layout: post
title: Software Crisis on Infinite Oofs
date: 2026-03-29 07:47:12-0400
categories:
tags: [programming, rant]
labels: [career, harm, software]
summary: A reminder that we never had a problem writing code, only getting it to work
thumbnail: /blog/assets/TAF-ARCHIVE-Dev-6456542222.png
description: Let's look at the actual problem of programming and how to (start to) solve it.
spell: Oofs gvfBvL turvy topsy OLpLBw borderColor fillColor mkiiYV Telephonics Grumman Hazeltine Prolog umHtNh Rocq sqrt
proofed: true
---

<script src="/blog/assets/chart.js"></script>
{% include mathjax.html %}

* Ignore for ToC
{:toc}

Somebody recently asked me about my preferred technology stack, and that turned into a lengthy rant[^BK6UPd].  It seemed worth trying to capture that in a post, for people who have had problems that they can't put into words because we stopped talking about the idea.

[^BK6UPd]:  I know, how uncharacteristic, right?  Me, turning an innocent question into a preachy lecture...

![A glassy, metallic face looking up and to the left, with glassy eyes shattered and cracks above the temple](/blog/assets/TAF-ARCHIVE-Dev-6456542222.png "I gather that some people feel like this during allergy season...")

And I suppose, to help put things into words, we might as well start there.

## Definitions

Back when I went to school, we didn't explicitly talk about it often, but every topic had a common undercurrent[^gvfBvL], that we needed to plan and organize to forestall the [Software Crisis](https://en.wikipedia.org/wiki/Software_crisis), and we needed to design new tools to eliminate it.  You can read Wikipedia's attempt to distill decades of public conversation and research into a handful of paragraphs, but three items stand out in what they refer to in the past tense.

[^gvfBvL]:  Apart from the undercurrent that every class covers extremely similar ground.  Ideally, each class should reinforce and build on the prior classes, but a cynic could see every class as little more than applications for the handful of core data structures, stacks, queues, lists, trees, hash tables, and so forth.

- Projects exceeding budgets and time allocated to them
- Low-quality and inefficient software
- Unmaintainable code

I know, it seems mind-boggling to imagine a software industry plagued by cost-overruns, low quality, and a complete lack of maintainability, doesn't it?  Imagine the turvy-topsy world where teams struggle to push software out the door on time, and most of what gets out there has severe problems, rather than today when nothing ever goes wrong.  Seriously, they position this as an artifact of some Dark Ages.

> With the increase in the complexity of the software, many software problems arose because existing methods were inadequate.

Apparently, we have adequate methods now, and I guess that we now nail the schedule, with software that always meets and exceeds expectations, and developers can fix problems and add features lickety-split.  End of post, I guess.  {% emoji person shrugging %}

## Difficulties

You can probably see the problem in the article.  The "reasons" that they cite focus on the sudden increase in processing power.  And since we have grown accustomed to that, problem solved.  But somehow, we still have all the symptoms despite no longer having a problem.  Allow me to provide a...well, not a different cause, but a distillation and analysis of the causes that happen to all fit into one idea.

**Complexity grows with possible interactions.**

Honestly, you don't need to know anything more than that to understand the overwhelming majority of software failures.  When the people who Wikipedia editors cite blamed more powerful computers, they shot at the messenger.  Additional processing doesn't create the problem.  It makes the problem more apparent to a wider variety of projects as they take advantage of the additional power.

## Examples

Do you know why you programmers should [avoid `GO TO` statements {% cc %}](https://www.cs.utexas.edu/~EWD/ewd02xx/EWD215.PDF)?  You avoid them, because using them means that *any pair* of lines of code might *directly* interact.  The difficulty of managing your program---designing, budgeting, scheduling, writing, testing, maintaining, and whatever steps I omitted---has become quadratic, proportional to the square of the number of lines of code.  Refusing to arbitrarily jump around the program limits the possibilities to sequential statements that you can see on the screen at the same time.

Why do we engineer everything in the system to discourage you from writing self-modifying code, software that rewrites itself as it runs?  If you do that, then the difficulty of managing it has become functionally infinite, because anything in the program can interact with not only anything else in the program, but anything that could potentially end up in the program at some future point.

## Exponents and Encapsulation

By the way, I lied (or oversimplified) above, when talking interactions through static code.  Because data carries information from instruction to instruction, you can have interactions of arbitrarily large sets of instructions, such as the entire path through the program.  Worse than quadratic (*n<sup>2</sup>*) expansion, that looks more like exponential (*2<sup>n</sup>*) expansion.  But the moment-to-moment interactions look quadratic, and arbitrarily jumping around affects how you can deal with those.

You remember exponential growth rates from prior posts, right?  The "hockey-stick charts" all describe exponential growth.  To refresh memories, let's look at a chart comparing exponential growth to the aforementioned quadratic growth.

{% chart OLpLBw||{
  type: 'line',
  data: {
    datasets: [
      {
        label: 'Exponential',
        data: [
          1,
          2,
          4,
          8,
          16,
          32,
          64,
          128,
          256,
          512,
          1024,
          2048,
          4096,
          8192,
          16384,
          32768,
          65536,
          131072,
          262144,
          524288,
          1048576,
          2097152,
          4194304,
          8388608,
          16777216,
          33554432,
        ],
        fill: true,
        borderColor: '#b96645',
        fillColor: '#b9664520',
        tension: 0.1,
      },
      {
        label: 'Quadratic',
        data: [
          1,
          4,
          9,
          16,
          25,
          36,
          49,
          64,
          81,
          100,
          121,
          144,
          169,
          196,
          225,
          256,
          289,
          324,
          361,
          400,
          441,
          484,
          529,
          576,
          625,
          676,
        ],
        fill: true,
        borderColor: '#1468a3',
        fillColor: '#1468a320',
        tension: 0.1,
      },
    ],
    labels: Array.from(Array(26).keys()),
  },
  options: {
    responsive: true,
  }
} %}

Anyway, this hints at how we have "solved" the Software Crisis so far.  If you can limit the points at which parts of a program can interact, then you can reduce the difficulty of managing it.  Object-oriented programming, functional programming, design patterns, application frameworks, and more all try to convince[^j1399v] developers to only allow interactions through narrowly defined gateways, places where someone can audit what happens at those gates.

[^j1399v]:  Because computers can run any valid program for the platform, a sufficiently stubborn programmer can find a way to retain and import any bad habit, so we can only ever encourage better behavior.

Encapsulate a feature into a package that no outside code can inspect or affect, and you can rigorously prove that your feature works as advertised.  I mean, don't get me wrong, here.  You *won't* rigorously prove anything, because nobody wants to pay for that kind of labor, but you could definitely ship that one piece verifiably bug-free and compliant with the requirements, if you wanted to do it.

## Revenge of the Exponents

You can probably see where this will end up, though.  Limiting the size doesn't prevent an explosion of difficulty.  It can only *postpone* when the difficulty emerges.  After all, when you have your tiny, clean packages that you (could) have proven correct based on the requirements, what do you do with it?

Correct, you connect it to other packages.  Because each package limits its scope to minimize its difficulty, it'll need to interact with many other packages, and you have now reintroduced your exponential complexity, because every connection now presents a potential problem.  The smaller the pieces, the more you'll need to accomplish your goal.  You'll still get exponential growth in the management complexity, but with a somewhat smaller value for *n* at any given time.  I hate to invoke the field, but exponential curves have something of a fractal nature, where no matter how you change the starting conditions (*n*), the base, or duration, it looks like it starts slow before quickly accelerating.

If you don't believe me, consider one procedural question:  Given a program with *n* lines of code, what average size should your components have to minimize the number of interactions?  Seriously, think about that question.  If the complexity of a program *doesn't* grow exponentially for some size of component, then that size should make itself readily apparent.

Anyway, this reminds me that you technically need to know *slightly* more than that complexity grows with interaction points:  Checking the functionality does **not** scale exponentially.

## Other Procedural Camouflage

We also "fixed" this with a different approach, one that some people will find controversial for me to even mention:  We converted the industry to "agile methodologies."  Honestly, I don't entirely mind the agile approach, and sympathize with some of its motivations.  But we also need to admit that the mechanics---breaking work into short "sprints" that end with listing the things to fix and updating the next sprint's schedule based on the newly discovered work, while abandoning a full specification or schedule---completely cede the ground on complexity.  The method fully embraces the Software Crisis instead of solving it, by saying that we'll actually *never* finish the project, because every two weeks doubles the number of things that can go wrong.

Alongside this, we have mostly moved to web technologies.  And this also camouflages the Software Crisis on schedules.  At the start of my career, you might ship a new version of software annually, and the organization poured effort into maximizing the chances that it wouldn't need any fixes so that the team could move on to new features.  Now, we have the common wisdom that you ship as often as possible---even after every change, for some projects---to the server, because you only deploy to the server, and "let" (force) the users to check for bugs.

Sub-idea that we'll ignore here for the moment, the number of technologies that don't actually do anything more than wrap existing features, but maybe in the wrong way so that it becomes slower and brittle.  For example, as much as I have enjoyed working with [React](https://react.dev/), it really only creates a new, separate syntax for [Web Components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components), and it pushes HTML (the presentation) into JavaScript (management code), taking longer to display the page *and* providing more things that could go wrong on the way to displaying things.  It popularized a useful programming model, but because control bounces up and down the technology stack to propagate data, it also quickly becomes difficult to understand all those interactions that I've talked about since the top.

Notice how those three (ignoring the "mediocre library" thing) ideas interact.  Instead of the complexity exploding immediately, we developed strategies and processes to hold off the disaster.  For our schedules, we only think about the next few weeks.  And while most shops don't *entirely* shrug their shoulders on quality, we have generally opted to optimize for frequent updates over careful updates.  I don't want to say that a given project shouldn't make one or all of those decisions.  But I do want to make the point that each of them camouflages or accepts the symptoms of the Software Crisis.

By delaying the onset of recognizable complexity, we get further into projects before realizing the actual cost, and [sunk costs](https://en.wikipedia.org/wiki/Sunk_cost) mean that most people will refuse to walk away.  Agile processes, for all their benefits, dismiss the complexity and maintainability problems as something to worry about during some future two-week sprint; we even renamed "unmaintainable code" to [technical debt](https://en.wikipedia.org/wiki/Technical_debt), emphasizing the fix-it-in-post-production (to borrow from film) idea.  Continuous deployment, for all its benefits, makes low-quality software an ordinary part of life.

## Technical Debt

As a side-note, since I invoked the term, we should probably talk about technical debt.

I like the metaphor a lot, because it precisely describes what happens, even if nobody wants to believe it.  We take an expedient but ill-advised action now, saving labor now, with the expectation that we'll need to pay for it later with compounding interest.  To phrase it in more concrete terms, on a still-hypothetical project, I might choose to copy and modify code everywhere that I need the feature.  I *should* take the code, make it work for each variation, and encapsulate that for more robust and reliable reuse, but {% key CTRL %}-{% key C %}, {% key CTRL %}-{% key V %} can go so much faster for some uses.  In this case, I have "borrowed time" that I can use to get other things done.  However, I'll need to pay that debt back, not only in eventually doing the job right, but in how, every time that functionality needs fixing, somebody needs to remember to fix every copy of the code, not to mention the additional interaction points that increase the complexity of the project, which describe the interest payments on the debt.  The metaphor really does work well.

Despite the value of the metaphor, teams don't treat it like debt.  If you borrow money, you ask questions such as the interest rate, the term of the loan, and the value of what you can do with that extra money during that time[^PUoiC7].  If the value that you can get out of the loan doesn't outweigh the cost of borrowing, then you don't borrow the money.  Having forgotten and hidden the Software Crisis, though, teams don't make the same calculations for technical debt.  We act like technical debt arises out of the ether, and put "Refactor[^MRMtf9] Component-XYZ" onto the backlog for some future sprint, even though working around sloppy old code accounts for a significant fraction of every task, mimicking the person who only pays the minimum on their credit card balance while occasionally wondering why that balance keeps going up.

[^PUoiC7]:  More crass, but also sometimes relevant, will you need to pay the debt back yourself?  If you can pass the responsibility for repayment on to someone else, that changes the math dramatically.

[^MRMtf9]:  For the non-programmers, "refactoring" describes the process of reorganizing code into a more sensible and maintainable set of components, ideally reducing points of interaction.

## Lines of Code

I'll actually add a fourth problem, something that *absolutely* has benefits, but also compounds the complexity problems:  Code generation.  When you use a web application framework, you generally provide some specification---a set of data models, for example---and run some utilities that build out all the code that provides the basis for your application.  Under ideal circumstances, you leave most of this code alone and only add what makes your application interesting.

However, your application now has piles of code, and more importantly piles of potential interaction points, that you didn't create and may never bother to validate.  It *should* reduce the difficulty to not need to do not need anybody to write and test that code, because (one hopes) the application framework developers put more effort into most cases than individual developers could, but it still leaves you with many more interaction points that might go wrong.

Again, I find code-generation mostly helpful, especially if you can do it through a reliable, audited process, and it keeps that code behind some interface that restricts interaction.  We haven't gotten there yet, for reasons that elude me, but even failing that, *not* writing and debugging boilerplate code improves things better than everybody writing and debugging (in effect) the same code.

### Crisis As a Service

I won't belabor this point, because I wrote an entire post detailing the [documented productivity problems with LLMs]({% post_url 2026-01-18-using-ai %}), but do you know what generates lots of code without any consideration for the number of interaction points?

Yeah.  {% emoji sparkles %}

We have companies proud to have these machines churn out code as quickly as possible, massive technical debt feeding the Software Crisis.  And that bill will come due.

Like I said, though, I don't want to spend time on this again, when I try to keep that other post updated when new research comes out.

### Go Small and Go Home

And at the other end of the spectrum, the reactionaries---in politics and technology, as it turns out---in the industry whine about "bloat," grumbling that everybody should take out any features that they (the speakers) don't personally use regularly.  They cheer and venerate minimalism, insisting that any developer making software with friendlier interfaces, translations, accessibility, and so forth, has a delusion of some sort.

They see the Software Crisis, but like the Wikipedia page suggests, they can only see a solution in pretending that computers haven't advanced since the 1970s, where every byte matters and only a certain privileged demographic had access to any computers.

Don't get me wrong, here.  Companies absolutely *do* spend time on features that no user wants.  Every media website monitors your usage while filling up the screens with advertisements, pop-ups insisting that they need to flood your e-mail inbox or send you notifications or whatever.  Everything now has an AI chatbot to politely ask if you want to do the only thing that you can do on the page/screen while covering the buttons that you need to do it.  Following Apple's example, every commercial operating system vendor wants to decide whether you should have permission to use any particular piece of software.  Everything wants your attention, needs an account, wants to send you text messages, wonders why you don't want to *hang out* with it, because it thought your were buddies.

The Free Software people use the term "anti-features," because nobody pays for a product or service and wishes that wasted more of their time and worked less reliably.  They do all serve purposes, though, only not on your behalf.  You can agitate for stopping companies from doing that, but calling it "bloat" won't work, because the companies see it as useful revenue.

## What to Do

Now we get to the hard part.

We already know that I don't know how to solve this problem.  If I could, then I'd probably go on the road racking up enormous consulting fees while saving the corporate world trillions.  Or I'd at least produce perfect software cheaper and faster than anybody else out there.

Let me sketch out what I do know, though, so that we can all cross our fingers that enough people with different experience can move the ball forward far enough to maybe make some real progress.

### Admit to the Problem

First, as they say, you can't solve a problem when you refuse to admit that you have one.  We have an entire industry in such deep denial that we talk about the Software Crisis like we do the [Cuban Missile Crisis](https://en.wikipedia.org/wiki/Cuban_Missile_Crisis), something that threatened to destroy the world, but only lasted a couple of weeks a few decades ago.

What does an admission look like?  Well, we can't only state "the Software Crisis has endured" or the like.  We need to schedule with the expectation that every line of code written, every variable added, every database row, every external file, and so forth, all of that magnifies the complexity of the project.

### Full Plans

With that admission of a problem in mind, I'll make enemies among the Agile zealots here, but even if you follow Agile methodologies---and yes, many teams have good reason to do so---everybody should still understand what the finished product looks like.

I hope that you can see the reason for this.  If a team only works on its little corner of a project, and only thinks in terms of the next two-week (or however long) sprint, then the team has no functional chance of spotting how quirks might come together downstream to become a problem.

### Scheduling

Years ago, I wrote a post on [schedules and estimates]({% post_url 2021-01-27-estimate %}), and I want to reiterate what I consider one of the most important observations about software work.

Good schedules break down in a 2:1:3 ratio.  At best, for every hour that a team spends writing or rewriting code, they'll spend twice that planning the work and three times that testing and fixing the work.  And in my experience, if you try to cheat that ratio, because "it doesn't need a design" or "we'll ask the developers to not create bugs"---real ideas that I have seen at companies---you'll make the ratio worse.

In other words, if you decide to jump right into development without thinking through the requirements or design, then you'll still need to do the work, and probably redo it, as your half-coded plan turns out to not solve the problem.  If you decide that you can get by without testing---your team doesn't make mistakes, or you have automated tests---then novel show-stopping bugs will make it through the door, because automated tests can only test for what the developers already knew about.

And you know that I mean "clock time" and not "calendar time," right?  If you have five developers but only one QA person, then that person needs about fifteen times the amount of time that each developer takes.  One person can't do the design work for an entire team, either, if you want it done right.

When you build those aspects into the system properly, though, then you start to build the system in ways amenable to designing and testing, and look for ways to improve that.

### Testing

Once we know (or accept) that we want to rigorously test, and we start allocating time on the schedule to do so, then it should follow that we want to maximize the value of the time spent on testing.  That means automation.

Currently, most teams that I have seen have two separate kinds of testing.  Developers have "unit tests" that confirm decent outputs for common inputs, and then manual testing from the user perspective.  Some QA groups cleverly log their tests, creating a script to repeat on every release.  Log in.  Log out.  Try to log in with an imaginary user.  Try to log in with the wrong password.  Test with an extremely long user.  Test with an extremely long password.  And so on, because a change could have broken how any of these affect the system.  Did you try different operating systems and web browsers, by the way?

It also burns testing time.  Why do new bugs slip through?  To fulfill their duties, the testers need to re-litigate everything that they have ever seen break before, because that kind of problem will embarrass the team more than a new bug.  Forget about testing the exponentially growing set of potential bugs, especially those that only occur on a flaky Internet connection, with a user whose family name has an apostrophe, on a computer with a different product running, with a dozen identical rows in a database, on the second Tuesday of the month, and so forth.

We can solve at least some of that problem by *automating* every test after each release.  It doesn't give the testing time an exponential scale, but it at least means that humans don't run the same tests twice or stop testing certain aspects to make room for others.

And yes, that means building the user interface so that an outside program can manipulate it.  Electrical engineers have the idea of [design(ing) for test](https://en.wikipedia.org/wiki/Design_for_testing), and we really should steal that.

By the way, automated testing also allows for the introduction of so-called [mutation testing](https://en.wikipedia.org/wiki/Mutation_testing), which can further shore up existing testing and make better use of human-testing time.  Similarly, so-called Property-Based Testing suggests randomly or exhaustively generating the possible inputs for tests, then narrowing down the inputs to those that cause problems.

### Compartmentalize

This doesn't change from current practices.  Keep code broken into reusable and comprehensible pieces, and build on those.

The instinct still works, here, at least to some extent.  As demonstrated, it doesn't resolve the crisis, but a system designed as components of components, at least has places to get toe-holds.  Even if we can't guarantee that an *entire* application definitely works as advertised, we can at least guarantee a core and work outwards as resources permit.

I should note, here, that functional programming often does a somewhat better job of encapsulating code than other approaches, because they tend to prioritize unchanging ("immutable") data and similar means to improve the reproducibility of any particular calculation.  However, once you have persistent data outside the application---information in a database, for example---you no longer have that clean mathematical model.

It also seems worth mentioning, here, that this can include cutting features, hacking out old code, and otherwise minimizing program size.  However, that creates a new problem that you also can't really grow an audience past a certain point, which makes this less business-friendly.  And even if you only do this for fun, small verified utility programs *externalize* the costs by leaving scripts to build up the other features.

### Plan to Fail

In college, I had a professor who talked about software reliability, and used to sketch out a failure-rate curve like the following.

{% chart e57Mvh||{
  type: 'line',
  data: {
    datasets: [
      {
        label: 'Failure (%)',
        data: [
          0,
          25,
          43.75,
          57.8125,
          68.359375,
          76.26953125,
          82.2021484375,
          86.651611328125,
          89.98870849609375,
          92.4915313720703125,
          94.368648529052734375,
          95.776486396789550782,
          96.832364797592163086,
          97.624273598194122315,
          98.218205198645591736,
          98.663653898984193802,
          98.997740424238145352,
          99.248305318178609014,
          99.436228988633956761,
          99.577171741475467571,
          99.682878806106600678,
          99.762159104579950509,
          99.821619328434962882,
          99.866214496326222161,
          99.899660872244666621,
          99.924745654183499966,
        ],
        fill: true,
        borderColor: '#b96645',
        fillColor: '#b9664520',
        tension: 0.1
      },
    ],
    labels: Array.from(Array(26).keys()),
  },
  options: {
    responsive: true,
  }
} %}

The specific numbers on the graph don't necessarily mean anything; he did sketch it on a chalkboard, after all.  However, the shape describes the idea that potential faults add up quickly to having a near-complete chance of some failure or other, eventually.

Other professors mocked this, insisting that this described hardware, not software.  Hardware wears out over time, but software (they insisted) has a dangerous period where you might find some bugs, but if it survives that period, it'll probably never go wrong.  They said this in the years before everybody needed to scramble to fix [Y2K](https://en.wikipedia.org/wiki/Year_2000_problem) bugs in decades-old software, so we know that they had their acts together when it comes to predicting software that'll probably work forever. {% emoji eyeroll %}

In fact, in the years since, we have seen this sort of graph proven out, I think.  For any significant project created through current processes, it will have plenty of bugs, only some of which will get caught by the Quality Assurance process...a process that (by the way) companies keep trying to squeeze out as a waste of money.  And so the longer that people use the software, the more likely it becomes that somebody will trip over one of those bugs too subtle for testing to find.

Why talk about this?  Because we need to plan for literally unthinkable problems.  If we could think of the problems, then the developers would have already found a solution, or the testers would have found a way to provoke the problem, so part of every schedule should take time to plan for disasters.

In here, I would include all the instrumentation and monitoring systems that try to capture the context of faults while reporting them.

### Verify

Calling back again to when I took computer science classes, textbooks and (some) professors made a big deal about *correctness*, the idea that every one of our code "compartments," however we structure them, represents some assertion of functionality---it does *this thing* under *these conditions*---and that, in a correct program, somebody has proven those assertions true, the process of [formal verification](https://en.wikipedia.org/wiki/Formal_verification).

Certain professors would regale us with stories of the Pentagon[^mkiiYV] hiring teams of experts with higher degrees showing up to build mathematical models of code in order to prove its correctness.  Every one of these stories emphasized the cost, and that you would only ever do this for the most critical code.

[^mkiiYV]:  For those who might care but don't already know, I live and grew up on Long Island, the pile of sand to the east of New York City that looks suspiciously like a fish.  It has had a lot to recommend it, but almost every institution also has some connection with the Cold War defense industry, because companies opening offices here caused a population explosion.  My college campus, for example, really only existed because the location made it walkable to recruit students from Fairchild, Sperry, Telephonics, and about a dozen other major defense contractors, plus a quick ride from Grumman and Hazeltine.  The Cold War had ended by the time I went to college, but almost everybody with experience had some connection to the Pentagon, often their only experience with big-budget projects.

At around that time, artificial intelligence groups saw [Prolog](https://en.wikipedia.org/wiki/Prolog) and similar "logic-based" programming systems as the path forward, making it possible for software to take on some of the work involved in the proofs.  I don't know if we have a *direct* line of descent, here, but today we do have similar [proof assistants](https://en.wikipedia.org/wiki/Proof_assistant) to shoulder at least some of that burden.

Full disclosure, I keep promising myself that I'll finally learn one of these systems[^umHtNh] and start applying them to my own code.  And I say that because I do think that this comes the closest to helping us solve the Software Crisis, not by giving us more code to not understand, but by helping us understand what code we do have, by letting us know whether our code actually does what we claim.  And we don't even need a small army of experts with doctoral degrees.

[^umHtNh]:  Right now, [Rocq](https://rocq-prover.org/) interests me the most.  If you check that Wikipedia list, you'll notice that only two assistants check all the possible boxes that they list, Lean and Rocq.  Lean, ironically, has started accepting AI-generated fixes, which makes me uncomfortable, given their purpose, leaving the one that recently rebranded because the French name sounded a bit dirty.  I have installed it, but haven't investigated too deeply.

### Pay down Technical Debt

I mentioned this before in general, but as part of a solution, treat technical debt *like* debt.  Take out debt when it enables the team to work better.  Understand the effective "interest rate."  Factor managing the debt into schedules, and try to pay it off before it consumes the schedule.

Many teams have (or claim that someday they'll have) periodic "refactoring sprints," where the team refuses to add new features or fix bugs for the duration.  That, however, sounds pathological, like a person spending one month every year only paying credit card bills instead of paying rent or buying food.  It can help solve the problem, but usually comes at a new cost.

However, the idea of servicing the debt remains important.

### Better Tools

Returning again to my school-days, the literature used to talk about the **expressivity** of programming languages, the idea that every of a ratio between the amount of code written and the amount of work that the code does.

For the traditional example, let's say that you want to initialize a list with the even numbers in some range.  In a language with low expressivity, you need to manually type each number into the program; the longer the list, the more time you need to spend.  In a more-expressive language, you can define the relationship between the distance into the list (the index) and the value that you want, so that you can say that each item in the list should hold something like `2 * i + 14` to give you some even numbers.  We have programming languages that fall all around that range.

At this point, the conversation would shift towards the speculative.  What *could* we have in a language that would make it more expressive?  As a typical example of a suggested feature, if you have a loop---itself a tool of expression, preventing us from repeating code to repeat tasks---that lists a set of items, and you want all pairs, then you need a nested loop, one loop that covers every item, and another that, for each item, covers every item again.  If you want triples, then you need a third nested loop, and so forth.  The programmer needs to keep cloning that loop inside prior clones, making for an unreadable mess that takes time.  However (the examples would go), what if the language already knew that pattern could exist, and so had a "keep nesting this loop" command?  Then, you might have code that can generate any length sets of all items with compact code by saying "nest the loop based on this variable to that maximum depth," cleanly readable and far more expressive.

Somehow, the conversation stalled at this point.  We got some *minor* advances.  For example, Ruby has the single-line conditional statements.

```ruby
x = 5 unless y > 4
```

Likewise, many languages have added slightly cleaner syntax for common looping operations.  On the whole, though, we have mostly stopped talking about improving expressivity, and I'd bet that most readers have never even heard the term in this context.

Actually, I can think of one example where we still see a push for higher expressivity, configuration languages.  Configuring systems such as [Augeas](https://augeas.net/docs/language.html) and [Puppet](https://help.puppet.com/core/current/Content/PuppetCore/puppet_language.htm) push to pack more meaning into less code, but do it in a narrow space.

Maybe we should change this.  In the mainstream, it feels like new programming languages care more about compilation speed, [LLM-friendliness](https://www.nerd-lang.org/), [provability](https://en.wikipedia.org/wiki/Dafny), asynchronous operation, and so forth.  And while those goals can benefit certain kinds of projects, they don't reduce the number of interactions the way that higher expressivity would.  For clarity, I don't have a list of features in mind that I'd add to express more.  But I know that, if expressivity hasn't changed much in thirty years, it probably didn't happen because we hit a maximum ability to express ideas before most computers could natively do floating-point math.

The closest "real" language that I can think of trying to do this at all well?  [CoffeeScript](https://coffeescript.org/) of all things.  It looks like an attempt to make JavaScript look like Python, but you can see from the examples on the page that it reduces the amount of (common) code significantly, even if it still looks a lot like JavaScript, and still *results* in the bulkier JavaScript, which would defeat our purpose.

Similarly, we could see improvement from application frameworks that find some other way of providing boilerplate functionality *other* than generating code for the team to maintain indefinitely.

## Wrapping

This has all weighed on my mind, recently, because I have seen so many projects come along claiming to make this work easier, but we get ideas such as the following.

- Maybe dynamic languages should have some (but not much, and not well-considered) compile-time type-checking.
- If we trim microseconds off the compile time, developers can test their changes that much sooner.
- Generate as much code as possible, and let humans deal with making it all work.

The last feels, in some ways, terrifying.  After all, we can all see that the AI-bubble will burst.  We don't know when or how much of the real economy it'll take with it, but everybody sees that the arithmetic doesn't hold up.  It still takes too much energy to run these things.  They still do a mediocre job of everything.  It still creates copyright liability to use the output.  We could go on about the problems, but the specifics don't matter as much as the upshot:  Nobody (other than Nvidia) benefits from the push, and investment money has started drying up.

If that doesn't crash the entire economy and technology sector, this leaves companies (and large open source projects) in a jam of low staffing and a lot of shoddy code that nobody understands.  And that means staffing back up[^NDE1ld], at least for companies that can still afford it after burning money on AI subscriptions.  But without a plan, they all now live in the middle of an accelerated Software Crisis, something that they probably don't believe exists anymore.

[^NDE1ld]:  Especially, I would imagine, candidates that didn't let the chatbot deskill them, an effect that we *still* see happening in study after study of LLM chatbot use.

And all the above, about two-and-a-half thousand words up there, only nudges us in the right direction, I fear.  These solutions only fall into a small handful of categories, after all.

- Plan for software to grow worse.
- Reduce the number of interaction points in the software.
- Confirm software's correctness.

Remember, the crisis itself comes from the fact that potential problems grow exponentially, but finding and rooting out real problems can only happen linearly.  I bring this up again, because that math tells us that my start on solutions doesn't get us there.  "The math doesn't math," as they say.  In fact, the math looks something like this.

$$A \times 2^x - B \times y$$

The result of that calculation gives us the amount of code that can go wrong, the prospective pitfalls in that failure graph above that, given enough time, will cause a failure.  Resolving the Software Crisis means getting that difference as low as possible while still adding features.  Reducing the interaction points (*x*) helps, but not as much as we might expect.  For example, if we can halve the number of interaction points, then that part of the calculation looks like this, a help, but not a massive help when we know that *x* will keep climbing.

$${2^{x\over{2}}} = \sqrt[]{2^x}$$

Similarly, improving validation and testing (*y*) helps, especially if we can make it grow faster than linearly.  We can juggle staffing and schedules (the coefficients *A* and *B*) to mildly impact the situation.  But all this only provides a complete solution for the tiniest programs, the smallest values of *x* where we have the time to rigorously test the code and prove it correct.

And because of that, you can see why I say that this can only serve as the start of the discussion.  More ideas must exist out there.  The software industry has existed in a significant capacity for what, sixty years?  That doesn't compare to something like civil engineering, out maintaining structures for thousands of years[^2AfAux], but you know, that seems like enough time and enough people to come up with some useful ideas.

[^2AfAux]:  Civil engineers have worked so well for so long that the field has a reputation for laziness, because for almost any question that you might have about designing a workable structure, they have the information pre-digested on a table.

As such, while a lot of this feels a bit dire, I also have some hope that approaching software engineering like an engineer might actually help us get solid work out the door consistently.

* * *

**Credits**:  The header image is *TAF ARCHIVE Dev 6456542222* by [Trent Anthony Francis](https://www.trentanthonyfrancis.com/), made available under the terms of the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) license.
