---
title: Revamped UI in Firefox for Android
date: 2013-08-21T15:42:48+00:00
layout: post
permalink: /2013/08/21/revamped-ui-in-firefox-for-android/
image: /wp-content/uploads/2013/08/fig.png
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
  - development
  - feature
  - fennec
  - firefox
  - firefox for android
  - hacking
  - mozilla
  - nightly
  - planet
  - release
---
We have just landed the biggest UI change in [Firefox for
Android](https://play.google.com/store/apps/details?id=org.mozilla.firefox)
since our [first native
release](http://lucasr.org/2012/06/26/new-firefox-for-android-released/) back
in June last year. It took us about 3 months, 147 fixed bugs, and 250
changesets. Not bad!

We have completely redesigned and rewritten the Awesomescreen—where you search
bookmarks and browsing history when you tap on the URL toolbar—and the Start
Page—the one you see when you start the app. In terms of interaction, we're
essentially merging the Awesomescreen and the Start Page into a single UI with
swipable pages. This means the UI you'll see on startup is the same that you'll
see when you tap on the URL bar.

I really enjoyed working on this feature for a few reasons. First of all, it
was a _team_ effort. Everyone in the mobile front-end team (staff and
volunteers) contributed something to it.

Second, it was a nice opportunity to modernize and cleanup a large part of our
code base. Third, the new design feels more streamlined, cleaner, and lighter
throughout.

Last but not least, I really liked the way we approached the implementation
through a focused, gradual, and steady process using a separate repository
until we felt it was ready to merge. Implementing large features in a rolling
release process with relatively short development cycles can be quite
challenging.

The new UI is now available in our [Nightly
builds](http://nightly.mozilla.org/). Download, install, and let us know what
you think. There are definitely some rough edges here and there. In the next
few weeks, we'll be focused on getting it ready for Firefox 26. Enjoy!
