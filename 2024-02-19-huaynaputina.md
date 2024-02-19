---
layout: post
title: Developer Diary, Eruption of Huaynaputina
date: 2024-02-19 06:29:05-0500
categories:
tags: [programming, project, devjournal]
summary: Progress on assorted projects
thumbnail: /blog/assets/3587376222_a401a77c8f_o.png
offset: -15%
teaser: This week's projects include Notoboto and early phases of the secret-but-not-really project.
spell: Notoboto Huaynaputina Colca Tk Hualca Enking
proofed: true
---

Today marks the 424<sup>th</sup> anniversary of the massive eruption of [Huaynaputina](https://en.wikipedia.org/wiki/Huaynaputina) in what we now call southern Peru.  Records suggest that people may have seen indications of the impending eruption as early as December 1599, and that it lasted for half to nearly a full day, with ash falling in the area for weeks.

If you live in the United States, you know about the eruption by reputation, even if you've never heard the name or connected it to a volcano.  For example, the trouble that the English had in establishing [Jamestown](https://en.wikipedia.org/wiki/Jamestown,_Virginia) and the [1605 California floods](https://en.wikipedia.org/wiki/California_flood_of_1605) both trace their origins to the eruption, and the entire Northern Hemisphere seems to have had at least one wet summer and colder winter around 1601.

![Colca Canyon, the remnants of Huaynaputina](/blog/assets/3587376222_a401a77c8f_o.png "What a difference four centuries makes, right?")

I assure you that none of these projects will remotely have the importance of either holiday, and I don't think that I'd want them to, honestly, unless they actually advocated for protecting people.

## Not-So-Secret Project

I don't remember if these changes went out during this week, but [**The Light's Edge**'s landing page](https://www.thelightsedge.com/) now includes a minimal e-mail submission form.  For anybody needing to do this, since I already have [PHP](https://en.wikipedia.org/wiki/PHP) running on my VPS for other purposes, I whipped up a quick script to pass the address on to me based on this rough pattern.

```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  $email = $_POST["email"];
  if (filter_var($email, FILTER_VALIDATE_EMAIL)) {
    $to = "email.address@example.com";
    $message = "Email: $email";
    mail($to, $subject, $message);
    echo "Email submitted successfully!";
  }
}
?>
```

I don't have newsletter software running at the other end of this, only an e-mail account from which I'll manually blind-copy people announcements when parts of the story go live.

## Notoboto

{% github jcolag/Notoboto %}

As mentioned at some point, I have started some much-needed cleanup, here, such as removing unused code and stubbing out fields that don't exist in the oldest versions of notes.

However, I also now allow for creating a new note without having a note already selected.  I don't know how I overlooked that problem.

In addition, I have replaced my awful text-based attempts to convey the search modifiers (case-sensitivity, whole-word, and regular expressions) with [Material Design's icons](https://fonts.google.com/icons).  Alas, Tk can't read something in their SVG files, so it uses the PNG versions, for now.

For consistency, I have started moving other Material Design icons into place for other features.

## Next

I still have work to do on **Notoboto**, so expect to stay focused there, though the backlog of library updates does keep growing.

* * *

**Credits**:  The header image is [Hualca Hualca](https://www.flickr.com/photos/33037982@N04/3587376222/) by [Leonora (Ellie) Enking](https://www.flickr.com/photos/33037982@N04/), made available under the terms of the [Creative Commons Attribution Share-Alike 2.0 Generic](https://creativecommons.org/licenses/by-sa/2.0/deed.en) license.
