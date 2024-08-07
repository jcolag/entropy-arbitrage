---
layout: post
title: Project Updates, Harriet Tubman Day
date: 2020-03-09 07:03:32-0400
categories:
tags: [programming, project, devjournal, css, jekyll]
summary: Progress on the blog and a new (small) project
thumbnail: /blog/assets/NMAAHC-2017_30_48_001.png
offset: -17%
---

* Ignore for ToC
{:toc}

![Harriet Tubman](/blog/assets/NMAAHC-2017_30_48_001.png "Harriet Tubman")

As mentioned [last week]({% post_url 2020-03-02-bicker-clean %}), now that I have [Bicker](https://bicker.colagioia.net) mostly operational, I'm going to reduce the cadence of working on that code in order to make room for other projects.  But, I think the "developer journal" has been useful, so I'll continue on with the Monday morning posts.

## Blog Updates

I dumped an assortment of upgrades to the blog code, this past week.  It was well past time for another upgrade and Jekyll is still accomodating.

### Suggestions

Probably the biggest change comes from realizing that I now had released around sixty posts and am starting to see increasing traffic---welcome, readers from Albania, Argentina, Australia, Austria, Belgium, Brazil, Canada, China, Denmark, France, Germany, Hungary, India, Ireland, Israel, Italy, Nepal, the Netherlands, New Zealand, Norway, Panama, Romania, Russia, Serbia, Spain, Switzerland, Thailand, Turkey, the United Kingdom, and the United States---come through the blog.  While those are definitely milestones that please me, it also means that the blog has the potential to look intimidating to a new reader.  That is, if a potential reader drops into the blog index, there's no real way to get a sense of where to start reading.

The solution?  Recommend some posts!

I now mark certain posts---the writing that might be of broader interest or that explains a longer-term project---with a recommendation blurb that appears in a sort of slide-out tray on index pages.

![Open Tray](/blog/assets/recommended-panel.png "Open Tray")

The links are collected by an included component that tracks down and formats those recommended posts.  Be warned that putting [Liquid template](https://shopify.github.io/liquid/) code into a [Jekyll](https://jekyllrb.com/) post gets processed the wrong way around, so I've replaced the braces (`{}`) with square-brackets (`[]`) to prevent the code from actually including the recommended URLs here instead of showing you the code.

```html
<ul>
  [% for post in site.posts %]
    [% if post.recommend %]
      <li>
        <a href=[[ post.url | prepend: "/blog" ]]>
          [[ post.title ]]
        </a>
        <i>
          [[ post.recommend ]]
        </i>
      </li>
    [% endif %]
  [% endfor %]
</ul>
```

Maybe unsurprisingly, the heavy lifting is done in CSS, only opening the recommendations when the user hovers over the small tab.  The following is simplified, but you can see the full file in [the code repository](https://github.com/jcolag/entropy-arbitrage-code).

```css
.tray-panel {
  height: 40vh;
  left: 0;
  overflow-x: hidden;
  overflow-y: auto;
  position: fixed;
  top: calc(50% - 20vh);
  width: 2em;
}
.tray-panel .tray-pull {
  display: block;
  margin-top: calc(20vh - 0.5em);
}
.tray-panel .tray-contents {
  display: none;
  padding-left: 2em;
  padding-right: 2em;
}
.tray-panel:hover {
  width: 33vw;
}
.tray-panel:hover .tray-contents {
  animation: fadein 2s;
  display: block;
}
@keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}
```

The `overflow` properties prevent a rogue header from sticking out, while the `position` and `top` allow me to keep the panel fixed near the vertical center of the page, similarly with the `tray-pull` class centering the chevron in the panel.  The `hover` pseudo-classes then change the width of the panel while hiding the chevron and revealing the real contents.

Note that my original vision was to use the header as a cue to open the panel instead of a chevron.  In that case, I had code to rotate the header and move it into place as the text faded in.  Eventually, I abandoned that idea as too difficult to center in the collapsed panel.

### Not Breaking the Search

One problem with a blog that includes development *and* goes through some data format conversions is that backslashes (`\`) don't always turn out well.  The big impact I felt was on the [search page](https://john.colagioia.net/blog/search/).

The current approach to searching is to compile the entire blog into a single JSON document, which the search page uses to instantly find what you ask for as you type.  Normally, that's fine, but a rogue backslash causes a lot of parsers to interpret the JSON as invalid.

I tried manually escaping all the backslashes (`\\`) in the Markdown files, but it didn't always help and most of the doubled backslashes appeared in the final HTML.

Eventually, I worked my way through a few experiments with Liquid templates and determined that I could escape the backslashes *just* when creating the JSON files by calling `replace: "\", "\\\\"` on my post bodies.

...And then I needed to go through all the *old* posts with backslashes to fix them.

### General Housekeeping

You might notice that I've tweaked some other things with mostly cosmetic consequences.  For example, the tags are now formatted more like buttons than code snippets and the tag page no longer has the unnecessary extra separator line at the bottom.

I also improved the handling of colors, to better fit what's possible in [SASS](https://sass-lang.com/).

Incidentally, something I don't like about working with Jekyll that I don't *think* I've mentioned is that---as far as I've been able to tell---most of my CSS changes need to be marked as `!important` to override the existing theme's style.  That seems like a recipe for disaster.  Another small issue is that, since Liquid fills in its templates before anything else happens, I can't easily show any Liquid code.  Other than that, this hasn't been bad at all!

## Small Upgrades

I haven't been paying it much attention, but Bicker needs upgrades to both the [puma](https://rubygems.org/gems/puma/versions/4.3.1) and [nokogiri](https://rubygems.org/gems/nokogiri) libraries.  Conveniently, [Dependabot](https://dependabot.com/) monitors these things and creates pull requests, so there wasn't much to be done other than accepting the request.

## Character Generator

When I wrote about [**Seeking Refuge**]({% post_url 2019-12-14-seeking-refuge %}), I mentioned [a tool](https://github.com/jcolag/ProceduralStories/blob/master/people/generate.js) that I've been working on occasionally, to create the skeleton of a character outline for a global sample set.

One of the things I've never liked about the project is that it's just a script.  I can open a terminal window and run it...

![Example output](/blog/assets/console-character-profiles.png "Sample output")

...but that's deeply unsatisfying.  I need to be in a position to run [Node](https://nodejs.org/en/) programs and can't just point people to a running example, when they need it.  So, I've been thinking for a while that this might be better suited as a simple website.  A presentation like that would also make it easier to include other media, beyond a tiny color swatch and a flag.

Oh, speaking of flags, the flag emoji doesn't work correctly in most consoles.  Rather than 🇹-🇷​, read it as 🇹🇷​​​​​.  Yes, the flags are made up by the ISO country code emoji pair.  Likewise, the hand emoji changes color based on the skin tone that follows it instead of separating them.

Since this is just displaying static or generated data, it looks like the best bet for a project like this is going to be [Express](https://expressjs.com/).  From a quick glance, it looks very much like a bare minimum framework that expects the developer to deal with everything.  But again, we're only talking about serving one page with data pieced together from files, so that's probably not a bad thing.

Once Express has been installed in a Node project (`npm install --save express`), it's straightforward to get a single page up and running.

```node
const bodyParser = require('body-parser');
const express = require('express');
const app = express();

app.use(express.static('public'));
app.use(bodyParser.urlencoded({ extended: true }));
app.set('view engine', 'ejs');

app.get('/', function (req, res) {
  res.render('index', { 'key': 'value' });
});

app.listen(5000, function () {
  console.log('Example app listening on port 5000!');
});
```

The `app.get()` function handles an HTTP `GET` request (and there's a `.post()` to go with it), where---in this case---we render a `.ejs` file, or JavaScript embedded in HTML.  That's pretty close to ideal, since we basically just want to generate a data payload and display it formatted cleanly as HTML.

I already have the code that generates the payload, albeit as text instead of something sensible like JSON, but that's an easy enough fix.

Then, the aforementioned `.ejs` files are just HTML templates with some JavaScript added in special tags.  So, `<%= key %>` digs into the javascript object passed to `res.render()` above, and will (in this case) insert the word "value" into the web page.

Some fonts ([Alfa Slab One](https://fonts.google.com/specimen/Alfa+Slab+One) and [Lora](https://fonts.google.com/specimen/Lora), snagged from Google Fonts), a decent color scheme, and a hacked-together pseudo-woodgrain background image (noise, motion blur) later, and it's more or less what I wanted.

### But Where *Are* We?

One of the reasons I've wanted this project as a web page is one specific enhancement that would obviously never work in text:  A map, showing the random location and the five nearest cities.

To do that, I don't feel like using any of the big mapping services for a variety of reasons, licensing among them.  So instead, I followed [Leaflet's Quick Start Guide](https://leafletjs.com/examples/quick-start/) and had fully functional map (markers for the position and five cities with pop-up labels, panning, and zooming) in...maybe half an hour?

I'll be honest, one of the things that finally convinced me to make this a standalone project **was** hearing someone talk about [Leaflet](https://leafletjs.com/) and wanting to see how it is to use in a real project.  It turns out that it's a *tiny* bit clumsy, in that it uses JavaScript to transform an HTML element into the map (not uncommon), but...other than that, the code looks something like the following.

```JavaScript
var map = L
  .map('map')
  .setView([<%= person.coordinates %>], 8);
L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
  attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
  maxZoom: 18,
  id: 'mapbox/streets-v11',
  tileSize: 512,
  zoomOffset: -1,
  accessToken: '<%= mapboxToken %>'
}).addTo(map);
L.marker([<%= person.coordinates %>])
  .addTo(map)
  .bindPopup('<%=person.latitude%> <%=person.longitude%>')
  .openPopup();
for (var i=0; i<cities.length; i++) {
  var city = cities[i];
  var circle = L.circle([city.latitude, city.longitude], {
    color: '#b780a0',
    fillColor: '#95557a',
    fillOpacity: 0.5,
    radius: 10000,
  }).addTo(map);
  circle.bindPopup(city.name);
}
```

See?  Create the map with coordinates and zoom-level.  Set the map to pull the tiles from [Mapbox](https://www.mapbox.com/); you'll need your own account and token, but that took seconds and could replace it with another service, provided you're willing to change that URL template.  Add the marker and add 10km-radius circles to mark each city.  It reminds me a bit of [D3](https://d3js.org/), where most work operating on an element can be done through a chain of method calls.

![Example](/blog/assets/chargen-leaflet-example.png "An example")

It's not *perfect*, mind you.  As you can see in the sample above, labels on the map, such as route numbers, frequently get cut off where the tiles change.  But for a free library that moves this fast and smoothly?  It's fine and I don't need much more than that and---to be clear---I don't really know if that label problem is in Leaflet, Mapbox, or some interaction between the two.

However, there are two changes that I'll eventually want.

 * Possibly hiding (or shrinking) the map on page load, with a way to expand it to full size, which has nothing to do with Leaflet.
 * Scale the map so that the six markers are all visible.

But for now, this definitely fits my requirements.  The first one is just a little bit CSS and JavaScript and the second is almost certainly a "get the bounds of a list of markers, and set the scale based on that" kind of deal, so I'm not concerned.  I'll probably take care of at least one of the two in the upcoming week.

### Serving the Application

The last big step is setting this up so that I can get at it through my existing web server.  Unfortunately, this is non-trivial.

 * Express.js is running its own web server, so I can't just dump the files onto my existing server, which is served by [Apache](https://httpd.apache.org/).
 * I don't see any evidence of a Node.js web framework that Apache will just run, like it will a Ruby or PHP application.
 * In theory, I *could* run the web server on a separate port and just point everybody to `:5000` or whatnot, but Apache server is configured to automatically rewrite all HTTP requests to HTTPS and this application doesn't do HTTPS.
 * The right way to handle this, then, is to use Apache as a **proxy**, asking it to act like a conduit between the browser and the "real" web server.  However, I followed four separate sets of instructions on how to do this and couldn't get it to work.
 * I should be able to "cheat" and have Express.js use a self-signed certificate.  That works for my own computer, but not for my server, since the rules are presumably different.
 * Finally, I can use [Let's Encrypt](https://letsencrypt.org/) for a certificate, but...well, once again, that's non-trivial.

As mentioned, for *localhost*, we can just self-sign a certificate.

```sh
mkdir keys
cd keys
openssl req -nodes -new -x509 -keyout key.pem -out cert.pem
```

But for a server, we need to be more clever.  Be **very** careful, here.  You can re-use an existing domain without any trouble.  But if you use a domain that Let's Encrypt uses as the name of the certificate's files, you might be in for some confusion.  Of course, if you only have one domain, feel free to use that certificate, since that's all you need.

```sh
certbot --webroot -w ./static -d domain.tld
# replace 'domain.tld' with the real domain, like
# I put the server on 'colagioia.net'
ln -s /path/to/domain/keys keys
```

On my server, the keys are stored at `/etc/letsencrypt/live/domain.tld/`.  I also needed to mess around with permissions to make the link work.  But otherwise, it was just a matter of changing the `.listen()` call with this.

```javascript
var https = require('https');
/* ... */
app.use(require('helmet')());
/* ... */
https
  .createServer({
    key: fs.readFileSync('keys/key.pem'),
    cert: fs.readFileSync('keys/cert.pem')
  }, app)
  .listen(5000, function () {
    console.log('Example app listening on port 5000!');
  });
```

So far, so good, though I wasted far too much time working this out and would still much rather have the proxy.  That should probably be in a `try`/`catch` so that people who aren't interested in setting up the keys can function on HTTP.

### To the Background!

Obviously, we don't want to need me to log in to run the server for this to be usable, so instead, we'll use the [forever](https://www.npmjs.com/package/forever) package.

```sh
npm install forever -g
forever start index.js
```

And...we're live!  🥂  Check it out at <https://colagioia.net:5000/>.  I even set up a job that should (hopefully 🤞) restart the server on reboot, so this should be mostly hands-off.  Well, hands-off, *except* that I still need to set up the aforementioned job to renew the certificate, so if you're looking at this in forty-five days or so and you can't access the server...that's going to be why.

## Next

I have a couple of items to deal with for the background generator:

 * The renewal job...which I only *just* realized (seeing the status e-mail) is already handled for my normal domains ✔️,
 * Scaling the map appropriately, and
 * Hiding the map...which is less likely, as I'm less interested in that as time goes on and I've gotten used to seeing it, honestly, so...✔️.
 * A custom footer might be nice, so that people who host it can note whatever they need to note, like I'm crediting [Colagioia Industries](https://colagioia.net) for hosting manually.

So, the list pares itself down to scaling the map and the footer.

I'd also like to write more tests for Bicker, this week, while the idea is still fresh.  There's also another project or two waiting, but I'm not convinced the user interface technologies I want to use are up to the task.

* * *

**Credits**:  The header image is [Matte collodion print of Harriet Tubman](https://www.si.edu/object/nmaahc_2017.30.48), long since in the public domain, but appropriate, given that tomorrow is [Harriet Tubman Day](https://en.wikipedia.org/wiki/Harriet_Tubman_Day) and the Trump administration has punted on putting Tubman on the twenty-dollar bill...
