---
layout: post
title: Go Nowhere Fast
date: 2025-06-15 07:33:12-0400
categories: 
tags: [harm, rant, politics, harm]
summary: More talk about terminology and assuming a common understanding
thumbnail: /blog/assets/9404714466_8215ff19d9_o.png
offset: -25%
description: Thinking about the use of certain bring-your-own-interpretation key phrases in technology, political, and other spaces.
spell: Nevius Haviland quicksort Muskovites sides-ness
proofed: true
---

* Ignore for ToC
{:toc}

{% include mathjax.html %}

I taught computer science classes for close to twenty years, so let's start this post with the sort of question that I might have posed---and maybe did pose---to an algorithms class.  Even if you don't program, I *think* that you can follow along, though.  And afterward, we'll talk about the real topic, instead of the shallow pretext.

![An advertisement featuring a young child trying to control a hunting dog, which aggressively indicates a nested ad for Nevius & Haviland Efficient Spring Shade rollers, giving us a pointer, pun intended, to buy the Efficient](/blog/assets/9404714466_8215ff19d9_o.png "They even put the word in scare-quotes for me...")

Ready?

## Efficiency

Identify the *most efficient* of the following solutions to sorting a list.  (If your eyes glaze over, feel free to page down until you start seeing English again, or at least my dialect of it.)

Do you like option A?

```ruby
permutations = [
  []
]
result = []

# Generate all permutations of the input list
for i in 0..(input.length - 1) do
  # For each element of the input list...
  val = input[i]
  perms = permutations.length - 1
  for j in 0..perms do
    # And for each partial permutation found so far...
    perm = permutations[j]
    for k in 0..perm.length do
      # Insert the current element of the input list into each position
      # in the partial permutation.
      p2 = perm.clone.insert k, val
      # Add to the list of permutations.
      permutations.push p2
    end
  end
end

# Remove all partial permutations.
permutations = permutations.select { |x| x.length == input.length }
for i in 0..(permutations.length - 1) do
  # For each permutation...
  array = permutations[i]
  sorted = true
  # Check if we have an incomplete sort.
  for j in 0..(array.length - 2) do
    sorted = false if array[j] > array[j+1]
  end
  # If sorted, announce.
  result = array if sorted
end
```

Do you like Option B?

```ruby
input.sort
```

Do you like Option C?

```ruby
swapped = false

begin
  swapped = false
  for i in 1..(input.length - 1) do
  # For each element
    if input[i - 1] > input[i]
    # If it seems out of order with its neighbor, swap them.
      input[i - 1], input[i] = input[i], input[i - 1]
      swapped = true
    end
  end
  # Stop when we get through an entire cycle without swapping.
end while swapped
```

Or maybe you'd like Option D?

```ruby
input
```

Heck, one more for Option E?

```ruby
width = 1
n = input.length

while width < n
  # Repeat until the piece size hits the entire thing.
  i = 0
  while i < n
    # Split the array into fragments of the current size.
    left = i
    mid = [i + width, n].min
    right = [i + 2 * width, n].min

    merged = []
    l, r = left, mid

    while l < mid && r < right
      # Reorder the fragments.
      if input[l] <= input[r]
        merged << input[l]
        l += 1
      else
        merged << input[r]
        r += 1
      end
    end

    # Put the array back together.
    merged.concat(input[l...mid]) if l < mid
    merged.concat(input[r...right]) if r < right
    input[left...right] = merged

    i += 2 * width
  end
  width *= 2
end
```

I could actually provide dozens of alternative options, and in a real class, I might write each option in a different programming language (because people have preconceptions about certain languages and efficiency), but I've already used up enough space with the five options, and no matter what you see on the list, you should all get roughly the same answer:  You should refuse to answer, because I asked a trick question for rhetorical effect.

Seriously, why would I go through all that in a blog post, if the question had a clear answer?

