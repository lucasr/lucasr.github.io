---
id: 202
title: Context-sensitive menus
date: 2008-03-16T13:39:45+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2008/03/16/context-sensitive-menus/
permalink: /2008/03/16/context-sensitive-menus/
categories:
  - General
  - GNOME
  - Archived
tags:
  - bug
  - context-sensitive
  - GNOME
  - idea
  - menu
  - ui
---
I was just wondering why do we show disabled menu items in a context-sensitive
menu? In this case, showing disabled operations to the user doesn't bring any
useful information. For example, have a look at this context-sensitive menu for
a mounted USB stick in the Nautilus desktop area (see [bug
522739](http://bugzilla.gnome.org/show_bug.cgi?id=522739)):

![context-menu.png](http://www.lucasr.org/wp-content/uploads/2008/03/context-menu.png)

What's the point of showing all those disabled items? If it's a
**context-sensitive** menu, it should show only actions that make sense it that
context, right?

I see the point of having disabled menu items in a main menubar for the sake of
bringing awereness of all available actions in an application. However, for
context-sensitive menus, it just doesn't make any sense. Am I missing
something?
