---
id: 107
title: Image Properties in EOG
date: 2007-01-24T12:00:38+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/01/24/image-properties-in-eog/
permalink: /2007/01/24/image-properties-in-eog/
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
  - image properties
  - ui
---
I've been working on replacing the image info sidepane in EOG with an image
properties dialog. IMHO, this is a less invasive and more consistent aproach.
The sidepane takes too much space of the image view mostly when you want to
visualize the image EXIF data. Also, just dumping all EXIF data is not very
user-friendly. Therefore, another goal here is to make it more user-friendly.

<img class=" alignnone" src="http://lucasr.org/wp-content/uploads/2007/01/eog-current-ui.jpg" alt="" />

So, in [eog-ng](http://svn.gnome.org/svn/eog/branches/eog-ng/) there's an EXIF
tab in image properties dialog which at first sight only shows a summary of the
most common things you want to see in EXIF (aperture, shutter speed, flash,
ISO, date, etc). But I still want to give the possibility to view the
whole EXIF data for advanced users. So, just click on the "Details" expander
and you can view all EXIF tags. With the navigation buttons in the dialog, you
can easily check EXIF data from each image.

<img class=" alignnone" src="http://lucasr.org/wp-content/uploads/2007/01/eog-exif.png" alt="" />

I still want some feedback about it and some help on which EXIF should appear
in the summary and in what order. Discussion about image properties should take
place in [bug #313676](http://bugzilla.gnome.org/show_bug.cgi?id=313676).
