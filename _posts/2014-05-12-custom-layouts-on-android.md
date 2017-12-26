---
id: 3920
title: Custom Layouts on Android
date: 2014-05-12T12:42:06+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=3920
permalink: /2014/05/12/custom-layouts-on-android/
image: /wp-content/uploads/2014/05/layouts-post.png
categories:
  - Android
  - Free Software
  - General
  - Software
tags:
  - androiddev
  - async
  - layout
  - measure
  - optimization
  - performance
  - planet
  - ui thread
---
If you ever built an Android app, you have definitely used some of the built-in
layouts available in the platform—_RelativeLayout_, _LinearLayout_,
_FrameLayout_, etc. They are our bread and butter for building Android
UIs.

The built-in layouts combined provide a powerful toolbox for implementing
complex UIs. But there will still be cases where the design of your app will
require you to implement custom layouts.

There are two main reasons to go custom. First, to make your UI more
efficient—by reducing the number of views and/or making faster layout
traversals. Second, when you are building UIs that are not naturally possible
to implement with stock widgets.

In this post, I will demonstrate four different ways of implementing custom
layouts and discuss their respective pros and cons: composite view, custom
composite view, flat custom view, and async custom views.

The code samples are available in my
[android-layout-samples](https://github.com/lucasr/android-layout-samples)
repo. This app implements the same UI with each technique discussed here and
uses [Picasso](http://square.github.io/picasso/) for image loading. The UI is a
simplified version of Twitter app's stream—no interactions, just the layouts.

Ok, let's start with the most common type of custom layout: _composite view_.

## Composite View

This is usually your starting point. _Composite views_ (also known as compound
views) are the easiest way of combining multiple views into a reusable
UI component. They are very simple to implement:

  1. Subclass one of the built-in layouts.
  2. Inflate a _merge_ layout in the constructor.
  3. Initialize members to point to inner views with _findViewById()_.
  4. Add your own APIs to query and update the view state.

_TweetCompositeView_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/widget/TweetCompositeView.java)
is a composite view. It subclasses _RelativeLayout_, inflates
_tweet\_composite\_layout.xml_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/res/layout/tweet_composite_view.xml)
into it, and exposes an _update()_ method to refresh its state in the
adapter[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/adapter/TweetsAdapter.java#L85).
Simple stuff.

## Custom Composite View

_TweetCompositeView_ will likely perform fairly well in most situations. But,
for sake of argument, suppose you want to reduce the
number of child views and make layout traversals a bit
more efficient.

Although composite views are simple to implement, using general-purpose layouts
has a cost—especially with complex containers like _LinearLayout_ and
_RelativeLayout_. As platform building blocks, they have to handle tons of
layout combinations and might have to measure child views multiple times in a
single traversal—_LinearLayout_'s _layout_weight_ being a common example.

You can greatly optimize your UI by implementing a custom logic for measuring
and positioning child views that is specially tailored for your app. This is
what I like to call a _custom composite view_.

A custom composite view is simply a composite view that overrides _onMeasure()_
and _onLayout()_. So, instead of subclassing an existing container like
_RelativeLayout_, you will be subclassing the more general _ViewGroup_.

_TweetLayoutView_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/widget/TweetLayoutView.java)
implements this technique. Note how it gets rid of the _LinearLayout_ from
_TweetComposiveView_ and avoids the use of _layout_weight_
altogether[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/res/layout/tweet_layout_view.xml).

