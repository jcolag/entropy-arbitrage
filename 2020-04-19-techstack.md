---
layout: post
title: Advice for Aspiring Career-Hoppers, Part II
date: 2020-04-19 07:44:24-04:00
tags: [quora, career]
summary: Hopping to a software career
thumbnail: /blog/assets/25388715424_75a7389c41_c.png
offset: -25%
---

* Ignore for ToC
{:toc}

As promised, this is the second part of a [short series](/blog/tag/career/) to provide some quick guidance for people who would like to reach out feelers into a possible software development career.  As I mentioned in the [first post]({% post_url 2020-04-12-career %}), a lot of this material is recycled from some of my old Quora answers, updated for current times and the tone of the blog.

![Hands at a keyboard](/blog/assets/25388715424_75a7389c41_c.png "Hands at a keyboard")

To be completely clear, I'm writing this because I know there are people out there who are bored and can use the distraction of picking up a new skill.  If you come out of self-quarantine with a marketable skill, that's great.  But if you don't, you're no worse off than you were, so it's also fine to not be interested or to give up part-way through.  This is entertainment, not recruitment.

This installment is about the technological considerations you'll probably want to look at to get moving.  It'll probably continue on next week, too---I want to keep these posts digestible---before we get to the non-technical issues.

## Picking a Technology Stack

