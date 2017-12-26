---
id: 2171
title: The Board in Distros
date: 2011-03-22T10:14:59+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2171
permalink: /2011/03/22/the-board-in-distros/
categories:
  - Free Software
  - General
  - GNOME
  - Software
  - Archived
tags:
  - community
  - distro
  - fedora
  - feedback
  - GNOME
  - gnome shell
  - live cd
  - natty
  - opensuse
  - packages
  - planet
  - review
  - the board
  - ubuntu
  - unity
---
<div style="width: 510px" class="wp-caption aligncenter">
  <a href="http://www.flickr.com/photos/lucasrocha/5449682752/"><img src="http://farm6.static.flickr.com/5253/5449682752_57fe98eb08.jpg" width="500" height="313" /></a>
  <p class="wp-caption-text">
    The Board in GNOME 3
  </p>
</div>

So far, testing [The Board](http://live.gnome.org/TheBoardProject) has been a
complicated matter because it involved messing with jhbuild, build
dependencies, compilation of a dozen of modules, etc. Those are fine for
developers but not really for the people who just want to try the app. Here's a
summary of the progress made on the creation of distro packages for The Board.

## Ubuntu

[Robert Ancell](http://bobthegnome.blogspot.com/) initially created a PPA for
The Board under the GNOME 3 team in Launchpad. Thanks Robert! I then fixed a
few remaining build issues on the package and created a separate [PPA for The
Board](https://launchpad.net/~the-board-team/+archive/dev-snapshots). It
contains packages for Natty. To install The Board, open a terminal and run:

`$ sudo add-apt-repository ppa:the-board-team/dev-snapshots<br />
$ sudo apt-get update<br />
$ sudo apt-get install the-board`

You have to enable Ubuntu's Universe repository. There are still a few issues
with running The Board in Unity—blurred icon on panel, no status icon, etc.
I'll have to talk with the Unity team to know how The Board can be better
integrated with Ubuntu's new UX.

## GNOME 3 Live CD

Thanks to the work of [Andrew Wafaa](http://wafaa.eu/), The Board packages are
available for openSUSE. [Frederic Crozat](http://blog.crozat.net/) then
integrated Andrew's packages into the [GNOME 3 Live
CD](http://gnome3.org/tryit.html). So it's now easy to try The Board while
having a sneak peak on GNOME Shell and other GNOME 3 goodies. As I said
[before](http://lucasr.org/2010/12/06/adding-to-the-board/), I'm still unsure
on how to nicely integrate the app with GNOME Shell. The use of GTK+ status
icon doesn't really fit GNOME Shell's UI design.

## Fedora

[Cosimo Cecchi](http://blogs.gnome.org/cosimoc/) has created Fedora Rawhide
packages which still need to be updated for the [latest
release](http://lucasr.org/2011/02/01/the-board-0-1-1/)
and [reviewed](https://bugzilla.redhat.com/show_bug.cgi?id=670127). It should
be available soon, I guess...

All in all, my hope is that those packages will allow more people to try The
Board with minimum hassle. Keep in mind that The Board is still under heavy
development and is not ready for end-users. For now, I'm looking forward to
getting feedback, bug reports, and patches from insightful early testers and
developers! For instance, Luc's [15 minute
review](https://bugzilla.gnome.org/show_bug.cgi?id=642696) is an excellent
example of the kind of feedback I'm looking for.