The laborious work of figuring out what
[_MeasureSpec_](http://developer.android.com/reference/android/view/View.MeasureSpec.html)
to use on each child view is done by the ViewGroup's handy
[_measureChildWithMargins()_](http://developer.android.com/reference/android/view/ViewGroup.html#measureChildWithMargins%28android.view.View,%20int,%20int,%20int,%20int%29)
method—and
[_getChildMeasureSpec()_](http://developer.android.com/reference/android/view/ViewGroup.html#getChildMeasureSpec%28int,%20int,%20int%29)
under the hood.

_TweetLayoutView_ probably doesn't handle all possible layout combinations
correctly but it doesn't have to. It is absolutely fine to optimize custom
layouts for your specific needs. This allows you to write both simpler and more
efficient layout code for your app.

## Flat Custom View

As you can see, custom composite views are fairly simple to write using
_ViewGroup_ APIs. Most of the time, they will give you the performance your app
needs.

However, you might want to go further and optimize your layouts even more on
critical parts of your UI that are very dynamic e.g. _ListViews_, _ViewPager,_
etc. What about merging all _TweetLayoutView_ child views into a single custom
view to rule them all? That is what _flat custom views_ are about—see image
below.

<div id="attachment_3936" style="width: 1290px" class="wp-caption alignnone">
  <a href="http://lucasr.org/wp-content/uploads/2014/05/layouts.png"><img class="wp-image-3936 size-full" src="http://lucasr.org/wp-content/uploads/2014/05/layouts.png" alt="Custom Composite View (left) and Flat Custom View (right)" width="1280" height="439" srcset="http://lucasr.org/wp-content/uploads/2014/05/layouts-960x329.png 960w, http://lucasr.org/wp-content/uploads/2014/05/layouts-768x263.png 768w, http://lucasr.org/wp-content/uploads/2014/05/layouts-480x164.png 480w, http://lucasr.org/wp-content/uploads/2014/05/layouts.png 1280w" sizes="(max-width: 1280px) 100vw, 1280px" /></a>
  <p class="wp-caption-text">
    Custom Composite View (left) and Flat Custom View (right)
  </p>
</div>

A flat custom view is a fully custom view that measures, arranges, and draws
its inner elements. So you will be subclassing _View_ instead of _ViewGroup_.

If you are looking for real-world examples, enable the &#8220;show layout
bounds&#8221; developer option in your device and have a look at apps like
Twitter, GMail, and Pocket. They all use flat custom views in their listing
UIs.

The main benefit from using flat custom views is the great potential for flattening your view hierarchy, resulting in faster traversals and, potentially, a reduced memory footprint.

Flat custom views give you maximum freedom as they are literally a blank
canvas. But this comes at a price: you won't be able to use the feature-packed
stock widgets such as _TextView_ and _ImageView_. Yes, it is simple to [draw
text](http://developer.android.com/reference/android/graphics/Canvas.html#drawText%28java.lang.String,%20float,%20float,%20android.graphics.Paint%29)
on a _Canvas_ but what about
[ellipsizing](http://developer.android.com/reference/android/widget/TextView.html#setEllipsize%28android.text.TextUtils.TruncateAt%29)?
Yes, you can easily [draw a
bitmap](http://developer.android.com/reference/android/graphics/Canvas.html#drawBitmap%28int[],%20int,%20int,%20float,%20float,%20int,%20int,%20boolean,%20android.graphics.Paint%29)
but what about [scaling
modes](http://developer.android.com/reference/android/widget/ImageView.html#attr_android:scaleType)?
Same applies to touch events, accessibility, keyboard navigation, etc.

The bottom line is: with flat custom views,you will likely have to re-implement
features that you would get for free from the platform. So you should only
consider using them on core parts of your UI. For all other cases, just lean on
the platform with composite views, custom or not.

_TweetElementView_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/widget/TweetElementView.java)
is a flat custom view. To make it easier to implement it, I created a little
custom view framework called _UIElement_. You will find it in the
_canvas_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/tree/master/src/main/java/org/lucasr/layoutsamples/canvas)
package.

The _UIElement_ framework provides a measure/layout API which is analogous to
Android's. It contains headless versions of _TextView_ and _ImageView_ with
only the necessary features for this demo—see
_TextElement_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/canvas/TextElement.java)
and
_ImageElement_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/canvas/ImageElement.java)
respectively. It also has its own
inflater[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/canvas/UIElementInflater.java)
to instantiate _UIElements_ from layout resource
files[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/res/layout/tweet_element_view.xml).

Probably worth noting: the _UIElement_ framework is in a very early development
stage. Consider it a very rough sketch of something that might actually become
useful in the future.

You have probably noticed how simple _TweetElementView_ looks. This is because
the real code is all in
_TweetElement_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/widget/TweetElement.java)—with
_TweetElementView_ just acting as a
host[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/canvas/UIElementHost.java).

The layout code in _TweetElement_ is pretty much analogous to
_TweetLayoutView_'s. It handles Picasso requests
differently[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/widget/ImageElementTarget.java)
because it doesn't use _ImageViews_.

## Async Custom View

As we all know, the Android UI framework is
[single-threaded](http://developer.android.com/guide/components/processes-and-threads.html#Threads).
And this is for a good reason: UI toolkits are not your simplest piece of code.
Making them thread-safe and asynchronous would be an unworthy herculean effort.

This single-threaded nature leads to some fundamental limitations. It means,
for example, that you can't do layout traversals off main thread at
all—something that would be useful in very complex and dynamic UIs.

For example, if your app has complex items in a _ListView_ (like most social
        apps do), you will probably end up skipping frames while scrolling
because _ListView_ has to
measure[<sup>code</sup>](https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/widget/ListView.java#L1870)
and
layout[<sup>code</sup>](https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/widget/ListView.java#L1882)
each child view to account for their new content as they become visible. The
same issue applies to _GridViews_, _ViewPagers_, and the like.

Wouldn't it be nice if we could do a layout traversal on the child views that are not visible yet without blocking the main thread? This way, the _measure()_ and _layout()_ calls on child views would take no time when needed in the UI thread.

Enter _async custom view_, an experiment to allow layout passes to happen off main thread. This is inspired by the [async node framework](https://www.youtube.com/watch?v=TCuVxU07NWs&feature=youtu.be&t=33m43s) developed by the Paper team at Facebook.

Given that we can never ever touch the UI toolkit off main thread, we need an API that is able to measure/layout the contents of a view without being directly coupled to it. This is exactly what the _UIElement_ framework provides us.

_AsyncTweetView_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/async/AsyncTweetView.java) is an async custom view. It uses a thread-safe _AsyncTweetElement_[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/async/AsyncTweetElement.java) factory[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/async/AsyncTweetElementFactory.java) to define its contents. Off-screen _AsyncTweetElement_ instances are created, pre-measured, and cached in memory from a background thread using a [Smoothie](https://github.com/lucasr/smoothie) item loader[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/async/TweetsLayoutLoader.java).

I had to compromise the async behaviour a bit because there's no sane way of showing layout placeholders on list items with arbitrary heights i.e. you end up resizing them once the layout gets delivered asynchronously. So whenever an _AsyncTweetView_ is about to be displayed and it doesn't find a matching _AsyncTweetElement_ in memory, it will force its creation in the UI thread[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/async/AsyncTweetView.java#L46).

Furthermore, both the preloading logic and the memory cache expiration would need to be a lot smarter to ensure more layout cache hits in the UI thread. For instance, using a LRU cache[<sup>code</sup>](https://github.com/lucasr/android-layout-samples/blob/master/src/main/java/org/lucasr/layoutsamples/async/UIElementCache.java) here doesn't seem ideal.

Despite these limitations, the preliminary results from async custom views look very promising. I'll continue the explorations in this area by refining the _UIElement_ framework and using it in other kinds of UIs. Let's see where it goes.

**Wrapping up**

When it comes to layouts, the more custom you go, the less you'll be able to lean on the platform's proven components. So avoid premature optimization and only go fully custom on areas that will actually affect the perceived quality and performance of your app.

This is not a black-and-white decision though. Between stock widgets and fully custom views there's a wide spectrum of solutions—from simple composite views to the more complex async views. In practice, you'll usually end up combining more than one of the techniques demonstrated here.
