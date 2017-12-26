---
id: 3509
title: UI improvements in Firefox for Android
date: 2013-02-25T18:46:52+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=3509
permalink: /2013/02/25/ui-improvements-in-firefox-for-android/
image: /wp-content/uploads/2013/02/new-firefox-ui.png
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - android
  - call for feedback
  - community
  - design
  - firefox
  - flat
  - hacking
  - holo
  - mozilla
  - planet
  - tabs
  - twowayview
  - ui
  - ux
---
Now that we've landed all the major changes for our next UI iteration, it's
probably a good time to spread the word about it and get some more feedback.

The goals with these changes are: keeping a clear distinction between different
types of tabs; making better use of the screen real estate on different
form-factors and orientations; and being more compliant with Android's design
language. So, what's new?

## Tab types

With the introduction of private browsing support in Firefox 21—now in
Aurora—came the need for a clear distinction between regular and private tabs.
We've done two UI changes to accomplish that.

First of all, the tabs tray is now divided into sections for each type of
tab—regular, private, and remote—so that you always keep things separate and
organized. Furthermore, once you select a private tab, the main toolbar becomes
dark as a clear sign that you're in a different browsing mode.

## Two-way tabs tray

We now use a horizontal scrolling tabs tray whenever it improves our use of the
screen space. This is achieved with a
_TwoWayView_—[announced](http://lucasr.org/2013/02/21/introducing-twowayview/
"Introducing TwoWayView") a few days ago.

On phones, the tabs tray is vertical in portrait mode and horizontal in
landscape mode. On tablets, the tabs tray is a vertical scrolling side bar in
landscape mode and a horizontal strip in portrait mode. Small tablets (7" or
so) now share the exact same tabs UI than large tablets.

## Holo-ish

The Firefox UX team has been working on
[streamlining](http://madhava.com/egotism/archive/005060.html) the Firefox UI
across all platforms—both on desktop and mobile. The idea is that Firefox
should feel like the same product wherever you use it. Finding the right
balance between cross-platform design consistency and native platform
compliance can be tricky but I think we're getting there.

We've recently landed a new skin for Firefox for Android that is more aligned
with Android's Holo design language. Almost all textures and gradients were
replaced by flat colors giving a much lighter feel to the browser. I love it!

All these UI changes are now available in the
[Nightly](http://nightly.mozilla.org/) build. Give it a try and let us know
what you think—ideally in form of bug reports!
