---
id: 113
title: Hildon Desktop + FreeDesktop.Org
date: 2007-02-13T11:40:00+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/02/13/hildon-desktop-freedesktoporg/
permalink: /2007/02/13/hildon-desktop-freedesktoporg/
categories:
  - Free Software
  - General
  - Maemo
  - Archived
tags:
  - Desktop
  - freedesktop.org
  - GTK
  - gtkstatusicon
  - hacking
  - Hildon
  - hildon desktop
  - libnotify
  - Maemo
  - notifications
  - standards
  - system tray
---
We've been trying to put some effort on making [Hildon
Desktop](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/hildon-desktop/)
more compliant with [FreeDesktop.Org
standards](http://www.freedesktop.org/wiki/Standards). We have some nice news
on this direction.

**Desktop Notifications**

I added a service that implements the [Desktop
Notifications](http://www.galago-project.org/specs/notification/) draft
standard. It's not complete yet, I still need do some changes on one of [our
widgets](https://stage.maemo.org/svn/maemo/projects/haf/branches/hildon-libs/hildon-1),
but it's working like a charm. Also, support for multiple notifications at the
same time is pending. In practice, this means that applications using
[libnotify](http://www.galago-project.org) (or any other compliant client
library) will have their notifications shown on Hildon Desktop! Here is the
result:

![](http://lucasr.org/wp-content/uploads/2007/02/notification.jpg)
_Hildon Desktop showing a notification using libnotify._

**Notification area (aka system tray)**

[Moises](http://www.moimart.org) rocked our world by adding support for [system
tray standard](http://www.freedesktop.org/wiki/Standards/systemtray-spec) in
Statusbar. This means that if you use
[GtkIconStatus](http://developer.gnome.org/doc/API/2.0/gtk/GtkStatusIcon.html)
(or any other compliant implementation of the client-side) it will appear in
Statusbar. Of course, still the usual Statusbar plugins can be loaded in
Statusbar too. There are some pending issues with the theming of systray items
(as you can see in the screenshot) but we expect to have it fixed soon. Here is
a (mandatory) screenshot of Hildon Desktop running inside Scratchbox:

![](http://lucasr.org/wp-content/uploads/2007/02/systray.jpg)
_Statubar showing Gossip and Network Manager systray icons._

**Update**: Moises has just fixed the theming problem. Yay!