When I refer to a [stack](https://en.wikipedia.org/wiki/Solution_stack), here, I mean a set of technologies where each piece generally rests on the foundations of another.  In web programming, the stack is usually something like the following.

 * A computer, which I'm going to ignore just now,
 * A programming language,
 * An [object-relational mapper](https://en.wikipedia.org/wiki/Object-relational_mapping) that gives the language easier access to a database,
 * An [application framework](https://en.wikipedia.org/wiki/Application_framework), which provides...well, a *framework* for you to plug in functionality around a minimal application,
 * Some libraries to make the framework do additional things, and
 * A [front-end](https://en.wikipedia.org/wiki/Front_end_and_back_end) library to simplify building the user interface.

There are some issues to consider in this choice, some of which may be more important to you than others.  And incidentally, if you'd like some more information on databases, I recently posted [an overview]({% post_url 2020-04-05-database %}) about what databases are and---in extremely broad terms---how they work.

### Readability

Especially when you're starting out, you probably want the programming language to be something you're comfortable reading, because you're going to read a *lot* of it.  Consider the following code snippets.

```
users.each do |user|
  break if user[:age] > 65
  print user
end
```

or...

```
(~R∊R∘.×R)/R←1↓ιR
```

or...

```
len = trunc(log10(size * size)) + 3;
sprintf(fmt, "%%%dd", len);
for (i = 1; i <= size; i++) {
  for (j = 1; j <= size; j++) {
    printf(fmt, i * j);
  }
  printf("\n");
}
```

or...

```
OPEN INPUT sales, OUTPUT report-out
INITIATE sales-report
PERFORM UNTIL 1 <> 1
   READ sales
       AT END
           EXIT PERFORM
   END-READ
   VALIDATE sales-record
   IF valid-record
       GENERATE sales-on-day
   ELSE
       GENERATE invalid-sales
   END-IF
END-PERFORM
TERMINATE sales-report
CLOSE sales, report-out
.
```

Those all do *extremely* different things, so it's not a head-to-head comparison, but my point is that each language has its own design philosophy.  Some prize looking like English.  Some prize looking like mathematics.  Some just try to be more memorable versions of machine instructions and don't really care about the user's comfort level.

You might like the first one.  You might like the third one.  You might not.  My point is that you should start in a language that makes you feel comfortable, not a language that makes me or Mark Zuckerberg or "some loud jackass on the Internet who won't shut up about the best language ever" comfortable.  You're the one trying to learn, not us.  We already got what *we* want.

### Accessibility

You're just starting out, so you shouldn't spend money on something you might give up on after a week.  Fortunately, most tools are free, these days (except for a computer), but you'll find a handful of products that require a monetary investment.

Don't bother with them.  They might be useful, once you've gotten your footing, but so much is made available as Free Software and/or easily found at no cost that you're better off learning on the cheap and making an investment only after you've started taking to programming and can better evaluate what the paid tools offer.

Likewise, if you need to sign up for access, don't bother.

The *only* point where I would recommend spending any money to start is when you don't have easy access to a computer.  I'll talk a little bit about that, later in this post, since that is technically a part of your technology stack.

Accessibility of a different sort might also be an issue if you are living with any physical or psychological impairments, natural or imposed by your environment.  I can't give you a whole lot of actionable advice, there, since you know far better than I do what you need.  If you can't find clear instructions on how to connect your screen reader, increase the font size, move the buttons apart, use keyboard controls, use eye-tracking, turn off animations, or whatever assistive technologies you might need, there's a good chance that the developers didn't think about you, which is unfortunate.  [This thread](https://news.ycombinator.com/item?id=18414562) raises some particularly interesting points to look out for---or, if you're a tool developer reading this for kicks, things you should be thinking about to support more developers.

### Maintenance

This might not be easy when you don't yet know where to look, but you should make sure there's some life in the project.  If nobody is updating the software, there are going to be security issues, outdated processes, and eventually fewer opportunities.

Look for recent---within the last six months---releases, blog posts, and so forth.  The more current and consistent, the more likely the project is going to keep improving as you go forward and the easier it'll be to get help when you need it.

By contrast, I recently considered using two different technologies for a recent project, but neither has been touched in several years.  So, I threw those options out.

### Community

There are two aspects of looking at the community.

First, just about every piece of modern developer software (languages, frameworks, and so forth) has mailing lists, forums, chat rooms, and similar places to interact.  Take a quick look at the interactions, there, to get a sense of the "culture" around those technologies.  Some going to be friendly and welcoming.  Some get frustrated with newcomers.  Since you're eventually going to need help from people with more experience, you want to make sure it's the former and that it has enough traffic per day that people will see your questions when you need them.

Second, if you are currently working (and are inessential enough to be social-distancing or we figure out [contact tracing](https://blog.ncase.me/onestepahead/) and/or treatments soon enough to go back to offices), your company *probably* already employs programmers.  That's a valid community.  Get to know them and consider learning what they use, since befriending them will get you a better response time and better help than any public chat room.  I can't speak for the programmers you work with, but some of the best time I've had on the job has been spending breaks helping people from other departments get through their problems.

### Job Opportunities

It doesn't really matter as much as you think, but since half of you are screaming at your monitor "all the jobs near me require [Var'aq](https://esolangs.org/wiki/Var'aq)," sure, go for it!

Don't *actually* pick Var'aq, though.  Not only are those job opportunities fictional to avoid offending a real community, but it's not well-maintained and there's almost no community.  I don't want the dumb joke coming back to haunt me in six months when people put it on their job applications.

But my point is that, if your goal is to get a job as quickly as possible and you live in a part of the world where local companies are heavily invested in a specific technology stack, that's a good enough option.

### A Last Resort Recommendation

As an expedient measure, I'm going to suggest that, if you can't find an option that you love and don't need a specific setup for a particular job market, you should probably just start with [Ruby on Rails](http://rubyonrails.org/).  Ruby's creator wanted the language syntax to look like English, within reason, and has spoken a lot about designing the language for the programmer instead of the computer.  Ruby and Rails are both kept up to date.  The community has directly invested in making sure it doesn't subtly (or directly) push people away.  And on top of that, the Rails idea of "convention over configuration" means that you'll spend much less time setting up your applications, leaving more time to work on the interesting parts.

It isn't perfect, of course, and I only recommend it *if* you have already looked at other languages and couldn't decide.  But it's a good enough starting point and, once you get your bearings, you can always learn whatever the companies near you are hiring for.

If you're already a programmer, though, keep in mind that the idea of a web application framework has spread quickly, and nearly every significant language has at least one framework associated with it.  See the [Comparison of web application frameworks](https://en.wikipedia.org/wiki/Comparison_of_web_application_frameworks) for a bunch.  For example, [Saetta Web Server](http://izysoftware.com/products/saetta-server/saetta-web-server/) appears to be a framework for C, something I never expected would exist.

## Hey, Don't I Need a Computer...?

Like I mentioned earlier, if you don't have access to a computer whenever you need it---I grew up with a shared computer in the living room that everybody in the family used for something different and then went to college where the software that my classes needed wouldn't work with my computer, requiring trips to the computer lab when it was open---this is one of the rare places I would recommend spending money for the sake of the experiment.

Specifically, if you can't test ideas out on your own schedule, it's going to be frustrating.  Even here, though, feel free to go cheap, because you're not going to notice a big difference in speed when you're just starting out, if you're just programming.

You have a few options, here, which unfortunately may be beyond what you're able to invest in terms of money or work.  I'm making the assumption that you need to *buy* a computer, here.  You might not.  Sometimes, people want to get rid of their old computers to make room, in which case you only need to find out about it and work out the social distancing complexities to get it home.

### Laptop

For a lot of people, the simplest route is going to be to just order some overstocked laptop from the retailer of your choice.  For about two hundred dollars, you can get a system that's a couple of years old and could last you for a decent amount of time.  It's a single unit, so it's just the one price.

The big problem with laptops, though, is that they're generally not made to be upgraded or repaired.  So, you're taking on some added responsibilities for making sure you don't drop and break anything---the connection for the power cord tends to be especially fragile---and dealing with disposal when the computer is (eventually) no longer usable.  Depending on your situation, you may also need to deal with the added responsibility of security, in that it's unpleasantly easy for someone to walk off with a laptop.

### Desktop

You might also think about a desktop computer.  You can often find better desktop boxes significantly cheaper than laptops (prices I see tend to hover around $150, even lower for a "single-board computer" like the [Raspberry Pi](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/)), *but* that price won't include a monitor or other display to see what's going on (and usually not a keyboard or mouse), which drives the price back up.

Sort of the flip side of someone walking off with your laptop, a desktop machine is less likely to vanish, but it requires dedicated space.

### Tablet or Phone

If you have an Android device and "root access," I haven't tried it and it looks like a lot of work, but it's apparently possible to install [Ubuntu](https://ubuntu.com/desktop) on the device, based on [this article](https://www.androidauthority.com/install-ubuntu-on-your-android-smartphone-765408/).

It's probably going to be slow and complain a lot about memory, but if you already have a phone (your own or someone's old phone they left in a drawer), the option is free, so that sounds good.

### Remote

The last basic possibility also requires already owning *something* that already has a screen, like a phone or a tablet.  It also requires a decent Internet connection and some extra work to set things up, but can be cheap and can be easily upgraded to something more powerful later.  In this case, you rent a server from a company and connect to it from your device.

The term you'll want to search for is [Virtual Private Server](https://en.wikipedia.org/wiki/Virtual_private_server), where the company buys extremely powerful computers and uses them to run many "virtual" (simulated) computers that you pay to use.  After you sign up, you can run something like [VNC](https://en.wikipedia.org/wiki/Virtual_Network_Computing) on your phone/tablet to connect to it.

It's not as convenient as a computer sitting in front of you, but it can work, with a little bit of preparation, research, and conversation with their tech support.  And it's relatively cheap, with the big companies in the field having a low-powered computer for a maximum of five dollars per month, but also charging less than a penny per hour, if you can turn it off between sessions.

It does have one huge advantage over the other approaches, though, and something you'll want to keep in mind as you work:  Because you're renting a server on the Internet, you can host your work publicly, meaning that you can show off to your friends and use the server as your portfolio.  And if what you're working on is useful, you can even look into charging for the service and having it pay for its own server costs.  Obviously, once you do that, though, you can no longer turn the VPS off after a couple of hours of work.

If it helps, I've been happily using [Linode](https://www.linode.com/?r=c507afa27d7e3f4879a9950a6f6b63243d7ea23d) to host my websites (including this one!) for more than ten years (and that's a referral link, if you want to support me but you can also easily find <https://linode.com> for yourself, if you don't...) and it's not hard to find ad campaigns on technology podcasts offering you a decent amount of free service on competitor [DigitalOcean](https://www.digitalocean.com/).  They both have excellent reputations and the single reason I chose Linode is that DigitalOcean didn't exist when I first needed the service.

Like I said, though, it's definitely not for everybody.  I'm talking about this so much because there's a lot to explain in comparison to "order a laptop," not because I'm pushing the idea.  But if you do have a phone/tablet and Internet connection, installing Ubuntu didn't work, and you can put a couple of dollars every month on a credit card, you might be able to get it to work out well for you until you can get a computer locally.  Even at five dollars a month, the cheap laptop is only going to be cheaper if it's still being used after three years.

## Next

After you've had some time to think about and investigate some technology stacks, next Sunday, we'll talk about what I think is generally a good way to learn the technology and specific things to look for.

#### <i class="fab fa-quora"></i>

* * *

**Credits**:  The header image is [Untitled](https://www.flickr.com/photos/wocintechchat/25388715424/) by [WOCinTech Chat](https://www.flickr.com/photos/wocintechchat/), made available under the terms of the [Creative Commons Attribution 2.0 Generic license](https://creativecommons.org/licenses/by/2.0/).
