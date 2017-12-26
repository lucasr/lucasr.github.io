---
id: 303
title: 'Mojitito: Mojito in Javascript'
date: 2009-07-08T05:09:07+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/?p=303
permalink: /2009/07/08/mojitito-mojito-in-javascript/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - gjs
  - hacking
  - javascript
  - moblin
  - mojito
  - ui
---
<img class="alignnone size-full wp-image-304" title="mojitito" src="http://www.lucasr.org/wp-content/uploads/2009/07/mojitito.png" alt="mojitito" width="400" height="316" srcset="http://lucasr.org/wp-content/uploads/2009/07/mojitito-300x237.png 300w, http://lucasr.org/wp-content/uploads/2009/07/mojitito.png 400w" sizes="(max-width: 400px) 100vw, 400px" />

So, I wanted to play a bit with Moblin's
[Mojito](http://moblin.org/projects/mojito) just to know how cool and easy it
is to use it on GNOME. So, tonight I ended up writing "Mojitito". It comprises
a Javascript wrapper that exposes Mojito's DBus API and can be easily used in
any Javascript-based app ([GNOME Shell](http://live.gnome.org/GnomeShell) for
example) and a crappy Clutter-based UI which just lists the items in an
ultra-simple way (just wanted to write something to use the Mojito wrapper).
Anyway, you can get the code
[here](http://www.gnome.org/~lucasr/misc/mojitito/) (you need
[gjs](http://git.gnome.org/cgit/gjs) and
[mojito](http://git.moblin.org/cgit.cgi/mojito). Just run the "mojitito"
script) if you want to play with it. I only configured a test Twitter account
but a real UI implementation should be able to present items from Last.fm,
Flickr, MySpace, etc in a fancy way. Anyway, it's pretty simple to use
Mojito and I'm really looking forward to seeing this kind of stuff being
nicely integrated in our new shell!
