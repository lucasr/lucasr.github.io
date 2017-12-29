---
title: Reader Mode in Firefox Mobile
date: 2012-06-21T13:32:33+00:00
layout: post
permalink: /2012/06/21/reader-mode-in-firefox-mobile/
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - announcement
  - browser
  - feature
  - fennec
  - firefox
  - Mobile
  - mozilla
  - nightly
  - planet
  - readability
  - reader
  - reader mode
  - release
---
It all started at the [Firefox Work
Week](http://www.flickr.com/photos/robceemoz/7113855919/) in Toronto back in
April. I managed to find some time during that rather busy week to build a
rough prototype of Firefox Mobile's [Reader
Mode](https://wiki.mozilla.org/Fennec/NativeUI/UserExperience/ReaderMode). I've
been able to focus on it in the last few weeks and it's now in good enough
shape for wider testing.

<p style="text-align: center;">
  <img src="/wp-content/uploads/2012/06/blog.png" width="500" height="239" />
</p>

Reader Mode is about bringing a smooth and beautiful reading experience to
Firefox Mobile. It removes all the clutter from web pages and shows you only
what you want to read in a minimalist UI. Here are a few things I'd like to
highlight about it.

### Read now or later

If the current page is convertible to Reader Mode, you'll see the reader icon
in the browser toolbar (see image below). If you tap on it, the current page
will be loaded in the Reader straight away. You can also add it to your Reading
List to read it later using the corresponding app menu item.

<p style="text-align: center;">
  <img src="/wp-content/uploads/2012/06/reader-button.png" width="500" height="67" />
</p>

### AwesomeBar integration

Your Reading List items will show up in the AwesomeBar results—just like any
bookmark or history item—making it super easy to find specific items. The
Reading List items will have a little reader indicator (see image below). The
Reading List shows up as a top-level folder in AwesomeBar's Bookmarks tab, if
you want to see the full list of items.

<p style="text-align: center;">
  <img src="/wp-content/uploads/2012/06/awesomebar-results.png" width="500" height="75" />
</p>

### Read your way

The Reader UI is minimal but very configurable. You can set the [color
scheme](http://www.flickr.com/photos/lucasrocha/7401989284/in/photostream/lightbox/)
(light, dark, and sepia), font size and margins the way you want through a
simple set of controls (see image above). We might be adding more options like
a toggle to show/hide images in the text.

<p style="text-align: center;">
  <img src="/wp-content/uploads/2012/06/style-toolbar.png" width="500" height="374" />
</p>

### Read any time

Once you add a page to your Reading List, it will be automatically made
available offline so that you don't need an internet connection to access your
Reading List on the go.

<p style="text-align: center;">
  <img src="/wp-content/uploads/2012/06/reading-list-folder.png" width="500" height="195" />
</p>

### Read anywhere

Your Reading List will be synced across all platforms where you use Firefox.
This means you'll be able to add a Reading List item in your Firefox on desktop
and read it on the go from your phone using Firefox Mobile. This is not
implemented yet as we need to have Reader Mode in desktop Firefox before we can
enable Reading List syncing there. So, at least for the initial release, the
Reader will only be available on mobile.

Firefox Mobile's Reader Mode is similar to existing reader apps. But, as you
can see, the real difference here is that it is deeply integrated in the
browser, where you usually read stuff anyway. As far as I know, Firefox is the
first mobile browser on Android to provide this feature.

Reader Mode is now enabled in the Nightly builds of Firefox for Android. It's
still a very early development version so expect bugs. Help with testing and
feedback is very welcome. [Download the Nightly](http://nightly.mozilla.org/)
and try it now!
