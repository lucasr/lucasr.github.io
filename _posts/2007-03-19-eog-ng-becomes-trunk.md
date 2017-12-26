---
id: 122
title: eog-ng becomes trunk
date: 2007-03-19T19:48:13+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/03/19/eog-ng-becomes-trunk/
permalink: /2007/03/19/eog-ng-becomes-trunk/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - EOG
  - eog-ng
  - GNOME
  - hacking
  - news
  - release
  - Roadmap
---
You've seen [some](http://blogs.gnome.org/view/lucasr/2007/02/05/0)
[cool](http://blogs.gnome.org/view/lucasr/2007/02/03/1)
[development](http://blogs.gnome.org/view/lucasr/2007/01/24/0)
[news](http://blogs.gnome.org/view/lucasr/2007/01/22/0) in my blog about eog-ng
branch, right? The good news is that last weekend I merged
[eog-ng](http://svn.gnome.org/svn/eog/branches/eog-ng/) in
[trunk](http://svn.gnome.org/svn/eog/trunk/) as part of the GNOME 2.19/2.20
development cycle. This means that we have a solid, faster and more stable code
in EOG from now on. Some highlights:

  * Feels faster and more stable _(the application core has been totally
  rewritten and optimized in several ways. This means you will feel
  that EOG startup is much faster, it uses less memory and crashes much
  less)_
  * New image collection pane _(cleaned up to make it look nicer with a one-row
  view. By setting "hidden" gconf keys you can place the
  collection pane on any window side — top, bottom, left, right
  — and it can be resizable or not)_
  * Toolbar in fullscreen
  * Image property dialog
  * "Open with" support to quickly images on other applications

Many/Special thanks to **Claudio Saavedra** and **Felix Riemann** for the
important contributions to this new code. You rock my world guys!

**Plans for 2.20**

  * Editable toolbar
  * Printing for multiple images
  * Plugin system
  * Support for IPTC and XMP
  * General UI polishing, mostly in
    * Image collection pane
    * Image properties dialog
    * Preferences dialog
    * Error/warning feedback
  * More code refactoring
  * Bug fixing, bug fixing, bug fixing, &#8230;

**Get Involved**

You can find a list of bugs/tasks here _(follow the instructions there)_:

<http://live.gnome.org/EyeOfGnome/RoadMap>

As I always say: contributions are **always** welcome! Give some love to EOG
today and have a better GNOME image viewer tomorrow! Let's make EOG rock our
world! :-)
