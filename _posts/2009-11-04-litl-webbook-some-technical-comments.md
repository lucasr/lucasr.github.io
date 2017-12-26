---
id: 332
title: 'litl webbook: some technical comments'
date: 2009-11-04T22:02:49+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/?p=332
permalink: /2009/11/04/litl-webbook-some-technical-comments/
categories:
  - Free Software
  - Gadget
  - General
  - GNOME
  - litl
  - Software
tags:
  - cache
  - clutter
  - gjs
  - GNOME
  - hacking
  - javascript
  - Job
  - litl
  - release
  - sync
  - ui
  - update system
  - webbook
---
<div id="attachment_516" style="width: 510px" class="wp-caption alignnone">
  <a href="http://litl.com"><img class="size-full wp-image-516 " src="http://www.lucasr.org/wp-content/uploads/2009/11/litl-team.jpg" width="500" height="203" /></a>
  <p class="wp-caption-text">
    The litl Team
  </p>
</div>

So, you've probably seen the news: [litl webbook](http://www.litl.com)
released! It's the result of heavy work of an awesome team! Our
[website](http://www.litl.com) has a lot of information about the product from
a user perspective, so I thought it would be nice to bring an overview of the
more technical aspects of the litl OS that I find specially interesting.
[Scott](http://cananian.livejournal.com/58744.html) has written some technical
notes about our OS too.

**Javascript.** Almost all UI code is written in javascript using our GObject
introspection-based binding called [gjs](http://live.gnome.org/Gjs) (using
SpiderMonkey engine). It was a quite interesting learning experience to write a
large amount of UI code in javascript. By the time we started, I think no one
in the team had any real experience with javascript. So, it took some time
until we all agreed on the javascript programming idioms (the flexibility of
the language may "cause" a lot of inconsistencies...) and on how to
better/correctly take advantage of its features. Most of what we agreed in
terms of coding style is in the gjs [style
guide](http://git.gnome.org/cgit/gjs/tree/doc/Style_Guide.txt). Doing stuff in
javascript (i.e. not doing the whole UI in C or any other insanity like this)
allowed us to prototype, refactor, rewrite things much faster. And that was
crucial for us because the ideas around the UI design changed a lot during
the first months of development and we ended up rewriting large chunks of
code several times on the way. Doing relatively large scale stuff in
javascript definitely requires very clear and strong guidelines in order to
keep the code base sane — maybe a bit more than usual.

**GNOME & FLOSS stuff.** The OS is heavily based on well-known open source
projects. Some facts: it's based on Ubuntu (with great support by Canonical)
and the UI is all written with GNOME platform and co. As I said, almost all
code is written in javascript using gjs. Most of the UI is Clutter-based. We
have our own specialized window and compositing manager that was implemented
with our use cases in mind. We're definitely one of the projects with the
largest Clutter-dependent code base. We use GTK+ in just a few places where we
needed more complex widgets (i.e. text entry). The web browser is Gecko-based
and it's pretty much implemented as a XUL app running in a separate process
than the OS chrome. We use Evince and Totem (as browser plugins), GStreamer,
Network Manager, and others. One interesting fact about our development
process is that, in the ~2 years of heavy hacking, we had to adapt to
major changes in the upstream projects we base our OS on. So, since we
started, we had to port our UI to Clutter 0.6, then 0.8, and finally 1.0;
had to port gjs to use the then-new GObject introspection scanner;
migrated from Network Manager 0.6 to 0.7; and maybe some other major
changes that I can't remember now. We contributed to those projects as
much as possible during the process.

**No storage, just caching.** You probably noticed that the device has "only"
2GB of storage. That won't sound strange if you see this from a "webbook
perspective". One of the ideas behind the product concept is that the
device serves as a much improved window to the web. In other words, the device
provides a simple and beautiful way to access web content — among other things.
So, we are pretty much only using storage for local caching. We don't really
store any real permanent data on the device. And that brings some interesting
challenges on how we implemented the OS. So we had to implement some smart ways
to cache as much content as possible and expire the right bits at the right
time so that the general experience is nice and smooth. Simple example: the OS
provides a way to access all your Flickr photos and videos (which can be **a
lot** of photos and videos btw) but we never permanently store anything
on disk. We cache things like rss feeds, profile pictures of your litl
contacts, a lot of your Flickr photos and videos, website favicons, installed
channels, etc. Each type of content may use a different way of expiring items
and all that needs to fit in the relatively small storage space we have. You
can guess how fun it was to hack on this. Hacking on syncing was even more fun
though :-)

**Syncing.** Another interesting aspect of the device is that each device is
connected to a litl account on our servers and all your stuff (browser cards,
channels, settings, contacts, etc) is always synced in our servers.
That means if you lose your device and get new one, you would just need to
connect your device to same account and all your stuff would be nicely
restored. Additionally, multiple devices can be associated to same account. In
that case, they will automatically share channels and other things. If you add
channel card in one, it will automatically appear on the other. We spent quite
some time working on our syncing infrastructure (client and server), dealing
some relatively complex problems — especially when dealing with making UI
immediately react to sync-related changes in the local and remote datastores.
The server side syncing stuff (and other server-side features) is implemented
with Google App Engine, some bits in Amazon S3 and Django.

**Seamless system updates.** The OS comes with a smart update system. No
package management involved. No user action needed to get system updates. In
practice, we download and install a new OS image and fetch your data again from
litl servers while the system is idle. The update system falls back to current
image in case something goes wrong with new OS images. The update system allows
us to keep updating, adding features, fixing bugs, and then push those updates
to our users in a burden-free way.

We had a lot of fun hacking on the litl webbook. It's always great to work in a
team full of very smart people. Definitely learnt a lot in the process. We
still have a lot of work to do of course but I already feel very proud of what
we've accomplished so far. Exciting times!

**Update:** Saying that the UI is 99,99% Clutter-based is not very accurate.
It's a bit less than that.
