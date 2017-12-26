---
id: 2076
title: Selection in The Board
date: 2011-01-26T02:30:23+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2076
permalink: /2011/01/26/selection-in-the-board/
categories:
  - Free Software
  - General
  - GNOME
  - Software
  - Archived
tags:
  - align
  - community
  - context-sensitive
  - design
  - distribute
  - distro
  - Free Software
  - GNOME
  - hacking
  - move
  - planet
  - selection
  - Software
  - the board
  - toolbar
  - ui
  - ux
---
<div style="width: 510px" class="wp-caption alignnone">
  <a href="http://vimeo.com/19193773"><img src="http://farm6.static.flickr.com/5129/5382956592_c71a611b2f.jpg" width="500" height="335" /></a>
  <p class="wp-caption-text">
    Selected Elements
  </p>
</div>

Since I started dogfooding [The Board](http://live.gnome.org/TheBoardProject)
on a daily basis, it became clear to me that not having a simple way to arrange
multiple elements in the page is quite annoying. If you wanted to arrange
multiple elements in a specific area of the page, you'd end up having to move
each element separately, one by one. Argh! This is why I decided to focus on an
initial set of features targeting this specific issue for the upcoming release.

You can now select, move, align, distribute, and remove multiple elements in a
page. Click on the image above to see a [video](http://vimeo.com/19193773)
demonstrating the new features. Selection can done in three ways: the usual
dragging from background to start selecting a region of the page, Ctrl+clicking
on elements, or using Ctrl+A to select all elements in the page.

Once more than one element is selected, a context toolbar slides in presenting
all available operations for the selection. I'm following the same obviousness,
clarity, and consistency principles I've
[discussed](http://lucasr.org/2010/11/17/context-toolbars-in-the-board/)
before. The available operations for any app state are always visible and
easily accessible. No need to dig around to find out what to do.

As usual, feedback on the design decisions are more than welcome. So, what's
next? I'll be fixing a few critical bugs and then roll a new release. I've been
pestering distro guys to create packages for The Board. I'll hopefully be
announcing the next release with links to distro packages.
