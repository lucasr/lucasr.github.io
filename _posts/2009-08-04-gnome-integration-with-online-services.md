---
id: 314
title: GNOME Integration with Online Services
date: 2009-08-04T02:40:32+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/?p=314
permalink: /2009/08/04/gnome-integration-with-online-services/
categories:
  - General
  - GNOME
  - Archived
---
<div style="width: 510px" class="wp-caption alignnone">
  <a href="http://live.gnome.org/OnlineIntegration"><img src="http://farm4.static.flickr.com/3302/3526804232_3c4f690ff8.jpg" width="500" height="333" /></a>
  <p class="wp-caption-text">
    Keukenhof
  </p>
</div>

While deciding about [libgdata](http://live.gnome.org/libgdata) [inclusion in
GNOME
2.28](http://mail.gnome.org/archives/devel-announce-list/2009-July/msg00005.html),
we (Release Team) somehow considered it didn't make much sense to have
libgdata in the desktop suite. So, one thing that came to my mind was that we
need some space to aggregate development efforts aiming to integrate online
social services in GNOME. Also, it seems that we need to highlight those
modules in a more clear way as it seems that just a few people are aware of
those GNOME-based technologies. In order to get "something" started
before I forget it, I created this wiki page:

<http://live.gnome.org/OnlineIntegration>

I tried to include all the cool modules I know about that aim to integrate with
online social services in some way: from instant messaging to maps, from Google
apps to CouchDB. I tried to draft some proposed guidelines for the modules so
that we can (maybe) define cross-module goals in the short-term. Providing
GObject Introspection support could be one. Proving new plugins to Mojito could
be another. Or maybe covering more online services. My impression is that
Mojito brings a nice way to integrate data from different social services
behind a simple API. Maybe a mid-term goal could be to thing about ways to
integration online services in GNOME Shell?

Anyway, comments and suggestions are welcome!
