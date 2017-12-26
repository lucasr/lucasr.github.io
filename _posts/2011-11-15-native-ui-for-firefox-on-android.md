---
id: 2579
title: Native UI for Firefox on Android
date: 2011-11-15T14:07:54+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2579
permalink: /2011/11/15/native-ui-for-firefox-on-android/
categories:
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - android
  - call for feedback
  - call for participation
  - community
  - contribution
  - contributors
  - design
  - feedback
  - fennec
  - firefox
  - Free Software
  - mozilla
  - native ui
  - performance
  - phone
  - qa
  - testing
  - ux
---
<img class="alignnone size-full wp-image-2600" src="http://lucasr.org/wp-content/uploads/2011/11/native.png" width="502" height="241" srcset="http://lucasr.org/wp-content/uploads/2011/11/native-300x144.png 300w, http://lucasr.org/wp-content/uploads/2011/11/native.png 502w" sizes="(max-width: 502px) 100vw, 502px" />

It's been a month since Johnathan [publicly
announced](http://groups.google.com/group/mozilla.dev.planning/browse_thread/thread/ff8d89bfa28383bb)
the native UI for Firefox on Android. So it's probably a good time to give
everyone a quick status update. In case you haven't heard about it yet, we are
re-implementing Fennec's UI using Android's native platform to be able to
deliver a much better performance and UX to our users on Android devices.

In terms of architecture, one of the key points of the native UI is to move
Gecko and XUL out of Firefox's startup path on Android. This way, the UI can
start up and respond to user interaction immediately while Gecko and XUL load
and run on a separate thread. The communication between Gecko and the native UI
then happens through a simple [message
system](https://wiki.mozilla.org/Fennec/NativeUI/Messages). This means we're
replacing [Electrolysis](https://wiki.mozilla.org/Electrolysis) with a lighter
architecture that brings similar benefits. For the curious, [Mark
Finkle](http://starkravingfinkle.org/blog/) wrote an [architecture
overview](https://wiki.mozilla.org/Fennec/NativeUI/Architecture_Overview) with
more details.

We're landing the new code on a separate repository called
"[birch](hg.mozilla.org/projects/birch)" which will eventually be merged in
[mozilla-central](http://hg.mozilla.org/mozilla-central/). Large parts of the
primary browser UI have already been implemented—AwesomeBar, tabs, bookmarking,
notification popups, addons manager, preferences, context menus, and
more. We also have a new panning/zooming implementation that is
extremely fast and smooth. The design team is bringing a new phone UI
for Firefox that is both beautiful and simpler. The new design is part
of a wider effort to streamline the Firefox UX on all platforms,
desktop and mobile.

This is all very exciting but there's still a lot to do to make it all
feature-complete, stable, and ready for users. If you want to help us with
feedback and testing, install the native UI's [nightly
build](http://ftp.mozilla.org/pub/mozilla.org/mobile/nightly/latest-birch-android/)
on your Android phone. Don't have an Android phone? Mozilla can give you one!
Have a look at our [Test Drivers program
page](https://wiki.mozilla.org/Mobile/Testdrivers_Program) for more
information.

It's key to Mozilla's mission to have a strong presence on the mobile web
space. We're working hard to make Firefox the most exciting mobile browser on
Android. Development is moving insanely fast and I can't wait to see the new UI
delivered to our users next year!
