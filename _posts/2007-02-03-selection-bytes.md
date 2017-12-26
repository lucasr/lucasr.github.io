---
id: 109
title: Selection bytes
date: 2007-02-03T00:28:09+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/02/03/selection-bytes/
permalink: /2007/02/03/selection-bytes/
categories:
  - General
  - GNOME
  - Maemo
  - Archived
tags:
  - bug
  - GNOME
  - GTK
  - gtkiconview
  - hacking
  - patch
---
Some weeks ago, I [posted](http://blogs.gnome.org/view/lucasr/2007/01/15/0)
about how could it would be to have the GtkIconView selection looking like
[this](http://bugzilla.gnome.org/attachment.cgi?id=77963&action=view). So, the
first step was done: I cooked a
[patch](http://bugzilla.gnome.org/attachment.cgi?id=81192&action=view). I guess
when/if the patch is integrated into GTK _(I'm still waiting for the feedback
from the maintainers)_, the next step will be to do some rocking
theming work in GtkIconView selection. Comments on this subject should go on
[bug #382544](http://bugzilla.gnome.org/show_bug.cgi?id=382544).

<img class="  alignnone" src="http://lucasr.org/wp-content/uploads/2007/02/gtk-icon-view-selection.png"/>

**Update 1:** don't pay too much atention to this checkbox in this screenshot.
This is just part of GtkIconView test program with some weird layouts.

**Update 2:** for those interested, the rounded borders will come the theme
engine, not in GTK itself.
