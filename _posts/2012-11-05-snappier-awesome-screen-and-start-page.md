---
title: Snappier Awesome Screen and Start Page
date: 2012-11-05T17:25:02+00:00
layout: post
permalink: /2012/11/05/snappier-awesome-screen-and-start-page/
image: /wp-content/uploads/2012/11/snappier.jpg
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - android
  - benchmarks
  - call for feedback
  - fennec
  - firefox
  - hacking
  - mozilla
  - performance
  - planet
  - smoother
  - snappy
  - ux
---
As part of [my
effort](http://lucasr.org/2012/10/16/smoother-firefox-for-android/) to make the
Firefox for Android smoother, I've spent the last week or so improving the
performance of the Start Page and the Awesome Screen. So, what's the issue I'm
trying fix here? In one word: latency.

Our telemetry data shows that Firefox for Android is taking several seconds—up
to 10!—to show the top sites in the Start Page. This means our users are
staring at a blank page for several seconds on startup. We've been getting
similar reports about the time to show the initial list of sites on the Awesome
Screen. Both the Start Page and Awesome Screen use the same frecency query.

After some investigation, it seems that one of the main reasons for the
frecency query to be so slow right now is that we fetch images (favicons or
thumbnails) in the query itself. i.e. we're reading lots of binary
blobs from the disk as part of the query. This can be very slow on mobile
devices—especially with thumbnails which are much larger images than favicons.

To address that, I've recently landed patches that change the Start Page and
the Awesome Screen to first fetch the list of sites (URL and title) then load
their respective images asynchronously. So, how much faster did they get?

The results of my local (non-scientific) benchmarks look very promising! With
these patches, the Start Page takes about 33% less time to show top sites and
the Awesome Screen takes 36% less time to show the initial list of sites—in a
medium-size history and bookmarks database.

The corresponding telemetry data is already trending towards saner performance
results but I'll have to wait for a larger data sample from users on the latest
Nightly to see how much we're actually improving. I'm keen to hear how much
difference these patches made on your [Nightly](http://nightly.mozilla.org/)
experience. Feedback is welcome!
