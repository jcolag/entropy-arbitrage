---
layout: post
title: SlackBackup
date: 2019-12-22 7:01:12-0500
categories: project
tags: [slack, electron, javascript, programming, technology, project, announcement]
summary: "I announce an older project of mine that some people use"
thumbnail: /blog/assets/slackbackup1.png
---

* Ignore for ToC
{:toc}

![Sentiment Analysis](/blog/assets/slackbackup1.png "Sentiment Analysis")

A job and a couple of social groups have more or less standardized on Slack for internal communications.  One of the biggest problems with using Slack, for those who haven't had the experience, is the pricing scheme, which effectively holds your team's conversations for ransom by hiding older content and displaying banners announcing that the conversation is behind a paywall.  If a "team" is actually multiple Slack teams with different legal requirements, the cost can be extraordinarily high.

That's Slack's prerogative, of course.  But, since they also offer an API with (currently) no usage restrictions except for rate limits, it's _my_ prerogative to download my history, and I'm not fond of business models that are closely related to extortion, obtaining something of value from someone through threat of (in this case) a lack of access to your own conversations.

_SlackBackup_ is an example of a project spiraling out of control in a satisfying way.  It started life as a short script to just pull specific information.  Then it became a script with a configuration file.  Then the script added the ability to delete older files.  That became an Electron app to easily modify the configuration file.  And then *that* became a program that will also search the archive and show visualizations of my conversations.  Most of that happened over a weekend...

![Main Page](/blog/assets/slackbackup2.png "Configuration")

It's not perfect, but it appears to work reliably (at least, until Slack inevitably kills its token-based API) and it's easy enough to provide new builds.

## Get It

Should you need something like this, you can download the latest build (v1.2) [from GitHub](https://github.com/jcolag/SlackBackup/releases), though it may be a *bit* behind code changes.

If you're more technical (you can download a repository and use the command line), [the repository](https://github.com/jcolag/SlackBackup) has straightforward instructions for you, which will keep you at the latest and greatest.

## The Technology

I won't bother going into too much detail as to how it all works (because interested people can dig through the repository and ask questions), but I'd like to give a quick overview of the major technologies involved.

The core of the user interface is the [Electron/React Boilerplate](https://github.com/electron-react-boilerplate/electron-react-boilerplate), which combines [Electron](https://electronjs.org/), [React.js](https://reactjs.org/), [Redux](https://redux.js.org/), [React Router](https://reacttraining.com/react-router/), [Webpack](https://webpack.js.org/), and the [React Hot-Loader](https://gaearon.github.io/react-hot-loader/) in a single package.  Redux struck me as too top-heavy for the minimal data flow needs of the application, so I chose to work with [Reflux](https://github.com/reflux/refluxjs), instead, so you'll see some remnants of the original boilerplate Redux code that I still haven't completely extracted.

The core of what the program does leverages Slack's deprecated-but-still-usable [token-based API](https://api.slack.com/web) with a simple HTTP library making the requests.

The interface styling is handled via [Bootswatch](https://bootswatch.com/), providing more than twenty decent styles I can easily swap out.  Some [Font Awesome](https://fontawesome.com/) symbols are also used and the [Moment](https://momentjs.com/) library is used for formatting times.  [D3](https://d3js.org/) is used for all the data visualizations.

Those visualizations rely on an implementation of the [Flesch index](https://github.com/words/flesch), [sentiment analysis](https://github.com/thisandagain/sentiment), and a [Porter stemmer](https://github.com/words/stemmer).  Note that all analysis and visualization is focused on your user in each Slack team, to avoid any privacy concerns.

I also started integrating [Project Fluent](https://projectfluent.org/) for localization purposes, but haven't gotten far enough for that to make a difference.
