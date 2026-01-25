---
layout: post
title: Developer Journal, Day of the Disappeared
date: 2021-08-30 07:00:31-0400
categories:
tags: [programming, project, devjournal]
labels: [blog, fylakas-onomaton, library-update, ruby]
summary: Progress on assorted projects
thumbnail: /blog/assets/Bandera-de-los-Desaparecidos-Dia-de-la-Memoria.png
offset: -31%
---

* Ignore for ToC
{:toc}

Today marks the [International Day of the Disappeared](https://en.wikipedia.org/wiki/International_Day_of_the_Disappeared), drawing attention to people missing due to secret imprisonment.

![Remembering the disappeared in Argentina](/blog/assets/Bandera-de-los-Desaparecidos-Dia-de-la-Memoria.png "Remembering the disappeared in Argentina")

As the calculus of accepting refugees returns to the public discourse, keep in mind that you probably know people who have been affected by this sort of violence, whether it happened in your country, or they arrived in your country seeking asylum from it.

In any case...here's some talk about code.

## Library Updates

On a day when I wasn't able to put in any real work, I let GitHub automatically merge an update for [**Uxuyu**](https://github.com/jcolag/Uxuyu) and [**Bicker**](https://github.com/jcolag/Bicker).

## Fýlakas Onomáton

The big goal for this week was getting [**Fýlakas Onomáton**](https://github.com/jcolag/fylakas-onomaton) to deploy on Heroku.

### Ruby Versioning

The first part of this was finding a version of Ruby that...

 * The system would allow me to upgrade (or downgrade, if need be) to, and
 * Matched something that Heroku supports.

Unfortunately, this hits one of the unfortunate snags with working with Ruby:  Different installation methods are stuck on different versions, and they all conflict and are used in different ways, because they all expect to be the only instance.  My default Ubuntu bundler conflicted with my [RVM](https://rvm.io/) installations of Ruby and vice versa, so the versions all declared code to be broken.  And it's non-trivial to vacuum out all the bits of the former so that at least RVM will actually work as expected.  And even then, it's not always a global solution, if something still "remembers" an old version.

I settled on Ruby v3.0, since it's now considered the stable version, but that obviously required other upgrades.  To be fair, though, Ruby's development team has made upgrades much more sensible than they once were.

### Database Issues

Also, getting it ready for deployment in production meant setting everything up to serve the compiled assets and making sure that [SQLite](https://sqlite.org/index.html) isn't even *referenced* in the project.

Migrations also aren't run when deploying, which feels like a peculiar stance to take.  That raised an issue that one of the existing migrations was incorrect.  I previously had the following, to add a foreign key referencing the user table to the activations.

```ruby
add_reference :activations, :user, foreign_key: true
```

The `foreign_key` clause is not only unnecessary, but it causes some deployments---like whatever Heroku is using---to try to create the foreign key *twice*, causing an error.  Unfortunately, this means that anybody who might be playing with this at home will have a retroactive breaking change.  I don't see that being a large community, however...

### Real Work

You'll also see improved styling on the tables and at least stubs of static pages.

Anyway, long story short---too late, I know---you can check out the server running at <http://onomaton.club/>.  I wouldn't register an account just yet, since I still need to read up on how to manage SSL certificates, here.  I'm *not* paying Heroku twenty dollars for the SSL service, since that's far more than the VPS that this project would need, and the point of using them was to keep this cheap, but it looks like there's a way to manage the certificate through AWS.  That might be ugly, but again, the expected revenue for this project is a couple of dollars from people buying the app, so I have no interest in spending any more money on it than is strictly necessary...

## Entropy Arbitrage

In trying to get **Fýlakas Onomáton** deployed on Heroku, as mentioned above, I needed to mess around with the Ruby configuration, moving to RVM.  Unfortunately, the aforementioned incompatibilities struck, leaving it impossible to run any of the Jekyll code.  That meant that I couldn't test any changes or publish a new post.

Fortunately, after finally clearing up all the ambiguities that I could find, and then upgrading all the packages, everything managed to get back on track.  And as a bonus, the blog now runs using Jekyll version 4, which has some new conveniences that I should explore soon.

## Next

Now that **Fýlakas Onomáton** is squared away, I want to circle back to **Doritís Onomáton** to add a semi-critical feature that I forgot about:  When requesting an activation code, the app should supply device information.  Without information about the device, there's no reasonable way for a user to determine when to revoke an API key.  *Then* I start looking at how to submit the app.

Full disclosure, though, I seriously never expected *this*---a silly little app to generate random nonsensical names---to be the project that spiraled out of control.  What started out as a quick experiment to see if Flutter was worth working with has now affected every Rails project I'm working on, pushed me to use Heroku for the first time, *and* now I'm reading about AWS.  Similarly, the "I'll just throw together a server" project has been taking up time for *four months*, on Saturday.

* * *

**Credits**:  The header image is [Bandera de los Desaparecidos — Día de la Memoria](https://commons.wikimedia.org/wiki/File:Bandera_de_los_Desaparecidos_-_D%C3%ADa_de_la_Memoria.jpg) by [Banfield](https://commons.wikimedia.org/wiki/User:Banfield), made available under the terms of the [Creative Commons Attribution Share-Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.
