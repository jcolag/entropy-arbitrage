---
layout: post
title: Managing Priorities
date: 2021-06-13 07:56:12-0400
categories:
tags: [rant, programming]
summary: What is worth doing?
thumbnail: /blog/assets/tree-forest-snow-winter-girl-fog-819272-pxhere.com.png
offset: -49%
---

![Foggy roads](/blog/assets/tree-forest-snow-winter-girl-fog-819272-pxhere.com.png "Foggy roads")

In the past few weeks, I've seen...not "a surprising number" of comments online trying to buck the imagined software orthodoxy---because it's hard to surprise me after all these years in the industry---but I'll call the number anomalous and concerning.  It's concerning enough that I want to push back against the ideas, or at least try to build a framework around them before it gets out of control.

I'm talking about this in the context of software, but there's something like the sentiment in every industry.  The most generic version of this, looks something like the following.

 > People *say* that we shouldn't reinvent the wheel, but sometimes you probably know how to make a better wheel or might get a lot out of a new kind of wheel.

There are other versions that blame the problem on "managers" as some abstract group that (somehow) doesn't know anything about the actual work and exist to slow everyone down.  There are versions imagining some weird [cancel culture]({% post_url 2020-07-12-tolerance %}) unfairly destroying the careers of people who choose to re-implement things.  And there are versions that don't bother trying to justify the idea of redoing existing work.

In a lot of ways, this connects to the idea that "everything is the top priority," on some projects, so nothing gets done.  I'll get to that at the end, once we've pulled the framework together.

## Reinventing Wheels

