---
id: 3236
title: Introducing Smoothie
date: 2013-01-06T23:48:43+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=3236
permalink: /2013/01/06/introducing-smoothie/
image: /wp-content/uploads/2013/01/smoothie.png
categories:
  - Android
  - Free Software
  - General
  - Software
tags:
  - abslistview
  - android
  - api
  - async
  - call for feedback
  - github
  - gridview
  - hacking
  - library
  - listview
  - loading
  - mozilla
  - pattrn
  - planet
  - scrolling
  - smoother
  - smoothie
---
A big part of [Pattrn'](http://pattrnapp.com)s UI is about scrolling through
lists of images from the cloud. So I spent a quite some time tuning it to
ensure that the scrolling experience is as smooth as possible. In the past few
weeks, I've been working on factoring out this code into a tiny library called
[Smoothie](https://github.com/lucasr/smoothie).

Smoothie provides a simple API to load _ListView_/_GridView_ items
asynchronously, off the UI thread. It does all the obvious things you'd
expect—loading items as they become visible, cancelling item requests for
recycled views, etc. But it does a bit more than that.

Smoothie is gesture-aware: it will avoid wasting item requests after a fling
gesture and enable incremental item loading while you scroll the list with
finger down. Furthermore, it supports offscreen item preloading to reduce the
number of placeholder-type items as you scroll. Under the hood, Smoothie uses a
thread pool executor backed by blocking queue with dynamic priorities.
Offscreen item requests will dynamically get higher priority as they become
visible on screen while scrolling.

So, how do you use it? It's easy:

  1. Add an
     _[AsyncListView](https://github.com/lucasr/smoothie/blob/master/library/src/org/lucasr/smoothie/AsyncListView.java)_
     or _[AsyncGridView](https://github.com/lucasr/smoothie/blob/master/library/src/org/lucasr/smoothie/AsyncGridView.java)_
     to your layout. They only add one extra setter method to their respective
     parent classes.
  2. Implement an
     _[ItemLoader](https://github.com/lucasr/smoothie/blob/master/library/src/org/lucasr/smoothie/ItemLoader.java)_
     with your app-specific logic for loading and displaying items. You'll have
     to override four methods: _getItemParams()_, _loadItem()_,
     _loadItemFromMemory()_, and _displayItem()_.
  3. Build an
     _[ItemManager](https://github.com/lucasr/smoothie/blob/master/library/src/org/lucasr/smoothie/ItemManager.java)_
     with your _ItemLoader_ and set it on the target _AsyncListView_ or
     _AsyncGridView_.

Think of Smoothie as a slim backbone for your _ListView_/_GridView_'s
asynchronous loading. You can easily hook up your own image loading/caching
framework in it. For instance, one of the sample apps implements an
[_ItemLoader_](https://github.com/lucasr/smoothie/blob/master/samples/bitmap-cache/src/org/lucasr/smoothie/samples/bitmapcache/PatternsListLoader.java)
backed by
[Android-BitmapCache](https://github.com/chrisbanes/Android-BitmapCache) with a
simple fade-in animation to display images.

Besides the API docs in the
[code](https://github.com/lucasr/smoothie/tree/master/library), have a look at
the [sample apps](https://github.com/lucasr/smoothie/tree/master/samples/) to
get a better idea of how to use the library. Keep in mind that the API is not
final yet. Feedback is very welcome! Enjoy!
