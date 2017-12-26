---
id: 1970
title: Running Uninstalled
date: 2010-12-02T22:47:37+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=1970
permalink: /2010/12/02/running-uninstalled/
image: /wp-content/uploads/2010/12/uninstalled.jpg
categories:
  - General
  - GNOME
  - litl
  - Software
  - Archived
tags:
  - app
  - code
  - coding
  - GNOME
  - gnome shell
  - hacking
  - havoc pennington
  - icons
  - images
  - litl
  - planet
  - plugins
  - run
  - the board
  - translations
  - ui
  - uninstalled
---
Back in 2008, when we started writing the initial infrastructure for the
[litl](http://litl.com/) OS UI, [Havoc](http://ometer.com/) added a way to run
the whole thing using uninstalled files in the source tree. Back then, I was so
blindly used to the "make → make install → run" cycles that I didn't think this
would be especially useful. I was obviously wrong.

litl's UI shell is a relatively big component comprising our window and
compositing manager, UI shell, plugin framework, a few highly integrated
apps—online photos, video chat, settings, friends, etc—among other things.
Having to install all that for every change in the code would be time consuming
and utterly distracting.

I added support for uninstalled run in [The
Board](http://live.gnome.org/TheBoardProject) a few weeks ago. It's an separate
[executable](http://git.gnome.org/browse/the-board/tree/src/the-board-uninstalled.in)
that allows you to run the app using fonts, images, icons, plugins residing in
the source tree. The only missing part is being able to use uninstalled
translations from the source tree—any good ideas on how to do it? [GNOME
Shell](http://live.gnome.org/GnomeShell) also allows you to run it from source
tree inside Xephyr using a [wrapper
script](http://git.gnome.org/browse/gnome-shell/tree/src/gnome-shell.in).

The bottom line is: any step between a code change and running the software is
a distraction. If you can make your app run using only uninstalled files from
source tree, do it! This is especially important in complex code bases using
lots of different assets—icons, images, UI definition files, translations,
fonts, etc. This allows you to test your code changes without much hassle.
And it saves you precious time.
