---
id: 110
title: EOG statubar
date: 2007-02-03T01:26:14+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/02/03/eog-statubar/
permalink: /2007/02/03/eog-statubar/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - EOG
  - eog-ng
  - exif
  - GNOME
  - hacking
  - statusbar
  - ui
---
I heard very often that there are some EXIF info that users are really interest
in having easy/quick access to. EXIF presentation was really improved as I
already [reported before](http://blogs.gnome.org/view/lucasr/2007/01/24/0).
EOG's statusbar could be used to show really common EXIF values like date and
exposure values. I wanted to do this in a way that not much noise is added to
statubar. Here's the result:

[<img style="border: 0px initial initial;" src="http://lucasr.org/wp-content/uploads/2007/02/eog-statusbar-thumbnail.jpg" border="0"/>](http://lucasr.org/wp-content/uploads/2007/02/eog-statusbar.jpg)

I haven't commited this yet because I'd like to get some feedback first. Some
additional related issues:

  * Is there a way to show exposure values in a non-photographer-friendly way?
  I'm thinking in adding a GConf key to optionally enable something like
  "exposure info in statubar". End-users would free from those evil info then.
  * Should the time reside on statusbar?
  * Show simplified date/time ("23/12/2007, 12:48") or a full descriptive one
  ("23 December 2007, 12:48")?
  * What do you think is missing in statusbar?

Comments?
