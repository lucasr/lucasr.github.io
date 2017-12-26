---
id: 1648
title: Videos in The Board
date: 2010-08-04T00:26:01+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=1648
permalink: /2010/08/04/videos-in-the-board/
categories:
  - Free Software
  - General
  - GNOME
  - Software
  - Archived
tags:
  - call for ideas
  - clutter
  - clutter-gst
  - community
  - Free Software
  - GNOME
  - hacking
  - patch
  - planet
  - Software
  - the board
  - video
---
[<img class="alignnone" src="http://farm5.static.flickr.com/4093/4858123317_c07cedef07.jpg" width="500" height="313" />](http://vimeo.com/13869009)

So, you now know about [The
Board](http://lucasr.org/2010/07/24/introducing-the-board/) and my short-term
and long-term plans for it. Thanks everyone for the positive energy and the
nice feedback! For those interested in contributing to the project, I created a
very basic [wiki page](http://live.gnome.org/TheBoardProject) for The Board in
GNOME's wiki. The most useful bit for now is the [initial
guide](http://live.gnome.org/TheBoardProject/Build) to get The Board built and
running. Feel free to fix and add missing bits there.

I had a couple spare hours a few days ago and ended implementing the initial
code for video things. Seek bar is still missing because I couldn't find a nice
way to present it — ideas are welcome. Code is available
in [gitorious](http://gitorious.com/the-board). Click on the image above to
watch a [video](http://vimeo.com/13869009) showing more or less how it works.
The general interaction is very similar to photos. I had to apply [a couple
patches](http://bugzilla.clutter-project.org/show_bug.cgi?id=2176) to clutter
and clutter-gst (git master) to get video colours right.

Things will become more interesting when I implement integration with Cheese
which will allow you to produce photos and videos in place. Probably one of my
next steps.
