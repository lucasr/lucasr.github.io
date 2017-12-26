---
id: 139
title: Plugins in The Eye
date: 2007-05-15T09:59:06+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/05/15/plugins-in-the-eye/
permalink: /2007/05/15/plugins-in-the-eye/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - EOG
  - epiphany
  - gedit
  - GNOME
  - gtkiconview
  - hacking
  - patch
  - plugin
  - plugin system
  - postr
  - release
---
Eye of GNOME 2.19.2 is the second _under-heavy-development_ release of Eye of
GNOME in the direction of GNOME 2.20. This is a special release: it's the first
one that ships the new plugin system which allows developers to extend EOG's UI
and behavior. Of course, a lot of polishing is still needed but the
possibilities are quite vast.

Special thanks go to the [Gedit](http://www.gnome.org/projects/gedit) and
[Epiphany](http://www.gnome.org/projects/epiphany) teams because most of the
EOG plugin system code came from those projects.

As usual, please, crash, play, use, crash again, **extend** EOG as much as you
can. :-)

**First EOG plugin**

As a proof of concept for the plugin system, I wrote a very simple plugin which
nicely integrates EOG and [Postr](http://burtonini.com/blog/computers/postr).

[<img class="alignnone" style="border: 0px initial initial;" src="http://lucasr.org/wp-content/uploads/2007/05/eog-postr-thumbnail.jpg" border="0"/>](http://lucasr.org/wp-content/uploads/2007/05/eog-postr.jpg)

<img class="alignnone" src="http://lucasr.org/wp-content/uploads/2007/05/eog-postr-menu.png"/>

<img class="alignnone" src="http://lucasr.org/wp-content/uploads/2007/05/eog-postr-dialog.png"/>

Three important notes about the screenshots and the plugin:

  * I haven't released the plugin code yet because it's just a proof of concept
  thing. Now I need to write it the right way.
  * The thumbnails pane in Eye of GNOME is using a
  [patched](http://bugzilla.gnome.org/show_bug.cgi?id=382544) GtkIconView which
  makes the selections much more visible.
  * For those who use Postr, you probably saw something different in its UI.
  You're right! I've made some improvements in the thumbnails pane.
  [Ross](http://burtonini.com) already merged in the main
  [repository](http://burtonini.com/bzr/postr/postr.dev).