Option A's sorting algorithm takes the most brutally systematic approach, by generating every possible ordering of the input elements and checking whether each ordering looks sorted.  Option B uses...whatever the language provides for sorting, probably [quicksort](https://en.wikipedia.org/wiki/Quicksort), but nobody cares if they don't need to maintain it.  For Option C, we have a [bubble sort](https://en.wikipedia.org/wiki/Bubble_sort), probably the first algorithm that any student learns.  Option D assumes that somebody else sorted the input for us.  And Option E gives us a [merge sort](https://en.wikipedia.org/wiki/Merge_sort).

And yet, I say that you can't and shouldn't try to find the most efficient option, because to find the "most efficient," we need to know *efficient at what?*

We might care about speed, memory usage, clarity of purpose, instructional value, developer time, or any number of other parameters, or a bunch of them all at once.  And until you know what you care about, you don't know anything about efficiency.  To get something into production that almost certainly works as quickly as possible, Option B gets pretty efficient, because somebody else did the work of writing and testing it for you.  To provide an example of what sorting actually *means*, I think that Option A provides more efficiency than any of the alternatives, while Option C gets more efficient as a project to teach new programmers about algorithms.  Option D seems most efficient if you really do get your input already in order, which happens more often than you might think.  And Option E floats somewhere in between those various points.

Some might perform better on memory-limited systems.  Others might perform better when you have a massively parallel computer.  And if you need to do the work on pen and paper, you might want something entirely different.

Without that information, without that *goal*, efficiency doesn't have any meaning.  You can't have efficiency as a goal, because efficiency only optimizes resources with a goal in mind.

In Computer Science, many students and more than a few instructors confuse efficiency with *time complexity*, how some equivalent of processing cycles increases as the input length changes.  Or, more specifically, we might confuse efficiency with the *asymptotic upper-bound time complexity*, or how long the task will generally take, in the worst case (upper-bound), as the input length grows arbitrarily large (asymptotic).  We do this, when we do, because in any substantial running software, you want to know if the system can keep up with inputs in real time, or if we need to manage the input; for example, if your video-processing algorithm can't keep up with input, then you can't use it for streaming.  Using that branch of academia, we can say that the different approaches have the time complexities in the table, in what we call Big-O notation, for reasons that you'll probably figure out.

|Option|Time Complexity[^1]|English, Please?|
|------|----------|-----------|
|A|O(n!)|Exponential time|
|B|O(n lg n)...probably|Linear-and-logarithmic time|
|C|O(n<sup>2</sup>)|Quadratic time|
|D|O(1)|Constant time (or wrong)|
|E|O(n lg n)|Linear-and-logarithmic time|

[^1]:  For those of you who haven't sat through a logarithms class, *lg* stands in for any logarithmic function, because they all look the same---always rising, quickly at first, but more slowly the larger the input---except for a constant coefficient.  You might remember some of that from a junior high math class or, if you want to get weird about it, working with a [slide rule](https://en.wikipedia.org/wiki/Slide_rule), which simplifies arithmetic using logarithms.

Yes, quadratic as in polynomials with a squared variable, and yes, logarithmic as in junior high school math where you need to find the exponent to raise some base (usually 10 or *e*, but 2 in computer science) to get some number.  No, nothing specific like addition or (constant) multipliers, because those fade away as we make the computers faster; when we say $$O(n^2)$$, we might actually have calculated something like $$362 n^2 + 5372 n + 89926$$ or whatever.  We only care about the broadest behavioral aspects, because that determines how well we can keep up with input, and we can usually make the actual numbers go away by spending money[^2].

[^2]:  If that doesn't make sense, and you remember early television, think about the often-recycled and -parodied episode of **I Love Lucy** when Lucy gets a job at the chocolate factory.  The conveyor belt speeds up, and she can't keep up, *but* we could fix that by cloning a second Lucy, or a third, to pick up the slack.  No matter how fast the conveyor belt gets---the coefficients---some number of clones or bionic arms or whatever would take care of it.  However, if processing each piece of candy required comparing it with *every other piece of candy* that came before it, for example, now increasing the speed of the conveyor belt will quickly outpace the economics of cloning and bionics.  In the same way, a faster computer can address some speed problems, but not all, because for some processes, large inputs still require too much work.  Therefore, we drop the multiples (the speed of the conveyor belt) and additions (the time that it takes for each employee to start work in the morning) to only look at the dominant term in the polynomial.

Do I *really* want to talk about first-year computer science, though?  You know me better than that...

## Other Fields

You can probably already see where I want to go with this, right?

If you try to make---using the example above---your code run faster, but you don't have any time pressure, then you've wasted your effort.  And likewise, if you assume that people have a plan when they try to improve efficiency, you can see what they care about.

Efficiency enables goals.  Efficiency expresses values.

I've made this mistake exactly like everybody else has.  For example, I guarantee that I've made the same comment as everyone else that nobody should call the [Department of Government Efficiency](https://en.wikipedia.org/wiki/Department_of_Government_Efficiency) by that name, because---until it took over the [US Digital Service](https://en.wikipedia.org/wiki/United_States_Digital_Service)---it didn't qualify as a department by any line of reasoning, and had no interest in government efficiency.  Likewise, you don't need to go too far to find fired government workers talking about how they *totally* support the theoretical mission of making government more efficient, but don't think this gets to that goal.

However, consider what the Muskovites have done in practice.  They have gutted the agencies tasked with overseeing or otherwise reining in Tesla, SpaceX, {% x %}, and other Musk-owned ventures.  They have exfiltrated databases from the government, including data about cases against Musk's companies and his rivals.  And they have made routine administration more difficult, while selling off assets, but enabling more surveillance.  The Senate actually [released a full report](https://www.warren.senate.gov/imo/media/doc/130_days_of_elon_musk_report.pdf) on the topic, so don't take my word for it.

Do we want to believe that they really have no idea how to make organizations more efficient, or can we accept that they mean making their oligarchy more efficient by not having the pesky democratic government in their way?  When they talk about "fraud, waste, and abuse," might they mean things that they personally wouldn't spend money on, rather than some imagined universal or standardized idea of those words?  I contend that they made the government more efficient, but not in the ways that we'd like it to become; it has become more efficient in helping them.

Remember, nobody has "efficiency" as a goal, unless they explain efficiency in what context.  In fact, the conversation reminds me of a fairly standard trope that I talked about in the post about **Star Trek**'s famous [*Patterns of Force*]({% post_url 2020-12-31-force %}) episode.  Or, rather, it reminds me of the conversations that led to parts of that episode, and I happen to have my discussion of it to gesture at.  You know what I mean...

> **KIRK**: But why Nazi Germany? You studied history. You knew what the Nazis were.
>
> **GILL**: Most efficient state Earth ever knew.

I discussed there that we've always had this bizarre myth that only fascists get things done, because they don't spend time deliberating[^3].  The Nazis especially benefited from this idea, technically even before they existed, with fiction writers fearing the hyperefficient "war machine" that the Germans *would* build, and according to them, we really only needed to see what countries would sign up to work with and against them.

[^3]:  Why do you think that, in the United States, we still have the insipid myth of "spineless Democrats," repeated so often and so loudly that it [hides the actions that they take {% cc %}](https://www.emptywheel.net/2025/06/06/lefty-pundits-continue-to-drown-out-democratic-actions-with-their-complaints-about-democratic-inaction/) on our behalf?  It spins right out of the idea, embedded everywhere from our companies to our right-wing movements, that you can't get anything done through cooperation or caring about people, literally all evidence to the contrary.

In reality, though, only about twelve percent of the German military counted as "mechanized," with a lot of their troops slogging through mud on foot or *maybe* the occasional horse-drawn cart.  Of the mechanized forces, Porsche designed an overly complicated gearbox for the famous [Tiger](https://en.wikipedia.org/wiki/Tiger_I) tanks, meaning that they spent a lot of time not working, especially when faced with dangerous obstacles like...mud.  The Nazi invasion of the Soviet Union happened, not because of some genius strategy, but because Germany had pretty much run out of all resources, especially food, and the Russians had the least-protected border...for reasons that became clear as the invasion continued.  Internally, the leaders couldn't wait to stab each other in the back by any means available, and bunches of them had drug problems.

No, please, tell me again about the raw efficiency of fascists, the sorts of regimes now often outlived rather significantly by pet rabbits...

They murdered people with efficiency, sure, working them to death to stretch those limited resources as far as possible.  But they didn't do a great job on anything *useful*, unless you judge entirely on hatred, which I realize that many people do.

## Beyond Efficiency

This reasoning applies to most words in the discourse, too.

### Overreach, and Similar

Consider the [militia movement](https://en.wikipedia.org/wiki/American_militia_movement) in the United States.  For decades, they've talked a big game about how they want to prepare themselves for when some hypothetical presidential administration begins shutting down dissent and deploying troops in the streets.  They often use words like "overreach."

And yet, in the past few months, have they had other things to do?  Did they start watching archives of daytime soap operas?  I ask, because in addition to the "efficiency" issues above, the current administration has done the following.

- Fired bureaucrats and other governmental leaders to [replace them with personal loyalists](https://theconversation.com/what-happens-when-leaders-have-loyalists-in-charge-of-men-with-guns-lessons-for-the-us-from-nicaragua-syria-and-other-authoritarian-countries-250579).
- Used the full force of the government to [silence critics](https://theconversation.com/donald-trumps-chilling-effect-on-free-speech-and-dissent-is-threatening-us-democracy-253139), including [Musk himself](https://cepr.net/publications/elon-musk-could-apologize-to-donald-trump-but-not-to-the-american-people-inside-the-maga-mind/), who has tried to retract some of what he said during their whiny online slap-fight.
- Used masked, unidentified forces to [abduct individuals](https://americandragnet.org/) with no due process, exiling some of them to a [foreign prison](https://en.wikipedia.org/wiki/Terrorism_Confinement_Center).
- Deployed the [military on United States soil](https://theconversation.com/trump-orders-marines-to-los-angeles-as-protests-escalate-over-immigration-raids-demonstrating-the-presidents-power-to-deploy-troops-on-us-soil-258527), for use against American citizens.  Along the way, he has [decried the protests against ICE](https://rollcall.com/factbase/trump/transcript/donald-trump-speech-250th-anniversary-army-fort-liberty-north-carolina-june-10-2025/) as "animals," not "from our country or from people that love our country," and so forth.

I could probably go on, if we reach back more than a couple of weeks, and that doesn't even get into whatever went down [yesterday](https://en.wikipedia.org/wiki/No_Kings_protests) that I haven't caught up on, but you get the point.  To us, this seems fairly overreach-y.  But when they talk about invading American cities or trampling on civil rights, they meant it looking more like [enforcing desegregation](https://www.eisenhowerlibrary.gov/research/online-documents/civil-rights-little-rock-school-integration-crisis) or the ATF [seizing stockpiles of illegal weapons](https://theconversation.com/waco-the-siege-25-years-on-94324), not militarizing border control or silencing critics.  That, they have no problem seeing on television, especially if it happens to "coastal elites."

### Politics

Likewise, think about how different people use the word "political."

For some of us, we can't escape politics, because people's values pervade everything around us.  I've pointed out before that [art and technology always embody politics]({% post_url 2020-10-18-stories %}), and you can either choose those politics or let society pick them through your implicit choices.  In that post, I talk about how a park bench tells you who gets to rest, why they get to rest, and how long they may rest.  If you fear a homeless population bringing down property values---instead of, you know, *housing them*---then you create uncomfortable benches where you can only sit upright, and never with anything like privacy.  But if you care about (for example) parents with children or younger couples, then you make entirely different decisions.  You can try to avoid the decision by doing what the neighboring community did with their benches, or picking whatever the bench manufacturers (a real thing?) tell you has sold best in recent years, but in that case, you've only outsourced your politics to somebody who doesn't care about you or the people who you worry about.

I like to use benches as the primary example, because we can probably all enumerate every possible decision involved in the overall choice.  But the same holds true for art.  Every character, every relationship, every image says something about values, either directly, or "laundering" those values through the artist's negligence.

And I land here, because many people don't or won't see it.

For example, if a television show includes a Japanese character, a transgender character, and a few women, we can all see the politics of that, asserting that the world includes this variety, and so should our media.  If you cast only white men, which *still* makes a political statement, though, arguably a much louder statement than alternatives, but many people will deny it having any political statement.  Their eyes see white, male, and cisgender as a "default state," and defaults couldn't possibly say anything political.  Except that this gets to exactly what I said above about "outsourcing" your values.  Defaults don't mean that the work made no choice.  Defaults mean that the artist didn't take an active role in those choices[^4].

[^4]:  I stand guilty of making that mistake as much as anybody else.  At some point, I should write a post digging into the many failures along these exact lines, where I accepted some trope or other uncritically, and in doing so directly undermined the book's intended political statements.

Likewise, I've said many times, over the years, that for a certain segment of the population, only two types of social progress exist.  If it completed[^5] before they became socially aware, then it had good and just goals, and they used whatever means they used for good reason.  If it hasn't completed, then only horrible, violent, and ugly people care about the goal, and they believe that society must stomp it out, because it has "gone too far" by asking us to treat "those people" like humans.

[^5]:  No fight for social progress ever completes, but roll with it for the sake of things.  In reality, we can and should always do more, and opponents will wait decades and even centuries to claw back changes.  If we, as a culture, had kept that in mind over the past three hundred years and stopped patting ourselves on the back with end-of-history stories, and if we had treated dystopian fiction as serious warnings about goings-on *at the time*, rather than fanciful predictions of some far-flung future, then we wouldn't have this mess of the past decade or so.  I dislike the framing of "waves" of feminism, among other reasons, because it suggests that suffragettes (for example) got the right to vote and immediately packed up their things to happily go back to lives where they couldn't own property or earn a living.

Related, we have [identity politics](https://en.wikipedia.org/wiki/Identity_politics).  When people advocate on behalf of a group that they identify with, the *acceptance* of that group tends to define whether it qualifies as identity, and so a problem.  Among authoritarians, everything falls into the category of identity politics *except* for advocating for the majority ethnicity/religion/sexuality combination or the wealthy.  For socialists, everything looks like identity politics except for socioeconomic class.

However, for a Black transgender Muslim with a mobility handicap, what may look like identity politics to you looks suspiciously like urging you to stop treating them like a strange edge-case to worry about after we fix everything for the "normal" people.  For them, it looks like the only path to survival, since waiting for us to get everything else fixed doesn't solve any of their problems.  And at the extremes, even their *showing up* makes an uncomfortable political statement, a reminder that not everybody lives the same life.

In fact, I probably should've started the section there, because comfort has a lot to do with the casual definition of politics, here.  For a lot of people, it only becomes political if it reminds them of something uncomfortable, such as systemic racism, gender dysphoria, unhoused populations, persecution, starvation, labor abuses, or any of the many other things that I don't have the time to cram into this sentence.  If it shocks people out of complacency, *that* makes it "political" to them.

### Civility

Closely related, consider the right-wing obsession with so-called "civility."  If you dare to [characterize their actions/words in anything but the most flattering light {% cc %}](https://www.theindex.media/theres-no-civility-clause-for-fascists/), then they want you fired for violating their ideas of politesse.  But as mentioned, they see it as perfectly civil for *them* to call people "animals" or to threaten violence against protests, whether [authoritarian {% cc %}](https://www.nbcnews.com/politics/white-house/trump-warns-military-parade-protesters-will-face-heavy-force-rcna212136) or [extrajudicial {% cc %}](https://www.nbcmiami.com/news/local/desantis-says-in-podcast-florida-drivers-can-hit-protesters-to-flee-for-your-safety/3637117/).

They can call for [deploying nuclear weapons against civilians](https://israelpalestinenews.org/republican-lawmaker-supports-using-nuke-on-gaza/) or otherwise[^6] suggesting [extermination of a group {% cc %}](https://www.theguardian.com/us-news/2023/nov/10/florida-republican-michelle-salzman-palestine) and remain "civil."  They can [invite antisemitic weirdos to dinner](https://en.wikipedia.org/wiki/Nick_Fuentes#Dinner_with_Donald_Trump_at_Mar-a-Lago) and remain "civil."  But criticize a government for (at least) committing war crimes, and congratulations, you fail at civility and become [antisemitic](https://www.whitehouse.gov/fact-sheets/2025/01/fact-sheet-president-donald-j-trump-takes-forceful-and-unprecedented-steps-to-combat-anti-semitism), even the Jewish and/or Israeli folks making that same criticism, maybe especially them.

[^6]:  I use Gaza as an example, here, due to Trump using it as a wedge, but I understand the "both sides-ness" of this topic.  Mass kidnapping made a bad situation worse, and mimicking the War on Terror to---in essence---take revenge has made things far worse, exactly as the War on Terror did.  Acknowledging that tempers run high on both sides of the issue, I understand that Israelis feel unsafe, and I also understand that more violence absolutely has not made them safer, and it certainly hasn't made the targets of the violence safer.

You can see them play a similar game with freedom of expression.  They will talk [endlessly about the right to free speech](https://www.whitehouse.gov/presidential-actions/2025/01/restoring-freedom-of-speech-and-ending-federal-censorship/), even while they work to [silence their critics](https://theconversation.com/trumps-aggressive-actions-against-free-speech-speak-a-lot-louder-than-his-words-defending-it-252706).  We can wag a finger at the hypocrisy, but they don't classify criticism of their ideas, words, and actions, as legitimate speech, so they see no reason to protect it.  Speech only matters if it supports them.

You can talk about the alleged hate in people's hearts if they want to stop an occupation and bombing of a civilian population, but they'll punish anybody who characterizes ethnic cleansing or police violence as hateful.  They'll defend your right to call for [violence against judges who enforce the rule of law {% cc %}](https://www.theguardian.com/us-news/2025/may/17/trump-judges-courts-threats), or your right to [take part in a violent insurrection](https://en.wikipedia.org/wiki/Pardon_of_January_6_United_States_Capitol_attack_defendants) on their behalf, but if you talk about institutional racism in the United States, then they want to purge your [improper ideology](https://www.whitehouse.gov/presidential-actions/2025/03/restoring-truth-and-sanity-to-american-history) from the public arena.

Their [marketplace of ideas](https://en.wikipedia.org/wiki/Marketplace_of_ideas) has fairly strict regulations, when it comes to expressing modern science, political theory, and economic fact.  Speaking of which, let's skip over to one of those fields.

### Science

I'll keep this quick, because you see this same conflict of definition across the sciences, a sampling maybe including the following.

- [Trust the science {% cc %}](https://www.theguardian.com/world/2021/feb/25/marjorie-taylor-greene-transgender-sign)
- [Do your own research](https://pubmed.ncbi.nlm.nih.gov/36032354/)
- [Reproducibility](https://theconversation.com/how-trumps-gold-standard-politicizes-federal-science-258277)

In all these cases, they present phrases that *sound* like they mean to support the process of incrementally improving our understanding of ideas based on experimentation and feeding results of experiments back into new experiments, but they define and employ the ideas to allow them to justify whatever conclusions that they happen to want.

### Law

One last item, here.

The political right *loves* to talk about [law and order](https://en.wiktionary.org/wiki/law_and_order).  And they'll use that phrase as a pretext to *violate* the law in their pursuit of some real or perceived crime.

Everybody treats this as a shock, because they misread "law and order" as the [rule of law](https://en.wiktionary.org/wiki/rule_of_law).  Let's compare the two.

> **law and order** (2) The strict enforcement of law, statutes, and social conventions.
>
> **rule of law** (1) The doctrine that no individual is above the law and that everyone must answer to it.

They see law as including the social order, including [systemic racism](https://en.wikipedia.org/wiki/Institutional_racism).  In fact, they often prioritize it over the other aspects of law, explaining why they don't mind if occasional individuals set themselves above the law, provided that individual comes from a privileged background and uses their power against somebody who does not.

Similarly, *patriotism* could have made another viable section of its own, too, but I'll cram it in here.  One side seeing a hatred of the country's people, governments, traditions, laws, and culture as somehow more patriotic than criticizing bad policy, what I like to call "real estate fan fiction," since I don't know what else makes a country that you could love it.  Even not showing "proper respect" to the symbols of the country, they call hatred, even as they disregard the actual, written standards of respect to wear flag-themed shorts.

In fact, while the local "No Kings" protest yesterday focused far too much on a single person---"Donald Trump has got to go" may have emotional resonance, but the hundred and fifty years of contrived grievance that got him into office and the damage that he has done won't vanish, once he has slunk back into a hole, somewhere, now that he has staffed everything with loyalists---but they did occasionally go for "USA" chants, a reminder that *we* care about the country, enough to fight against what they've started doing to it.  If you don't mind dismantling democracy, refusing to welcome strangers (except for white South Africans), a military parade through the streets, eradicating the social safety net, and so forth, then that makes *you* the problem.

## Learning the Lingo

We could go on pretty much forever, if we wanted to, because this never ends, but I focused on the United States and mostly the last few months.  How many people spent decades calling every government "fascist," so that they could turn around starting in 2017 to tell you that the word doesn't have any real meaning?  Or maybe they tried to haggle over the definition of [ethnic cleansing](https://en.wikipedia.org/wiki/Persecution_of_Uyghurs_in_China) or [concentration camps](https://web.archive.org/web/20191015183608/https://www.commondreams.org/news/2019/10/14/doctors-demand-trump-close-inherently-immoral-immigrant-detention-centers-ahead-mass), because surely what happens today couldn't qualify.  We could look at how many people cheered on [Russia's invasion of Ukraine](https://en.wikipedia.org/wiki/Russian_invasion_of_Ukraine) as a blow to imperialism.  Or we could talk about "protecting" this group or another that has only seen invigorated competition rather than attacks, the "dignity" in work, or any number of other things.  We could also try to talk about the shell game needed to keep making sure that implicit biases don't skew recruitment at schools and companies, by changing the term for the practice from affirmative action, to equal opportunity, to diversity, to diversity/equity/inclusion/accessibility, to whatever we'll call it once Trump gets run out of office again.  Even slogans like [Make America Great Again](https://en.wikipedia.org/wiki/Make_America_Great_Again) require *you* to figure out what it means by "great," promising you everything by promising everybody nothing in particular and delivering it.  And never forget about [states' rights](https://en.wikipedia.org/wiki/States%27_rights), which somehow need to exist for the purposes of discrimination, but not for the purposes of protecting anybody.

And if this applies in computer science and politics, you know that this applies in the corporate world, which we often build entirely on euphemisms.  People talk about fire drills, meaning either emergencies to deal with quickly or artificial emergencies to test employees.  Steep learning curves might mean something that you learn quickly or that takes significant effort to learn.  Someone off in the weeds might have started doing unnecessary work or gotten bogged down by their duties.

We get into a shocking amount of trouble, I think, by signing onto ideas because of what we would mean by them, rather than asking what they actually intend.

And with that, I hope that everybody stayed safe, yesterday.

* * *

**Credits**:  The header image is [Nevius & Haviland 'Efficient' spring shad rollers - a pointer - when hunting for shade rollers buy the 'efficient'](https://www.flickr.com/photos/24029425@N06/9404714466) by the [Boston Public Library](https://www.flickr.com/photos/boston_public_library/), made available under the terms of the [Creative Commons Attribution 2.0](https://creativecommons.org/licenses/by/2.0/deed.en) license, with the underlying in the public domain as a 1893 work whose copyright has absolutely expired.
