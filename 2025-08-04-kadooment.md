---
layout: post
title: Developer Diary, Kadooment
date: 2025-08-04 08:36:05-0400
categories:
tags: [programming, project, dev-journal]
summary: Progress on assorted projects
thumbnail: /blog/assets/2821350680_dbdbb4a17e_c.png
offset: -30%
description: This week's projects include the likely end-for-now of computer woes, the blog's code, and my Notoboto note-taking application.
spell: Kadooment stenotype Typey Codidact Notoboto Radicale Inf fpm fastcgi_params fastcgi_pass unix fastcgi_index fastcgi_script_name conf favorited Cryptpad Forgejo YaCy gPodder dateFormat jison isadded endmermaid minifier cson stringify
proofed: true
---

* Ignore for ToC
{:toc}

Today, Barbados celebrates Kadooment, which marks the end of the [Crop Over](https://en.wikipedia.org/wiki/Crop_Over) harvest festival.  And honestly, long-time readers probably know that August has so few holidays of interest that I probably would have gone with this on the name alone, but it also has the virtue of reminding us that we have started heading towards winter.

![A Kadooment parade](/blog/assets/2821350680_dbdbb4a17e_c.png "It sounds festive, but drop the final syllable, and you get a wacky cartoon super-villain")

And on to the week's projects.

## Argh, Part 7

Things continue to shape up, I think, so much so that I can probably start retiring the **Argh** "bit" in the posts, soon.

### Resettlement, Part 4

I have now fully landed on the "new" laptop, and have used it for most of the past week. {% emoji party popper %}

As mentioned, transferring the `~/.local/share` folder from the dead machine has saved me a lot of the effort of remembering what applications I need installed, and I could arguably remove a bunch without caring much.  I find myself stumbling on the occasional utility that a script needs, but not much more than that.

Therefore, I'll say the following for now, as sort of the I-hope-final installment to this story for at least a long time.

- The servers remain in...well, service.  I could certainly go back to using Thunderbird and other applications, but I might like the in-house web-apps (Snappy Mail and Radicale/Inf Cloud) better, even though I *do* like Thunderbird.  More on the servers later.
- The horrifyingly old laptop *also* remains in service as the keeper of my overnight script letting me quickly take notes if I wake up in the middle of the night.  Some quick `git` magic on both machines streamlines everything nicely.  This saves me from carrying a laptop to and from my bedroom every day, which will probably save wear-and-tear on the plugs, an issue that has probably wiped out more laptops of mine than any other problem.  I could probably also run (slightly) bigger services on it than I can on the Raspberry Pi units, if I wanted, as well.
- Eight gigabytes of RAM---what I bought for something like ten bucks earlier in this process---mostly suffices for normal tasks, but I'll want to splurge and upgrade that, at some point, because the machine *does* slow to a crawl, if I ask it to do anything significant.
- Because I already had access to the neglected refurbished Framework chassis and could scavenge a Wi-Fi card and hard drive, I believe that this move only cost me twenty-five bucks out-of-pocket, ten for the memory and another fifteen for the NVMe-to-USB adapter to recover my data.  And given that I have a couple of other NVMe hard drives around, the latter gadget may become a semi-permanent external storage device for one of the servers.  I'd consider that a success, even if it took me more than a month and a half.

If anybody wants that sort of thing, I'll save my impressions of the Framework machine for the August newsletter, after I have had a couple more weeks to fiddle with it, and so this doesn't accidentally endorse a proprietary product.  Plus, when I got the System 76 machine, *it* seemed fairly solid at first, too, even if it (apparently correctly) felt a bit fragile for its size.

Oh, one note unrelated to the hardware:  Expect a [tech tips](/blog/tag/tech-tips) post on managing SSH keys soon, because it took me *far* too much time to diagnose and fix that problem...

### Mini-Server, Part 5

I tried to install a couple of new services---[**Beehive**](https://github.com/muesli/beehive) and [**Jupyter Lab**](https://github.com/jupyterlab/jupyterlab/), most prominently---but didn't get anywhere with them.  The former wouldn't serve up a working page for whatever reason, and it looks like the project ran out of steam soon after announcing a big rewrite.  The latter started sending me down a dark road[^1], so I backed away quickly.

[^1]:  Specifically, it felt like a trip deep into Python's inane reproduction of [DLL Hell](https://en.wikipedia.org/wiki/DLL_hell), and I have to say that "nobody should install Python applications using default Python tools, so you should create virtual environments so that every Python script has its own little universe" feels like an admission of complete failure.  I wonder if this change in direction has humbled the Python evangelists any, where they used to swarm out of the woodwork to tell you about no better language existing...

#### Feed Reader

For a moment, I didn't think that I'd have anything interesting to present, this week, but then I realized that I still had [RSS Guard](https://github.com/martinrotter/rssguard) kicking around on the laptop.  And while I don't have a serious problem with it, I never got accustomed to its insistence on not allowing filtering by article tags, so it seemed time for a new RSS feed reader.  My requirements---a user interface (surprisingly not universal), an API, lightweight and few dependencies to survive on an old single-board computer, and so forth---limited the options, but Fresh RSS seems to check every box.

Installation went well enough, though actually coercing NGINX into serving it took a bit of extra effort, which...I'll present here, in case anybody else needs it.

```nginx
server {
    listen 80;
    server_name server.local;
    location ~ ^/rss/.*\.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_param PATH_INFO $fastcgi_path_info;
    }
    location /rss/ {
        alias /var/www/FreshRSS/p/;
        index index.php index.html;
        try_files $uri $uri/ /rss/index.php?$args;
        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/run/php/php8.2-fpm.sock;
            fastcgi_param SCRIPT_FILENAME $request_filename;
        }
    }
}
```

Oh, and I needed to install `php8.2-fpm`, as the PHP-fluent among you might have guessed by its mention on the sixth line.  Regardless, it'll take some time to grow accustomed to the slightly weird user interface, and I'll need to create yet another script to grab the "favorited" articles for the newsletter, but once I slog through the thousands of articles that it scarfed up, I should settle in nicely.

#### Services Running

For the "final" tally, since I alluded to this earlier, the two servers run the following.

- [Code Server](https://github.com/coder/code-server), a full version of Visual Studio Code, but as a web page.
- [Cryptpad](https://cryptpad.org/), the full office suite.
- [Forgejo](https://forgejo.org/), git hosting.
- [Fresh RSS](https://freshrss.org/), the aforementioned RSS feed reader.
- [Inf Cloud](https://inf-it.com/open-source/clients/infcloud/), a user interface for calendar and contacts, in this case pulling the data from Radicale, below.
- [Jellyfin](https://jellyfin.org/), the media server.
- [Own Tracks](https://owntracks.org/), location-mapping software.
- [Radicale](https://radicale.org/v3.html), the server storing calendars and contacts.
- [Snappy Mail](https://snappymail.eu/), an IMAP e-mail client.
- [YaCy](https://yacy.net/), a peer-to-peer search engine.

Between those and continuing judicious backups that got me back up and running this time through, this should make it possible to keep working, even if I need to do something upsetting like use an old tablet as the "computer."  The only real gap comes from the blog, where I need to rebuild that environment every time I change computers[^2].

[^2]:  I should note that I nearly tried moving my local version of the blog to one of the servers.  Doing that would give me the flexibility to consistently update and publish posts from anywhere.  I would, however, need a decent editor and control mechanism, and it looks like if I want a multi-document interface, syntax highlighting, and access to real files---to say nothing of running local scripts---I'll probably need to build it myself.  That delays that project indefinitely...

What do I have running on the laptop, then?

- [Authenticator](https://apps.gnome.org/Authenticator/)
- [Beeper](https://www.beeper.com/)
- [Firefox](https://www.firefox.com/en-US/), with a bunch of pinned tabs including some from the above list, some external messaging, and some for checking status...
- [gPodder](https://gpodder.github.io/)
- [Notoboto](https://github.com/jcolag/Notoboto), because if I didn't want to use it, I wouldn't have written it...
- [Plover](https://www.openstenoproject.org/plover/)

At least full-time.  I could probably move the authenticator codes to a web app such as [2FAuth](https://2fauth.app/), and may do that as a backup plan, but the desktop app works fine.

Anyway, maybe the Mini-Server updates will continue to appear when something interesting comes up, since I do enjoy highlighting worthwhile projects that I end up using.  We'll see.

Meanwhile, I also dug out an adapter for the USB power line on the Raspberry Pi with a power button on it, making recovery from the usual crashes on one machine less annoying.  Best that I can figure, Jellyfin probably wants more memory for certain tasks.

## Entropy Arbitrage

{% github jcolag/entropy-arbitrage-code %}

Sunday before last, I wrote up a post about how, given the resources, I would try to solve the [payment processors going after adult content]({% post_url 2025-07-27-payment-processor %}) by building a payment-processing layer. And to clarify it, I decided to use diagrams like this, generated by [Mermaid](https://mermaid.js.org/).

{% mermaid %}
gantt
  dateFormat  YYYY-MM-DD
  title       Adding Gantt diagram functionality to mermaid
  excludes    weekends

  section A section
  Completed task            :done,    des1, 2014-01-06,2014-01-08
  Active task               :active,  des2, 2014-01-09, 3d
  Future task               :         des3, after des2, 5d
  Future task2              :         des4, after des3, 5d

  section Critical tasks
  Completed task in the critical line :crit, done, 2014-01-06,24h
  Implement parser and jison          :crit, done, after des1, 2d
  Create tests for parser             :crit, active, 3d
  Future task in critical line        :crit, 5d
  Create tests for renderer           :2d
  Add to mermaid                      :until isadded
  Functionality added                 :milestone, isadded, 2014-01-25, 0d

  section Documentation
  Describe Gantt syntax               :active, a1, after des1, 3d
  Add Gantt diagram to demo page      :after a1  , 20h
  Add another diagram to demo page    :doc1, after a1  , 48h

  section Last section
  Describe Gantt syntax               :after doc1, 3d
  Add Gantt diagram to demo page      :20h
  Add another diagram to demo page    :48h
{% endmermaid %}

It worked perfectly on my version of the blog, but as some of you noted---and thanks for catching it, to those I didn't say that to earlier---went wildly wrong when I deployed to the site. Turned out that, all this time, despite the problems that the blog had a few months back with excessive spacing dragging down load-times, it had a [minifier](https://en.wikipedia.org/wiki/Minification_%28programming%29) running, which fouled up the diagram source.

For example, I input the above diagram as something like this.

```
gantt
  dateFormat  YYYY-MM-DD
  title       Adding Gantt diagram functionality to mermaid
```

...and so forth.  I stole the contents from Mermaid's big [Gantt example](https://mermaid.js.org/syntax/gantt.html), made available under the terms of the [MIT license](https://github.com/mermaid-js/mermaid?tab=MIT-1-ov-file#readme), if you actually want to read along.  Anyway, that code goes into the post completely normally, and then some JavaScript turns it into a real vector diagram---sorry RSS folks, you don't see that part---that normal people can look at without their eyes immediately glazing over.  However, Mermaid holds to that format *exactly*, including new lines and other spacing, meaning that the "minifier," which only ran on a *production* build, trashed the diagrams.

Upshot, somebody (me {% emoji hello %}) wished the minifier into the corn-field, because individual bytes don't really matter much, these days, with packet sizes incredibly large.

Along the way, the scripts got updated for newer tools, and the "rock on" sign {% emoji rock on %} got a readable name for use in Saturday's post about [**Let It Come From Whom It May**]({% post_url 2025-08-02-let-come %}).

## Notoboto

{% github jcolag/Notoboto %}

As mentioned last time, the code needed some quick cleanup, here.

Most importantly, the old code to remove the diacritical marks through Unicode decomposition has gone away.  Again, the process still works extremely well for what it did, but the table-based transliteration accomplishes the same goal *without* stomping on non-Latin writing systems.

Less important, but feeling more friendly, the library files have scurried away into a `lib` sub-folder to avoid clutter, exactly like the assorted image files have their own folder.

And now that we all get the idea of these libraries, the CSON code now also sits in a library, in case anyone ever needs the thing for another project. Call it with `::cson::parse $string` or `::cson::stringify $dict`.

## Next

I don't really know.  Expect some clean-up to continue, and as a result of this week's work on **Notoboto**, part of me wants to increase that code's modularity, so that I don't need to constantly sift through hundreds of lines to find what I need.  And I still need to take stock of the projects that I had in maybe-interesting states before the old laptop bought the farm.  I'll probably come up with something...

* * *

**Credits**:  The header image is [Kadooment Festival](https://www.flickr.com/photos/44764399@N00/2821350680) by [alfback2003](https://www.flickr.com/photos/alfback/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) license.
