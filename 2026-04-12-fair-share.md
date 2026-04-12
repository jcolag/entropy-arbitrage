---
layout: post
title: Fair Share
date: 2026-04-12 08:02:02-0400
categories:
tags: [economics, politics, rant]
labels: [taxes]
summary: Pitching an offbeat economic idea
thumbnail: /blog/assets/6848822477_7559e8c3a1_o.png
offset: -25%
description: Not quite eat-the-rich, but maybe make them more palatable for an eventual brunch.
spell: zrwmCL logit frac Georgism fdecomite
proofed: true
---

* Ignore for ToC
{:toc}

<script src="/blog/assets/chart.js"></script>
{% include mathjax.html %}

Somewhat similar to my post around the holidays about [judging politics by whether it enables connections]({% post_url 2025-12-14-connections %}), I have sat on this idea for a long time as one of my favorite crackpot pet theories.

![Presenting a pile of coins and a sprout in cupped hands against a semi-abstract background of more coins](/blog/assets/6848822477_7559e8c3a1_o.png "Time for a (pile of loose) change?")

Given the time of year in the United States, you can probably guess that this theory turns eyes towards taxation.

## OK, Define Fair

You see, I often have a pet peeve when people talk about taxation, especially in liberal and progressive circles.  I mean, I agree that we need to pay taxes, because we all have a stake in the future determined by the relevant government.  However, *the term* invariably shows up when it comes to wealthy people:  Paying their "fair share."

I hate the phrase, because they almost certainly believe that they pay more than their fair share...because they believe that "fair" means that they get money instead of paying it.  They keep *saying* as much, so I don't know why we'd try to use ideas that we know won't work[^zrwmCL].  But also, I don't think that any of us has any intuition about what fair might even look like, let alone a common enough view that we could encode into law.

[^zrwmCL]:  See also, "experts have found little evidence of voter fraud" as a bizarre euphemism for "Donald Trump still lies about voter fraud because he refuses to admit to losing the 2020 election" or "job creators" as a euphemism for "people who externalize their costs onto the public, requiring constant clean-up and litigation, generally from governments."

### Obligatory MMT Moment

