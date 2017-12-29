---
title: Introducing TwoWayView
date: 2013-02-21T14:47:33+00:00
layout: post
permalink: /2013/02/21/introducing-twowayview/
image: /wp-content/uploads/2013/02/twowayview.png
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
tags:
  - abslistview
  - adapterview
  - android
  - announcement
  - fennec
  - firefox
  - hacking
  - listview
  - mozilla
  - planet
  - scrolling
  - twowayview
  - view
  - widget
---
We've been working hard on a new iteration of the tabs UI for Firefox for
Android. The new UI includes a horizontal scrolling tabs tray to make better
use of the screen real estate on phones and tablets in different orientations.

Unfortunately, the Android platform doesn't provide any
[AdapterView](http://developer.android.com/reference/android/widget/AdapterView.html)
with horizontal scrolling support nor could I find any non-naive open source
implementation out there.  Enter
[TwoWayView](https://github.com/lucasr/twoway-view).

_TwoWayView_ is an _AdapterView_ that can be scrolled either vertically or
horizontally. Just set the orientation of the view and it will do the right
thing for you. In its current state, it supports all the usual _AdapterView_
APIs (selection handling, adapter, item click and long click listener, etc),
view recycling, list selector, choice mode (single and multiple), edge
glow, and scrollbars. Have a look at the [sample
app](https://github.com/lucasr/twoway-view/tree/master/sample) to see it
in action.

The code is based on various bits and pieces of Android's _AdapterView_,
_AbsListView,_ and _ListView_. It uses the necessary wrappers from
Android's Support Library in order to keep backwards compatibility.

The big missing features right now are focus handling, keyboard navigation, and
accessibility. I'll be working on those in the next few weeks besides all the
necessary bug fixes—I don't recommend using _TwoWayView_ on production code
just yet.

For now, feedback, bug reports, and patches are very welcome! Enjoy!
