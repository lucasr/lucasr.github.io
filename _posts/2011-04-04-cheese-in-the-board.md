---
id: 2249
title: Cheese in The Board
date: 2011-04-04T00:07:42+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2249
permalink: /2011/04/04/cheese-in-the-board/
categories:
  - Free Software
  - General
  - GNOME
  - Software
  - Archived
tags:
  - announcement
  - cheese
  - community
  - feature
  - GNOME
  - hacking
  - libcheese
  - photos
  - planet
  - release
  - the board
  - video
  - webcam
---
<div style="width: 510px" class="wp-caption aligncenter">
  <a href="http://vimeo.com/21895207"><img src="http://farm6.static.flickr.com/5176/5587113978_d75f1c9429.jpg" width="500" height="317" /></a>
  <p class="wp-caption-text">
    Cheese in The Board
  </p>
</div>

I spent a few spare hours during this week to finally implement webcam support
on [The Board](http://live.gnome.org/TheBoardProject)'s photo elements. I still
need to polish the design a bit but it's pretty nice already! Click the image
above to see a [video](http://vimeo.com/21895207) demonstrating how it works.

As you can see, I haven't shown my face on the demo video. This is because I
recorded it too late today and I would definitely have to shave—yes, I'm
looking like an ogre at the moment. So, I preferred to introduce the feature
using one of my daughter's favourite toys, my
pet [mug](http://lucasr.org/2010/05/17/mugs/), and my charming hands instead.

This feature was very simple to implement thanks to
[Cheese](http://projects.gnome.org/cheese/)'s library (libcheese) which
recently received a lot of [love](http://blog.fujii.eti.br/?p=70) from
[Luciana](http://blog.fujii.eti.br/). Thanks to her and the Cheese team I was
able to use Cheese's functionalities in The Board with little hassle. The
photos are saved on the location than the photos taken with the Cheese app.
When you don't explicitly write a caption before taking the photo, The Board
gracefully defaults to a date and time caption—see third photo on the video.

This work is not in git master just yet because I need to get
a [few](https://bugzilla.gnome.org/show_bug.cgi?id=646622)
[fixes](https://bugzilla.gnome.org/show_bug.cgi?id=646620) in Cheese first. So,
I've pushed the code to a [remote
branch](http://git.gnome.org/browse/the-board/log/?h=cheese) for now. This
feature should be available to testers soon—in the next development release.
Stay tuned!
