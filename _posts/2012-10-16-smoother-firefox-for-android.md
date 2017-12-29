---
title: Smoother Firefox for Android
date: 2012-10-16T16:50:43+00:00
layout: post
permalink: /2012/10/16/smoother-firefox-for-android/
image: /wp-content/uploads/2012/10/smoother-fennec.jpg
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - animation
  - browser
  - call for feedback
  - fennec
  - firefox
  - Free Software
  - frontend
  - hacking
  - Mobile
  - planet
  - smoother
  - Software
  - tabs
  - ui
  - ux
---
Now that [Reader](http://lucasr.org/2012/06/21/reader-mode-in-firefox-mobile/)
[Mode](http://lucasr.org/2012/09/03/reader-mode-in-firefox-beta-for-android/)
has been released in [Firefox
16](https://play.google.com/store/apps/details?id=org.mozilla.firefox), my main
focus for the 18/19 releases will be about making the experience of using
Firefox for Android as smooth as possible. I'll initially focus on three areas:
tabs UX, Awesome Screen performance, and page load progress feedback.

This will probably be a continuous effort and it's unlikely that I'll be "done"
in just one cycle. The goal here is incrementally land changes that have clear
user-visible impact. I've already landed the first batch of improvements to the
tabs UX:

  * The slide animation to show/hide the tabs tray is now much smoother,
  especially on Android devices with hardware acceleration support (ICS or
  later).
  * The swipe-to-close gesture on the tabs tray is now much more polished and
  reliable (see image above).
  * Tabs now slide to fill the gap of removed tabs instead of just snapping to
  the new positions.
  * We now give more space to the tabs tray so you can see more tabs at once.
  * Tapping anywhere in the main UI (not only the web content area) should close the tabs tray.

These changes together add up to a much better UX already but there's more
coming, stay tuned! This week I'll be working on ways to make the Awesome
Screen feel more responsive. For now, you can see the improvements in the tabs
tray in action on our [Nightly builds](http://nightly.mozilla.org/). Feedback
is very welcome!