Before we get to that, let me digress a bit.  The "fair share" thing feels even more nonsensical, because at least in the United States---as [Modern Monetary Theory](https://en.wikipedia.org/wiki/Modern_Monetary_Theory) points out---money pretty much grows on trees.  We don't get equal access to the tree, by any means, because...that would solve problems and make exploitation harder.  But since most people don't use cash for most purposes, most money gets into the economy because a bank added a number to a spreadsheet, and the Treasury gives it a thumbs-up.

It takes a *little* more than that, sure, like an expectation that someone will pay the money back someday, but not much more, and most of that added complexity exists to make the system feel legitimate rather than putting a hard restriction anywhere.  This means that, in a real way, taxes don't "go" anywhere.  They don't pay for anything.

When you hear somebody suggest that the Treasury issue a handful of trillion-dollar coins to cover the budget and avert a government shutdown, they acknowledge this.

Instead, sovereign governments spend money into the economy, and taxation takes money back out of the economy, a tool to reduce inflation.  This makes our first stop on the "fair share" nonsense.  You don't actually pay high taxes because of karma or to help poor children get school lunches.  You pay high taxes because doing so deflates the economy, making your money (and your income) more valuable.  If you have a lot of money, then you should pay higher taxes to make that money more valuable.

Alone, this already hints at where I think we want to go, that wealthy people have a far deeper motivation to pay high taxes than fairness:  Self-interest.

### Upkeep

And if we changed the system, so that the Treasury still actively created and distributed money?  In that case, taxes make more sense as maintenance fees.  It costs a lot to maintain a stable economy.  If you have a lot of money, you should *really* want a stable economy, so that your money doesn't accidentally vanish.  You want Treasury Agents and the Secret Service out there chasing counterfeiters.

## Tax Brackets

Anyway, back to the actual post, when I tried thinking about the broader problem, years ago, I fixated on tax brackets and how ugly they seem.  First, too few people understand what they mean, and so believe incorrect things like getting a raise might lose them money by putting them in a higher tax bracket.  It doesn't, because only the money *over* the threshold gets taxed at the higher rate, but the idea persists due to the presentation and lack of education.  In addition, though, the brackets don't scale.  I mean, in the United States right now, the government has set the top 2025 tax bracket starting at $626,351.  Here, let's throw in the table, on the chance that we want to work with this later or someone hasn't seen its like before, the latter more likely than the former.

|Rate|From|To|
|----|----|--|
|10%|$0|$11,925|
|12%|$11,926|$48,475|
|22%|$48,476|$103,350|
|24%|$103,351|$197,300|
|32%|$197,301|$250,525|
|35%|$250,526|$626,350|
|37%|$626,351|∞|

For those not familiar with the chart, and so that we all have the same context, you take your income[^CG-_E_], subtract the *From* value, take the *Rate* percentage of that difference, and add it to the *Rate* percent of the difference between each pair of lower *To* values.  Or in other words, if you make a million dollars, then you pay 37% of $373,649, plus 35% of $375,825 (250,525 from 626,350), plus 32% of $53,225, plus 24% of $93,950, plus 22% of $54,875, plus 12% of $36,550, plus 10% of $11,925.  After that, you mess with all the deductions that matter far less than you think.  Contrary to popular belief, if you earn enough money to bump you to the next tax bracket by a few dollars, only those few dollars get taxed at the higher level, while the rest of your income gets lower rates.

[^CG-_E_]:  Well, people like you and I start with our incomes.  The wealthy have lobbied for ways to juggle their money so that it doesn't actually qualify as income, a different problem to deal with.

Everybody making that final value ($626,351) up to as much as people can exploit, they pay the same fraction of their income as taxes.  If somebody earns trillions of dollars, that turns up the same percentage.

### Quick Aside

By the way, I don't understand how they choose tax brackets.  The largest increase comes at---for a family of four---around fifty percent over the *poverty rate*.  You can reach a stable lifestyle for your family, but increases beyond that feel like diminishing returns.  The next bump comes around when the family might actually have a comfortable lifestyle.  After that, increases shrug.

### Smooth

Putting those two oddities together starts us down an interesting path, I think, because we'd *want* to solve those problems (as normal people and not people who like to look things up on charts) by creating a continuous function, where each dollar earned ratchets up the tax rate by a tiny amount, from zero at the poverty line to whatever maximum tax rate we choose, and every value in between.

How does that function increase, though?  I mean, we could probably sit down with the current tax code and work out the function that cuts through the key points of the brackets, such as (quick messing around in LibreOffice Calc...) this not-quite solution.

$$Tax(i) = -0.00043 * i^3 + 0.56 i^2 + 121.65 i - 713$$

We all use computers and calculators to do this, these days, right?  Nobody actually sits down with a pen and paper, where the tables would save time?  Then this would make more practical sense, certainly.

My quick "ask an office suite to guess" function falls apart at the extremes, but for most "realistic" living incomes, the results of the function come fairly close to (deep breath) summing the repeated products of the differences.  That seems unsatisfying, though, even if it does create an infinite number of increasingly tax brackets (one for every dollar over $713) that decently approximate the existing tax brackets.

## Surplus Value

Instead, we probably want a function that taxes income by "the right" amount, whatever that should look like, rather than the amount that the government would otherwise take out.  What, then, *should* that look like?

Let me propose an idea that sounds a bit absurd:  We want to tax the "surplus value" created by *concentrations* of money.

I don't mean a wealth tax---though we almost certainly need those[^b096rR], too---but forcing money to act in an intuitive way.  After all, if you think about it for a bit, you'll notice that money doesn't add linearly.

[^b096rR]:  Large concentrations of wealth can only exist through exploitation, so one could make a solid argument that such money *should* belong to the community, as in taxed away to justify a stronger social safety net.

Sure, it *literally* adds linearly.  Fifty dollars plus twenty dollars equals seventy dollars, always and forever.  But money doesn't exclusively stick to the numbers, for some reason[^XAW9El].  Consider this in orders of magnitude, assuming no other access to resources, stranded in some random part of the country.

[^XAW9El]:  I did warn you that this would sound silly, but I do have a point, here.

### Orders of Magnitude

Given one dollar, at least in a lot of the United States, with some luck and care, assuming access to a grocery store with bulk bins, someone could potentially buy a day or so worth of food of dubious nutrition.  I haven't checked prices (and any prices I check might change), but I mean somewhere in the neighborhood of a cup of flour and a cup of (thinking of the cheapest protein options) yellow peas, certainly enough to fill them up for a day or two and not cause immediate problems, but not great.  And they'll need to cook the food, and probably need some shelter, not to mention some way of getting to and from that grocery store.  We have already exceeded the budget for the average recipient.

Given ten dollars, they could buy ten times as many ingredients, but they also have the option of higher-quality food, such as real vegetables, a small amount of fuel for cooking, and maybe even a bus ride to and from the store.  That frees up more time that can go to other aspects of survival.

At a hundred dollars, food stops looking like a problem.  At this point, our hypothetical subject now has the potential to get around and buy better clothing, a cheap tent, a cooking stove, or similar things that keep them safer or save more time.  They can't get all of them, but any represents a sudden and massive improvement.

Add another zero for a thousand dollars, and safety becomes possible; the person can live indoors, at least for a while, probably even with access to cooking appliances and food storage.  And you can see how this builds.  At ten thousand dollars, renting a room *and* food security *and* owning things becomes feasible.  At a hundred thousand, they can have a comfortable lifestyle.  As a millionaire, they can buy a home out-of-pocket, not only solving security problems but mapping them to an investment.

We can repeat this escalation to billions of dollars, and now hundreds of billions.  At that point, our hypothetical recipient can now plausibly own companies that destroy their competition and influence their own regulation, and other similar purchases that sound like utter nonsense.

No, really.  Have you ever thought about how you'd even *spend* a hundred billion dollars?  Even if you decided to send a million dollars to every single person whose future you care about, you'd need to come up with a hundred thousand such people.  And by the way, you'd need to move fast, because you'd probably need to keep that money invested rather than sitting around as stacks of cash.  It looks like a high-interest bank account---not how you'd actually invest that much money, but gives a floor for numbers---gives you five percent return per year, meaning that you get about 0.0137% or thirteen-point-seven million more dollars per day from *not spending fast enough*.

Most research in this area that I can find likes to talk about money actually having diminishing returns, because after a certain point, you run out of things to spend it on.  And while I get that aspect, it also reeks of propaganda, that we shouldn't worry about wages, because, you know, money doesn't buy happiness[^r142oy].  You notice that progression up there, after all.  More money provides access to more options.  At some point, those options include healthier choices, security becomes available later, and at another point, those options start to include power, including to bargain for cheaper prices or control how other people spend *their* money, which doesn't seem diminishing to me, even if I probably wouldn't have much interest in that kind of power, myself.

[^r142oy]:  The same people telling us not to worry about higher salaries also tell us that people in their forties don't own houses because they have the nerve to use ripe avocados as a spread instead of inviting the authors over for guacamole, and look at all these people who succeeded by depriving themselves of avocado toast after their parents gave them a house.

In other words, having a billion dollars provides a heck of a lot more value than one dollar repeated a billion times would, even though they describe the numerically same amount.  Or to put it another way, one dollar has much less value than one billionth of the value of having one billion dollars.  The concentration of money has a value of its own, and I *think* that taxation should target that surplus value, so that each dollar adds closer to only one dollar's worth of value.

### Wealth Hoarders

*I don't know, John*, I hear you cry from the back of the room.  *If that idea held true, then antisocial people would hoard wealth, and you'd end up with increasingly unstable systems that would bleed over into other fields.*  And...yes?  I'd like to introduce you to (someone insert a picture of me dramatically gesturing at everything around us) the world under late-stage capitalism.  If you want more than half-joking hand-waving, most studies show that economies with high [Gini coefficients](https://en.wikipedia.org/wiki/Gini_coefficient) have unstable economies, and then political polarization and instability.  Again, allow me to gesture emphatically at the economy, the political polarization, the climate, and so forth.

In other words, I agree with you.  If my idea holds, then the wealthy would destabilize the economy and politics, **exactly as they do**.  It doesn't prove my premise, but it tells me that the idea has something to it, if it can predict what we see.

### The Shape of Things

Granted, I don't know what that surplus value looks like.  I'll leave it to the economics people to work that out.  For now, we can imagine that it probably looks polynomial, for some value of *something*.

$$Value(d) = d^{something}$$

Or maybe I oversimplified, and we have something more sigmoidal, or rather the inverse, something that looks like the [logit function](https://en.wikipedia.org/wiki/Logit), but not that, since it only has a definition between zero and one.

$$logit(x) = ln(\frac{x}{1 - x}), 0 < p < 1$$

This escalates quickly, levels off for a bit, then escalates quickly again.

{% chart _jiMGB|A graph representing the hyperbolic tangent function, escalating quickly, leveling off, then escalating quickly again, as advertised, though strikingly hideous||{
  type: 'line',
  data: {
    datasets: [
      {
        label: 'Hypothetical inverse-sigmoidal curve',
        data: [
          -13.8155095579638,
          -2.94443897916644,
          -2.19722457733622,
          -1.73460105538811,
          -1.38629436111989,
          -1.09861228866811,
          -0.847297860387203,
          -0.619039208406223,
          -0.405465108108164,
          -0.200670695462151,
          0,
          0.200670695462151,
          0.405465108108165,
          0.619039208406224,
          0.847297860387204,
          1.09861228866811,
          1.38629436111989,
          1.73460105538811,
          2.19722457733622,
          2.94443897916644,
          13.815509557935,
        ],
        fill: true,
        borderColor: '#b96645',
        fillColor: '#b9664520',
        tension: 0.1,
      },
    ],
    labels: Array.from(Array(21).keys()).map((x)=>x/20),
  },
  options: {
    responsive: true,
  }
} %}

Again, not *actually* that function, because money probably doesn't have a finite range; you can have an unlimited supply of money *or* go into unlimited debt.  Plus, what a hideous graph!  But the shape of the function leaves us room for oddities such as the aforementioned studies alleging that more money doesn't help comfortable households.  And an infinite form would also allow for the way that debt acts similarly to money, seeming to get far worse than linear addition would suggest as the amount increases.

You can see this as the next step after continuous tax brackets.  Every dollar earned increases the tax liability slightly, so that every significant increase of income provides a consistent added value, rather than the wildly disproportionate escalation that we see today, probably reaching a point where higher income provides functionally no benefit at all.

## Too Much

*But won't that creative a dangerous incentive that prevents people from doing things that make them billions and maybe trillions soon?*  Sure, though we could argue the danger.  I mean, you can only get that kind of money through exploiting many people.  For example, how do you (potentially, allegedly) become the world's first trillionaire?

- Inherit billions of dollars from an Apartheid-era emerald mine.
- [Overstay on a student visa](https://archive.is/gzGpF) to the United States and then retroactively alter the record through a network of influencers modeling themselves on organized crime.
- Take massive government subsidies to set up a private space program.
- Use that space program to get massive government contracts, edging out national space programs.
- Use that space program to launch a satellite Internet service provider that governments rely on in emergencies.
- Buy "the public square" and turn it into a radicalizing propaganda machine.
- Use money from all that to create a large language model, taking the labor of many, burning fuel, heating water, pounding websites to scrape more data, and providing politically biased responses.
- Bring the enterprises under one roof.
- [Sell stock to the public {% cc %}](https://www.forbes.com/sites/tylerroush/2026/04/01/musk-closer-to-trillionaire-status-spacex-reportedly-files-for-ipo/) at an inflated price.

Therefore, yeah, we should probably want to take away that incentive, or at least redistribute that money back to the people who *actually* earned it (the public) when it does happen.

## Continuous and Escalating

Ignoring that horrifying *logit(x)* idea as too difficult to work with for a blog post, that gives us our polynomial model.  And honestly, if we add more terms to the polynomial function, we could get similar plateaus and even ranges where the added value per dollar seems to shrink, if we need that.  Regardless, the polynomial gives us a nice, clean function for our hypothetical taxation.

$$Tax(d) = d^{something} - d$$

If (granted, a big caveat) we built the model correctly, then somebody who gets a trillion dollars pays taxes that leave them with "only" a thousand times the value that somebody can get out of one dollar.  And for every dollar value that we give it, the function gives would give us a sensible result, with no discontinuities or confusing "getting a raise cost me money" mythology.

I'll leave it as an exercise to the reader---probably the same readers trying to work out the escalating marginal utility of money, already a huge ask---to work out how to adjust that function (or whatever replaces it) to provide a *maximum* income, as hinted at above.

### Maxima Again

I mean, again, if you can only come into a half a trillion dollars at once by exploiting people---inherit wealth from an unequal society, commit fraud, take plenty of government money, create pressure on governments, radicalize the public, steal more labor while polluting, and so forth---then maybe society should claw back most of that.  Especially if you [claim that sending COVID-19 relief checks caused inflation](https://www.jec.senate.gov/public/index.cfm/republicans/analysis?ID=37F5FA80-20FA-4A0A-8251-11CAB584B2C9) at a cost of three hundred billion dollars---and not CEOs literally bragging to investors about getting [good at pricing {% cc %}](https://www.fool.com/earnings/call-transcripts/2021/10/29/colgate-palmolive-company-cl-q3-2021-earnings-call/) during a crisis---then surely, *more* hundreds of billions of dollars than that going into a single bank account also inflates the economy.

It complicates the math to include terms that escalate further at high levels for that purpose, but like I said, I doubt that anybody seriously does all this on paper anymore.

On the other hand, if we set a maximum reasonable amount, then maybe that logit function starts to make sense.  I don't know.  Again, somebody needs to find that underlying extra value for any of this to even pretend to work, after all.

## Public Mistrust

Oh, and on the topic of exploitation, I might as well throw in one more idea, even though it almost certainly doesn't work with tax law as it stands today.  But if we wanted to overhaul the system to this extent, could we also bump up the tax rates for anybody previously working for a national government above some level who goes into the private sector?

I think of this primarily in terms of elected officials, where we can draw a bright line, though other people should qualify, such as appointees.  They draw a pension, enough to cover their needs.  We pay them to not need to work, because if they do work for industry, they bring their influence with them.  I'd as soon tax them a few hundred percent, personally, if they really want to work for big companies...

## Complex by Design

Oh, and we might as well make sure that we don't forget that the big tax companies [lobby to keep preparation complicated {% cc by-nc-nd %}](https://www.propublica.org/article/inside-turbotax-20-year-fight-to-stop-americans-from-filing-their-taxes-for-free) so that they can rake in money.

For almost everything relevant to your taxes, the organization that you work with notifies the Internal Revenue Service of what they need to know to calculate how much you owe them or they owe you.  They *could*, then, like in most of the rest of the world, mail you a letter with a bill or a check.  At that point, most people would move on with their lives, with a small percentage who would go through the process to try to prove them wrong and save some more money.

However, companies like Intuit have enough money that they can lobby politicians to force the government to maintain their *entire* business model for them, where all hundreds-of-millions of us, by law, go through the annual ritual where we process shoddy paperwork so that we can guess the number that the IRS already calculated months ago in split seconds.  Oh, and by the way, if you get the number wrong, you might go to jail.  No pressure.  Therefore, you go to an accountant, but probably a tax-preparation company, because they'll charge less.  And wouldn't you know it, the market has consolidated so that you get to choose between two entire companies.

They, in other words, have *too much money* and need a much higher tax rate.

## So What

Yeah, I know.  It beats me, too.  {% emoji person shrugging %}

I have had versions of this post floating around since long before I started the blog, though, so I mostly wanted to finally get it out to readers, in case it has something to it to build on.  Having nothing else to post a few days before most last-minute filers have their tax software open, then, made it seem like as good an excuse as any.

The post probably won't spark a revolution---[Georgism](https://en.wikipedia.org/wiki/Georgism) adapted to include intellectual property seems more appropriate to revolution---and probably won't land me one of those horrific FIFA Peace Prize trophies, let alone something credible.  Maybe it'll spark a better idea, or maybe someone will wow FIFA (Olive Garden[^rxl3jN], Nobel Committee, whatever...) by finishing off the math and showing that surplus value per dollar.

[^rxl3jN]:  Formally, I like to imagine, The Olive Garden® Never-Ending Salad and Breadsticks℠ Platinum Breadstick Prize in Macroeconomics...

We actually can, however, effect some change, at least, with enough effort.

- Before anything else, abandon the "fair share" narrative, which certainly hasn't helped yet.
- Then, starting from the end, in the United States, pass legislation that empowers the IRS to send the pre-filled forms to us, replacing the high-stakes guess-the-number games.
- Then, support a more progressive tax code, more brackets that increase as income increases, rather than assuming that the lower middle-class has money to burn or that we can stop caring at around half a million dollars, as long as the IRS does most of the work anyway.
- With that, replacing tax brackets with a function only makes sense, *cleaner* than code with long tables that people don't actually know how to read.

I don't know if that builds momentum for the other changes, but this would at least point in that direction.  And we probably want to do these other things, too...

* * *

**Credits**:  The header image combines [Making Money](https://www.flickr.com/photos/68751915@N05/6848822477) by [401(K) 2012](https://www.flickr.com/photos/68751915@N05/) and [Money](https://www.flickr.com/photos/21649179@N00/514737882) by [fdecomite](https://www.flickr.com/photos/fdecomite/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) and [Creative Commons Attribution 2.0 Generic](https://creativecommons.org/licenses/by/2.0/deed.en) licenses, respectively.
