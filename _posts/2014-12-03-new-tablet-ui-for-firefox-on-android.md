---
title: New tablet UI for Firefox on Android
date: 2014-12-03T21:45:22+00:00
layout: post
permalink: /2014/12/03/new-tablet-ui-for-firefox-on-android/
image: /wp-content/uploads/2014/12/tablet.png
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
tags:
  - androiddev
  - design
  - fennec
  - firefox
  - Free Software
  - goals
  - mozilla
  - planet
  - tablet
  - ui
  - ux
---
The new tablet UI for Firefox on Android is now available on
[Nightly](http://nightly.mozilla.org/) and, soon,
[Aurora](http://aurora.mozilla.org/)! Here's a quick overview of the design
goals, development process, and implementation.

### Design & Goals

Our main goal with the new tablet UI was to simplify the interaction with
tabs—read Yuan Wang's [blog
post](https://blog.mozilla.org/ux/2014/10/re-imagine-firefox-on-tablet/) for
more context on the design process.

In 36, we focused on getting a solid foundation in place with the core UI
changes. It features a brand new tab strip that allows you to create, remove
and switch tabs with a single tap, just like on Firefox on desktop.

The toolbar got revamped with a cleaner layout and simpler state changes.

{% include figure.html src="/wp-content/uploads/2014/12/Screenshot_2014-11-29-20-53-16.png"
caption="The new toolbar." %}

Furthermore, the fullscreen tab panel—accessible from the toolbar—gives you a
nice visual overview of your tabs and sets the stage for more advanced features
around tab management in future releases.

{% include figure.html src="/wp-content/uploads/2014/12/Screenshot_2014-11-29-20-51-55.png"
caption="Overview of your tabs." %}

### Development process

At Mozilla, we traditionally work on big features in a separate branch to avoid
disruptions in our 6-week development cycles. But that means we don't get
feedback until the feature lands in
[mozilla-central](https://hg.mozilla.org/mozilla-central/).

We took a slightly different approach in this project. It was a bit like
replacing parts of an airplane while it's flying.

We first worked on the necessary changes to allow the app to have parallel UI
implementations in a separate branch. We then merged the new code to
mozilla-central and did most of the UI development there.

This approach enabled us to get early feedback in
[Nightly](http://nightly.mozilla.org/) before the UI was considered
feature-complete.

### Implementation

In order to develop the new UI directly in mozilla-central, we had to come up
with a way to run either the old or the new tablet UIs in the same build.

We broke up our UI code behind interfaces with multiple concrete
implementations for each target UI, used view factories to dynamically
instantiate parts of the UI, prefixed overlapping resources, and more.

The new tab strip uses the latest stable release of
[TwoWayView](https://github.com/lucasr/twoway-view/) which got a bunch of
important bug fixes and couple of new features such as smooth scroll to
position.

Besides improving Firefox's UX on Android tablets, the new UI lays the
groundwork for some cool new features. This is not a final release yet and
we'll be landing bug fixes until 36 is out next year. But you can try it now in
our [Nightly](http://nightly.mozilla.org/) builds. Let us know what you think!
