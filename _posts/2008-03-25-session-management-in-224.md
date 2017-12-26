---
id: 206
title: Session Management in 2.24
date: 2008-03-25T00:00:40+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2008/03/25/session-management-in-224/
permalink: /2008/03/25/session-management-in-224/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - community
  - GNOME
  - hacking
  - maintainer
  - revamp
  - rewrite
  - Session
  - session management
---
In 2006, [Dan Winship](http://mysterion.org/~danw/blog/) presented [some
ideas](http://mail.gnome.org/archives/desktop-devel-list/2006-September/msg00084.html)
about the future of session management in GNOME. He wrote the initial code and
defined this nice architecture which turns gnome-session into a more generic
session management system and makes it easier to eventually replace the current
XSMP-based session management with a saner and less cryptic D-Bus-based
protocol in the future. On June 2007, he made a code drop on a branch called
[new-gnome-session](http://svn.gnome.org/svn/gnome-session/branches/new-gnome-session/)
and stopped working on that (for various personal reasons).

Since October 2007, I've been sparsely working on this new code (with full
support from Dan) on my spare time by filling some gaps, fixing bugs,
implementing missing features, etc. So, now the code reached a functional
state and I've just merged the new-gnome-session branch in
[trunk](http://svn.gnome.org/svn/gnome-session/trunk). [Vincent
Untz](http://www.vuntz.net/journal/) and I will be working on making the
new code shine for [2.24](http://live.gnome.org/TwoPointTwentythree).

If you want to know the general ideas around the new gnome-session, read:

<http://live.gnome.org/SessionManagement/NewGnomeSession>

Most of the design and features described there are already implemented (if not
all).

If you want to know what's still missing and want to help us, read:

<http://live.gnome.org/SessionManagement/Todo>

The new gnome-session is fully compatible with current session clients
(GnomeClient and others) and no code changes are required on existing apps.
However, some simple changes are necessary on some basic components that run
during the session such as gnome-settings-daemon, gnome-panel, nautilus,
metacity, gnome-keyring, etc. I have most of the patches ready and I'll
be filing bugs for each component soon _(actually, I've made other
necessary changes in some modules during the 2.21/2.22 cycle
already)_.

Big thanks to Dan! This important move would not be possible without his
support and invaluable efforts.

There's still a lot to do during this development cycle.

**Testing and patches are more than welcome!**
