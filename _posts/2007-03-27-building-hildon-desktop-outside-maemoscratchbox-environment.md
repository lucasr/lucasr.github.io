---
id: 126
title: Building Hildon Desktop outside Maemo/Scratchbox environment
date: 2007-03-27T09:34:09+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/03/27/building-hildon-desktop-outside-maemoscratchbox-environment/
permalink: /2007/03/27/building-hildon-desktop-outside-maemoscratchbox-environment/
categories:
  - Free Software
  - General
  - GNOME
  - Maemo
  - Archived
tags:
  - hacking
  - Hildon
  - hildon desktop
  - Maemo
  - nokia
  - plugin
  - portability
  - python
  - scratchbox
---
I wrote a step-by-step guide to have [Hildon
Desktop](https://stage.maemo.org/svn/maemo/projects/haf/trunk/hildon-desktop/)
running outside the Maemo/Scratchbox environment. Our major goal here is to
make it easy for distributons to package Hildon Desktop so that developers can
have a quick-to-setup environment for the development of plugins which doesn't
need to be built against ARM such as Python plugins. For now, this guide only
applies to Ubuntu _(If you can point out the changes needed to work on another
distribution, please let me know)_. This is a call for testers and
brave developers to follow the guide and report the missing/problematic bits.

<http://maemo.org/maemowiki/HildonDesktopPortability>

There are some issues that still block us from getting Hildon Desktop in a
distribution but we're working on that.
