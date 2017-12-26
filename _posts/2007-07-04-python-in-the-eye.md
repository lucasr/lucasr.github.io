---
id: 147
title: Python in the Eye
date: 2007-07-04T22:53:36+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/07/04/python-in-the-eye/
permalink: /2007/07/04/python-in-the-eye/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - EOG
  - hacking
  - ideas
  - plugin
  - plugin system
  - python
---
As I've
[announced](http://blogs.gnome.org/lucasr/2007/05/15/plugins-in-the-eye/)
before, the [development version](http://svn.gnome.org/svn/eog/trunk/) of [Eye
of GNOME](http://www.gnome.org/projects/eog/), your beloved image viewer,
features a new plugin system which allows you to extend EOG's UI and behavior.
Now that I added **python support** to the plugin system, the only thing is
missing is a bunch of cool plugins! :-)

I'll pay a beer (at GUADEC) for each one who develops a cool plugin and helps
us to improve our plugin system. I have some ideas for a start:

  * _File browser pane_: something like the File Browser Gedit plugin;
  * _Flickr Uploader_ (aka Postr integration): I have a prototype ready for
  this one;
  * _Photo feed viewer_: add support for adding, removing, and viewing photo
  feeds;
  * _Blog This Image_: this one could be done by integrating with good/old
  gnome-blog app;
  * _Add watermark to Image_: you would be able to add the watermark from a
  text or from an existing image;
  * _Location on Statusbar_: show a statusbar icon with a tooltip showing
  location info (city, country, neighborhood, street, etc) embedded in the
  image;
  * _Creative Commons Licence_: show a statusbar icon with a tooltip showing
  the license embedded in the image;
  * Add your suggestion here!

Volunteers!? :-)

**The Side Pane problem**

I want to allow plugins to add functionalities to a side panel in EOG. As you
probably know, there's no such side panel in EOG yet. Considering that
currently you can place the image collection pane on the top, bottom, right, or
left side of the window (a feature requested by several users), how can I have
the (left) side pane (for plugins) and allow the image collection pane to be on
the left side as well?

In the case of Gedit, the side panel has a documents list (the equivalent UI
element of EOG's image collection pane) and other "pages" can be added
to the panel by the plugins. In the case of EOG, this would not be a good
approach because the image collection pane is something that you want to keep
visible all the time and the side bar should always be on the left side.

Any suggestion?
