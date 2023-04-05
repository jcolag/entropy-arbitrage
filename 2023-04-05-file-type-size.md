---
layout: post
title: Normalizing Image Type and Size
date: 2023-04-05 07:10:05-0400
categories:
tags: [linux, programming, techtips]
summary: Using ImageMagick to produce application-friendly images.
thumbnail: /blog/assets/man-sand-people-street-artist-material-1338169-pxhere.com.png
teaser: I have some image-manipulation gimmickry that I needed to learn to schedule Mastodon activity.
proofed: true
---

Amusingly, I worked this out a while ago, when I finished the main work of the Mastodon-scheduling script in my [**Mastodon Tool Trunk**](https://github.com/jcolag/tool-trunk) in late January.  I meant to post about it then, but things got away from me, so you'll instead get a short post now.

![A black and white photograph of a bearded person in jeans and a leather jacket, drawing a complex image on a cobblestone surface](/blog/assets/man-sand-people-street-artist-material-1338169-pxhere.com.png "Sadly, you can't hire this guy to make things happen...")

In getting images acceptable to social media sites like Mastodon, I ran across two problems.

 * Source images can run to sizes far larger than the server will accept.
 * Many online publishers have embraced a variety of new image formats---I've seen WebP and AVIF images showing up with greater frequency---that social media sites haven't caught up to.

When I scheduled the posts manually through a web application, I'd take care of the images manually, as well.  I'd download them, put them through an on-computer or web-based converter to get a PNG or JPEG file, and then resize them in [GIMP](https://www.gimp.org/); pardon my use of a name that the developers *know* offend people and have repeatedly refused to change it.  That works, but it takes a lot of time.

For an automated process, I could really only see [ImageMagick](https://imagemagick.org/)---or one of its derivatives that occasionally gets some press---as a viable route forward.  And with some research, I came to this gem for handling both the image type and the size at once.

```console
convert '*.*' -resize 256x\> -set filename:fn \
  '%[basename]' '%[filename:fn].png'
```

This exaggerates the job, but it resizes any image wider than 256px *to* a width of 256px---more likely, I want 1024px, in practice, but this works as an example---and converts it to a PNG file.  ImageMagick does, in fact, know about WebP and AVIF, so I have my bases covered until the next technology shows up.

Oh, and if you only want to change one file, instead of everything in the folder, you can simplify that by removing the `filename` function, leaving something more straightforward, like this.

```console
convert target_image.avif -resize 256x\> target_image.png
```

Really, though, I had no intentions of using the command line.  Rather, I wrote the scheduler script in Ruby, so I need this to happen there.  As it turns out, from one of my first Rails projects, I know about the [`rmagick` gem](https://rubygems.org/gems/rmagick).  Using that, I get code that looks more like this, assuming that the script has already downloaded a source image.

```ruby
require 'rmagick'
def convert_image(filename, max_width)
  outfile = "#{filename}.png"
  img = Image.read(filename).first
  small = img.change_geometry!("#{max_width}x#{max_width}>") do |cols, rows, _img|
    img.resize(cols, rows)
  end
  small.write outfile
  File.delete filename
  outfile
end
```

You might notice that we have similar features, here.  In both cases, we resize to a maximum width---and height, too, since we occasionally see some wildly tall, narrow images---and then save it in the correct image format.  This particular implementation then deletes the source file and returns the name of the new version, but we care about that less, in this discussion.

You might notice that the resizing code doesn't need the backslash, here.  We only needed it for working on the command-line, since the shell will interpret the greater-than character (`>`) as redirecting output to a file.  Ruby knows better.

ImageMagick has an absurd number of features, honestly.  I even use it to create boring sample images, when I *test* the scheduler.

```console
convert -size 100x100 xc:#dccea1 test.png
```

This creates a solid square, using the background color from the blog.

At this point, it usually strikes me as stranger when I discover something that ImageMagick does *not* do, such as when I wrote [the script to create a collage of emoji]({% post_url 2021-10-06-collage %})...

* * *

**Credits**:  The header image is adapted from [untitled](https://pxhere.com/en/photo/1338169) by an uncredited PxHere photographer, made available under the terms of the [Creative Commons CC0 1.0 Universal Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/).
