---
id: 2849
title: Native Firefox for Android Beta
date: 2012-05-21T16:50:27+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2849
permalink: /2012/05/21/native-firefox-for-android-beta/
categories:
  - Android
  - Free Software
  - Gadget
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - android
  - beta
  - compositor
  - content provider
  - development
  - fennec
  - firefox
  - graphics
  - hacking
  - mozilla
  - panning
  - performance
  - planet
  - release
  - rendering
  - sync
  - zooming
---
[<img class="alignnone size-full wp-image-2850" title="" src="http://lucasr.org/wp-content/uploads/2012/05/ff-beta.png" width="500" height="309" srcset="http://lucasr.org/wp-content/uploads/2012/05/ff-beta-300x185.png 300w, http://lucasr.org/wp-content/uploads/2012/05/ff-beta.png 500w" sizes="(max-width: 500px) 100vw, 500px" />](https://play.google.com/store/apps/details?id=org.mozilla.firefox_beta)

At this point, you have probably heard the
[news](http://blog.mozilla.org/futurereleases/2012/05/15/new-firefox-for-android-beta-is-ready-for-testing/).
Yes, we've release the first public Beta of Firefox for Android with all the
goodness that we've been working on in the last 7 months: the brand new native
UI that is lighter, faster, and sleeker. Here are some big picture highlights
about this Beta.

## Design direction

The new native UI design is part of a wider effort in Mozilla to streamline the
visual identity of Firefox across multiple platforms—desktop and mobile.
Firefox should feel like one consistent product everywhere. Have a look at
Madhava's [slide deck](http://madhava.com/egotism/archive/005060.html) for more
information on what the Firefox design team has been up to lately.

Keep in mind that this first native UI release is just the first of many
iterations. For instance, there's a lot of interesting changes coming up as
part of our work on the [native tablet
UI](http://www.flickr.com/photos/61892693@N03/sets/72157629634831895/) that
will eventually trickle down to the [phone
UI](http://www.flickr.com/photos/61892693@N03/sets/72157629270239482/) as well.

## Panning and zooming

If you're using the Beta already (or have been using the Nightly or Aurora
builds) you'll notice how smoother panning and zooming are. This is
because the Beta features a major revamp on the graphics and rendering
infrastructure using tiled rendering and an off-main-thread layer compositor. I
recommend reading [Benoit
Girard](http://benoitgirard.wordpress.com/2012/05/15/off-main-thread-compositing-omtc-and-why-it-matters/)'s
and [Chris
Lord](http://chrislord.net/blog/Software/Mozilla/mobile-platform-at-fxto2012.enlighten)'s
blog posts for further details. It's worth mentioning that the Mobile Platform
and Graphics teams did an amazing work to implement all this in a rather short
period!

## Places and Sync

The [Places](https://wiki.mozilla.org/Places) database has been re-implemented
in Firefox for Android as a private [Content
Provider](http://developer.android.com/guide/topics/providers/content-providers.html)
for two reasons. First of all, it gives instant access to history and bookmarks
even before Gecko is up i.e. much faster startup experience. Secondly, it
allows the new native Firefox Sync—which is now nicely integrated with the
system's sync UI—to access your browsing history and bookmarks even when
Firefox is not running.

We've already started working on new features for the following releases
including the native UI for Firefox on Android tablets and a [reader
mode](https://wiki.mozilla.org/Fennec/NativeUI/UserExperience/ReaderMode). As
you can see, the upcoming Firefox for Android is a whole new beast. We are
working hard to make it the best mobile browser out there. You can help us now
testing the Beta as part of our [Mobile Test Drivers
Program](https://wiki.mozilla.org/Mobile/Testdrivers_Program)!

With the native UI, we're creating a new baseline for innovation on Firefox
Mobile. And it will only get better from now on. What are you waiting for?
Download the [Firefox for Android
Beta](https://play.google.com/store/apps/details?id=org.mozilla.firefox_beta)
now!