One of the big problems in the software industry is that---even though "don't reinvent the wheel" has been an idiom for a long time, at least as old as the 1840s---most people quickly trace the idea of not rewriting *software* to [Netscape](https://en.wikipedia.org/wiki/Netscape).  At the end of 1998, the team decided that [Netscape Communicator](https://en.wikipedia.org/wiki/Netscape_Communicator) had become so complicated that the company's best direction would be to effectively start everything from scratch.

Credible rumors say that executives were promised that it would be finished in nine months---a length of time so pervasive in bad estimates, that the assumption must be that whatever's good enough to produce a baby should be good enough to produce software---and instead took years to get back to where they were.  During that time, they were bought out by America Online, and eventually spun the browser off into the project now known as [Firefox](https://en.wikipedia.org/wiki/Firefox), one of the cornerstones of Free Software, these days.

So many people have retold the Netscape story, though, and so few companies have been transparent enough to tell their own disastrous rewrite stories, that people with less experience---particularly developers who haven't been through a rewrite that failed---tend to assume that everybody has generalized from that one example, and that fears are overblown.  Sometimes, they'll have a mediocre excuse to imply that prior developers weren't as good at rewriting things, because *now* we have automated tests...which are actually just programs that the same group of developers wrote, but that nobody has rigorously tested.

It's funny to hear young developers suggest that their predecessors wouldn't be able to handle reimplementing things, because the lack of free-licensed software actually means that we all spent a *lot* of time reinventing things that we knew existed.  One of the reasons that old software is so simple is that we didn't have *time* to produce more than the bare minimum.  The generation before me often needed to figure out how the project was going to put *text* on the screen, which you might imagine eats some time out of the schedule.

Nobody remembers those days fondly.  It was a lot of boring, repetitive work, without much to show for it, which brings me to...

## Return on Investment

Because it's apparently a foreign concept to many people outside finance---where I spend basically none of my time, by the way---allow me to introduce and generalize the idea of [Return on Investment](https://en.wikipedia.org/wiki/Return_on_investment) (RoI).  The easy definition is that it's the quotient when you divide the profit (the amount of money that an investment gives) by the amount of money that it cost (the initial investment).  Finance people use this to talk about "efficiency," and use it to compare opportunities, so that they can try to get the most money back for just having the money to invest.

That is, if you double your money, the return on investment is 2∶1.

The idea is fine by itself, if we're just dealing with money, but making things generally only involves money indirectly.  Everything has a cost and a value to *somebody*, but most of that is invisible during the actual work.

### Valuing Work

Consider that, if you're at work, every minute that you spend "on the clock"---no matter how you spend it---is associated with a value to you and has a price to your employer or client.  That value is something like your hourly wage times some fudge factor that accounts for any non-pay benefits.  Smarter managers or clients might also figure in the price of replacing you as a value that is saved.  You might not think about it in those terms, but your manager or client probably does; if you spend an eight-hour shift at work solving crossword puzzles instead of working, somebody at the company knows how much of their money that you "wasted," by not providing more value to them than they provided to you.  If you want a more political example, when labor groups go on strike, their argument is that the owner will lose far less money by giving in to the demands than they will by replacing everybody who has gone on strike.

We can argue the ethics of work and whether taking an extended break is *actually* wasteful some other time.  For now, it should just be obvious that, in an office or other place of employment, your "time is money" in a literal sense that shows up on spreadsheets.

Something that we think about less is that our *personal* time also has a value.  That's an easy idea to dismiss, but it's also easy to see that different enticements are required to convince us to spend our time on different things.  You might not want to help a friend move to a new apartment, but you might do it if they offer to buy lunch.  When I was a kid, many indoor shopping malls had a public relations office that would send employees out to the floor to ask people to take surveys, and they were open about the statistics showing that the likelihood of someone waiting to answer all the questions increased with the amount of money they offered.  There are few occasions where people would refuse an arbitrarily large amount of money to work on a vacation day or in an evening.

We might not always place a *financial* value on time, but it wouldn't take a sophisticated auction to find an average price.  So, when we spend a few hours on a project, you can argue that you're spending or investing an equivalent number of gavvo[^1], based on what else you could do with that time and/or how much someone could pay you to do something less interesting.  I'll grant you that it's not a comfortable idea, but it's fairly useful.

#### The Puppy Postulate

Years ago, I was in a discussion where we started talking about Free Software and the general idea of "finding" software on the Internet.  Because most of my friends and colleagues are...let's use the term "organizers," we quickly started putting together a list of what "free" might mean.  It looked something like this, based on the actual costs.

 * **Free as in concert**:  You can have an experience associated with the offering, and the relationship ends there.
 * **Free as in pizza**:  You can take and use the offering, but the relationship ends there.
 * **Free as in speech**:  Like the Free Software people talk about, you have the right to use the offering to almost any degree you like, but you also have the responsibility to defend that freedom for yourself and others.
 * **Free as in sample**:  You can take and use the offering, but it isn't going to work for anything but trivial cases, and is used to lure you into buying something.
 * **Free as in printer**:  The offering exists to sell you expensive things, like ink-jet printers are sold at a significant loss to sell overpriced ink.
 * **Free as in mattress**:  The offering is garbage, being given away because disposing of it properly would be more difficult.
 * **Free as in puppy**:  You can take and use the offering, but doing so means accepting the responsibility to become the offering's caretaker for the rest of its life.

The last item makes an important point about calculating investments:  If I choose to implement my own version of [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security), because I don't like that [OpenSSL](https://en.wikipedia.org/wiki/OpenSSL) doesn't have enough maintainers to keep up with security vulnerabilities like [Heartbleed](https://en.wikipedia.org/wiki/Heartbleed)---even if I consider my initial labor to be free---I would now have the responsibility to maintain my project and keep up with vulnerabilities.  That's now an ongoing cost that is part of the investment, but invisible at the start.

That ongoing cost can easily dwarf the initial investment, which is why you can find a huge variety of think-pieces about how to "make Open Source more sustainable."  And despite the variety, the answer that they come up with is always to find someone (else) to pay the developers to make free things.

### Valuing Results

Here's something that, if you're a professional in any field, you should know:  What's your contribution to your employer or client?

Seriously, that's something that you should know.  When it comes to renewing a contract, asking for a raise, or anything else, you should have a decent idea of how much your work contributes to the company's revenue.

If you're a sales representative, that's probably one of the most prominent things on your mind.  But even if you "only" clean the toilets, your work reduces the chances of employees getting sick, which saves the company some percentage of that population's work hours and insurance premiums, which could be an enormous amount.  And if you're a software developer, engineer, or other "knowledge worker," you should know your marketing and sales teams and their work well enough to understand what customers buy based on the features you work on and/or what those features enable your colleagues to do.

I once had an awful job.  The company had just been acquired by a giant competitor, and our product was so well-established that there wasn't much actual work to do.  I attended more birthday lunches for people who didn't even work with us than I received bugs or features to work on.  However, the one valuable part of that job---other than a paycheck to basically work on personal projects---was a management process class that the parent company required us to take as they transitioned to that process.  Most of it was mind-numbingly obvious, but the centerpiece of the process was "everybody works in sales."  That is, everything that you do, whether you actually sell things, or design them, or support the people who do those things, your work eventually affects somebody's purchasing decision.

That information not only helps you when you need to negotiate with your employer, but it also helps you set priorities, which is where we're going with this discussion.  This value is the return on the time that you (and your colleagues) have invested, and the tasks with the highest return on investment *should* have the highest priority.

In software, the value might be creating something new.  But it might just as easily making something tailored to someone's specific needs.  Or it might be learning more about the field.

And again, it's a little uncomfortable to think about it this way, and we might have trouble putting things into dollars-and-cents (or your favorite currency equivalent) terms, but the tasks that we undertake outside work *also* have value.  Many (paying bills, cooking, and so forth) keep us alive, which allows you to do everything else.  Some entertain us or make us better people.  And while I'm not suggesting that you necessarily should, you certainly could put a price tag on those things or determine some value on them.

## Putting It Together

I once had a *different* awful job.  The first year was a lax environment in a small company, where nobody really had a roadmap for the product.  The second year became a stereotypically toxic workplace, with individuals publicly reprimanded for things out of their control on a regular basis.

However, as bad as that job was, there was one recurring idea (along with a bunch of nice colleagues suffering together) that I found worth the terrible overall experience:  If a developer asked to implement a feature, the developer was tasked with working up a proposal, including a detailed estimate of the time that the change would likely take---I talked about [estimates]({% post_url 2021-01-27-estimate %}) back in January---and the expected value that the change would bring to the company.

That is, we were asked to analyze the return on investment.  If the feature---or the rewrite, looping back to the start of the post---is going to take two programmers a year to finish, will the change bring in or save more money than the salary and benefits for two programmers?

A better proposal might start with talking to the support team to find the recurring problems that customers have.  Features that solve those problems are not only a potential sales opportunity, but also produce an *immediate* financial benefit of reducing the burden on the support line, by solving the customer's problem before they make contact.  But also, never forget that software is like a puppy:  If you're not figuring in the cost and labor of taking care of it over its lifespan, then you haven't calculated the cost.  And if you're rewriting software, that's *two* puppies, not one.  The original puppy doesn't just vanish.

### Take It from the Top...

Let's return to Netscape.  They proposed taking the majority of the company's developers for nine months, as their investment.  What was the return?  At the end of the process, the goal was to have the same features that they started with, so the project wouldn't increase revenue.  I'm sure that they could argue that a better design would save developers time in the future---lessening the ongoing "puppy" cost, once nobody cared about the old version of the web browser---which we might calculate as (roughly) equivalent to having the developers work some extra time in a week without pay.  But we need to ask how many hours the new design would save, which requires carefully studying how the developers worked *before* the proposal.  And then, you'd need to calculate how many of those "extra hours"---really, just more work each employee can handle during the day without being slowed down---would pay off the initial investment.

In other words, rewriting a web browser was almost certainly a waste of money.  The return on investment was tiny, possibly negative, so it wouldn't have made sense to pursue it, no matter how much it might satisfy the developers.  There might have been a similar benefit to be had by just teaching the developers the history of the system, so that they could better understand the decisions that were made.  That, and rewriting some small areas that are particularly problematic, might have kept Netscape relevant.

Of course, I use Firefox as my primary web browser, so that's not the version of history that I *want*, but it could have happened that way.

## Art Imitates Life

That's how work projects...well, work.

For personal projects, we can apply similar guidelines, as long as we're willing to be open-minded about what constitutes a "return" and what constitutes an "investment."

I'll give you an example of my own, here.  Early last year, I started rewriting an old project of mine, [**Bicker**]({% post_url 2020-01-06-bicker %}).  I'd guess that the total investment was somewhere near eighty hours, though I admit that I admittedly didn't think to track my hours at the time.

The return on that investment?  It hasn't made me any money, of course, but the following have improved my life, I think.

 * It got me back in the habit of committing something to GitHub every day.
 * I updated my Ruby on Rails skills to the modern versions of the framework, which I have since put to use on [**All Around the News**](https://allaroundthe.news/), and am currently using for Secret Project #2 that [Entropy Arbitrage newsletter](https://entropy-arbitrage.mailchimpsites.com/) readers are in on.
 * Included in learning modern Ruby on Rails, I also learned how to use React---which I had been using for other projects at the time---with Ruby on Rails, though I have not had a need to do so again.
 * I now have some familiarity with some additional technologies, such as [Libravatar](https://www.libravatar.org/) and showing previews of mentioned URLs.
 * I proved to myself (and a couple of colleagues) that writing tests after the project has mostly completed isn't much harder than writing them as you go.  Doing so even turns up some sorts of bad design.
 * I wrote around a dozen blog posts, which became the start of my Monday [developer journal](/blog/tag/devjournal) posts, ensuring that---along with the Friday [social media roundup](/blog/tag/linkdump) posts---I'll always have at least *two* posts per week, even after I ultimately give up on the other weekly projects.  As long as I keep writing the blog, I'll at least start the work week with a developer journal and end it with a Twitter summary.
 * It provided entertainment and satisfaction to see a project that I used fifteen years ago become useful again.
 * It adds a mostly complete project to my portfolio (such as it is), which I can show prospective employers and clients, including a record of most of the development.
 * It's not *ready* for that role, but I can see a path where I use Bicker as the centerpiece of a business like [Disqus](https://en.wikipedia.org/wiki/Disqus).  It's a sleazy business model---all but requiring tracking people across the web---which is why I haven't taken the steps to make that easy, but it's certainly an option, if I ever need it.
 * The new design is clean enough that I'm more likely to maintain it than the original version.

I haven't tried (and won't try) to convert those items to gavvo values to strictly compare with my consulting rate, but they qualitatively feel like a good trade, and I think that's more than good enough for a project the size of **Bicker**.

I probably won't do it again, though.  My other products of that era don't have the business case that they used to.  For example, [Agile development](https://en.wikipedia.org/wiki/Agile_software_development) has convinced developers that there's no longer a need for project management software, which kills the market for a modern (and working) version of [**eManagr**](https://emanagr.com/).  Crowdfunding and collaboration sites are now trivial to find, meaning that a new (and working) [**Agora/Open**](https://agoraopen.net/) wouldn't have much of a chance to compete in the market.

That reminds me, though, that I should probably do something with those domain names, since I'm probably not starting the servers up again...

My point, regardless, is that the "return" on your investment is allowed to be education, fun, or anything else that you value.  Some projects bring enough value to justify them.  Some don't.

### Exceptions

There's one case where I'd say that, if you chose it as a value, then you're probably wasting your time:  Novelty.

I see this argument more than would make me comfortable.  There's a weird, romantic notion that a developer writing something from scratch without any plan is going to somehow produce something innovative...accidentally, I guess.  It's a terrible argument, because it relies entirely on the fictional trope of an ignorant person making a breakthrough, because they "don't know" about limitations.  The argument is undermined pretty severely, because nobody can find a case where this has happened, despite *centuries* of work on formal thought.  Plus, when it comes to algorithms, where this fantasy is usually indulged, we can literally prove the performance of the best possible algorithm for the available data and mostly derive that algorithm based on the proof, so developing without a plan just means hoping to stumble across the solution that could have been found at the start.

In other words, if you think that you need to reinvent something because the world will just be better with an extra one available, or if you have no idea what benefit your project might be, then you're trying to pawn "free as in puppy" off on someone, and---bluntly---you have no idea what you're doing.  Your time would be far better spent learning more about your field, so that you can reason about your projects.

The situation reminds me a lot of the days when people used to insist that doctors were hiding medical breakthroughs with household products from us, and that if we only had the courage to try treating our diseases with salt, vinegar, or scouring powder, we'd all be healthy.  How many of those people went on to change the world with their innovation?  Zero, though some got rich selling their self-help books to suckers.  Some also spent time in the local emergency room.

## Wheels within Wheels

I should follow up on a small point that I made about programming in the days before widespread Internet access and abundant Free Software libraries/frameworks.

Back then, as I said, reinventing wheels was routine.  I wrote *three* different Windows 3.1 programs to display an interface and connect it to library functionality based on a specification, because I couldn't reuse code written for other companies.  I've worked on software where the exception handling was written by hand, every time, using [`setjmp()`, `longjmp()`](https://en.wikipedia.org/wiki/Setjmp.h), and the [C Preprocessor](https://en.wikipedia.org/wiki/C_preprocessor).  Once, I needed to implement text input and output in assembly language, because the client commissioned a custom [BIOS](https://en.wikipedia.org/wiki/BIOS) from a contractor that turned out to be broken.

You can find many terminal-based tools that simulate a multi-window desktop, and most of those were written from scratch.  I once interviewed with a company where my prospective colleague needed to implement the [Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite).  Just about everybody working for more than fifteen years has needed to write custom code to print dates and times.  The same goes for logging, which is why it's hard to find two programs from more than a few years ago with anything like similar log formats.

Did the returns warrant any of that duplicated investment?  I'd guess not.  There are so many things that we *could* have written, if we could have skipped the parts that somebody else already handled.

And I know, you can't wait to ask.  I can hear it.  "Wasn't the code better, because it was written custom for that project?"

No.  No, it wasn't.

At best, we might have saved a few kilobytes by not implementing features that we didn't need in one instance.  But it has been a *long* time since a kilobyte of memory or disk space was worth much.  Even in early home computer software, developers would just add another floppy disk to the package and swap the required pieces into memory---with an assist from the user changing disks---when necessary.  The idea of "software bloat" is perpetrated by narrow-minded people who can't believe that other people use features that they don't care about.

Given the choice between "wasting" a few kilobytes of memory or leaving out a useful feature for time, only an obsessive person would consider saving the memory.  That's pathological---rather than responsible---behavior.

Similarly, there's one group that is still forced to reinvent things routinely, to a pathological degree:  Students.  They get education out of the deal, and the cost of the duplicated is usually minimal, so it works in that context.  But *nobody* considers programming classes to be a model for how people should function in the workplace or in personal projects.

## Reinventing Wheels, Again

So, let's go back to the original question posed.  When there's an opportunity to do so, should we rewrite existing software?

If you paid attention through the post, you know that the answer is that it depends on how much work goes into doing so, what the reward is for doing it, and how those two values compare.  And if you don't know the cost or the reward, don't ask until you do, because the answer will only make you unhappy.

And this should also explain the ties to prioritization, and why some people can't seem to make decisions about what needs to be done first.  Again, the answer is the task with the highest return on investment.  Why?  Because if that's the *only* task to be accomplished, then it'll at least provide the most value in the least time.

I know, you're going to try to tell me that you can't tackle the task with the highest return on investment, because it's blocked by another task...and so, you've answered your own question, by pointing out that one task *enables* the other, making it the higher return.

It's a handy tool for making decisions.  Not only does it help you actually make the decision, but it forces you to think about what you care about in a project, which can keep you from making something opposed to your values.

It's especially useful, if you're opposed to meetings.  After all, once you start estimating how much it costs to bring everybody to a room, it becomes much harder to justify doing it to listen to someone read something that could've been sent as an e-mail.  And that at least reduces the non-interactive meetings in favor of meetings where everyone's presence is actually valuable.

* * *

**Credits**:  The header image is [untitled](https://pxhere.com/en/photo/819272) by an unlisted PxHere photographer, made available under the terms of the [Creative Commons CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/) license.

[^1]: The gavvo is the national currency of [Graustark](https://en.wikipedia.org/wiki/Graustark), because we wouldn't want to give the impression that this only works for dollars...
