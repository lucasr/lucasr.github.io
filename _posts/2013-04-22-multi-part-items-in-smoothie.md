---
id: 3628
title: Multi-part items in Smoothie
date: 2013-04-22T11:51:24+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=3628
permalink: /2013/04/22/multi-part-items-in-smoothie/
image: /wp-content/uploads/2013/04/multipart.png
categories:
  - Android
  - Free Software
  - General
  - Software
tags:
  - adapterview
  - android
  - androiddev
  - announcement
  - async
  - call for participation
  - call for testing
  - feature
  - Free Software
  - gridview
  - library
  - listview
  - mozilla
  - open source
  - planet
  - smoothie
---
[Smoothie](http://lucasr.org/2013/01/06/introducing-smoothie/ "Introducing
Smoothie") makes it really easy to load _ListView_/_GridView_ items
asynchronously, off the UI thread. It handles all the complexity from gestures,
threads, scrolling state, preloading, and view recycling behind a simple
API.

Up until now, one of the biggest limitations of the Smoothie API has been the
lack of proper support for multi-part items. What is a multi-part item? It's a
_ListView_/_GridView_ item composed by multiple parts that have to be loaded
asynchronously with different priorities as you scroll.

Classic example: a list of photos with items composed by the photo image and
the author's avatar—both loaded from the cloud. With the existing API, 
Smoothie would force you to load the whole content of each item in one go. This
means you were forced to load both the main photo image and the avatar image
for each item before loading the next item in the list.

What if you wanted to start loading the main photo image of all visible items
before loading their respective avatars? The photos are probably the content
your users are actually interested in after all. That's what the multi-part
item support is about. It allows you to split the loading of each item into
multiple asynchronous operations with different global priorities.

So, how would you implement the above example assigning higher priority to the
main photo image over the avatar using Smoothie? Assuming you're already
familiar with Smoothie's API, just follow these steps:

  1. Override the _getItemPartCount()_ method from _ItemLoader._ Return the
     number of parts the item in the given Adapter position has.
  2. Handle the new _itemPart_ argument accordingly in
     _loadItemPartFromMemory()_, _loadItemPart()_, and _displayItemPart()._
     These methods will be called once for each item part.

The item parts will have indexes starting from zero. e.g. for items with 2
parts, the part indexes will be 0 and 1. The indexes also define the relative
priority between parts. _Smoothie_ will load the part with index 0 for all
visible items before loading part with index 1.

**Important note:** I had to break API backwards compatibility. If you don't
really need multi-part items, the only change you'll have to make in your code
is to subclass from _SimpleItemLoader_ instead of _ItemLoader.
SimpleItemLoader_ is an _ItemLoader_ specialized in single-part items that
hides all the part-related bits from the API.

The [updated
documentation](https://github.com/lucasr/smoothie/blob/master/library/src/org/lucasr/smoothie/ItemLoader.java)
contains code samples and a more detailed overview of the new API. Grab the
[latest code](https://github.com/lucasr/smoothie) while it's hot. Feedback, bug
reports, and patches are all very welcome as usual.
