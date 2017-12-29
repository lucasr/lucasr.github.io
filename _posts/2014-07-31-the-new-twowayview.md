---
title: The new TwoWayView
date: 2014-07-31T11:33:17+00:00
layout: post
permalink: /2014/07/31/the-new-twowayview/
image: /wp-content/uploads/2014/07/twowayview.png
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
tags:
  - androiddev
  - androidl
  - mozilla
  - planet
  - recyclerview
  - twowayview
---
_What if writing custom view recycling layouts was a lot simpler?_ This
question stuck in my mind since I started writing Android apps a few years ago.

The lack of proper extension hooks in the _AbsListView_ API has been one of my
biggest pain points on Android. The community has come up with different layout
implementations that were largely based on _AbsListView_'s code but none of
them really solved the framework problem.

So a few months ago, I finally set to work on a new API for
[_TwoWayView_](https://github.com/lucasr/twoway-view/) that would provide a
framework for custom view recycling layouts. I had made some good
[progress](https://plus.google.com/+LucasRocha/posts/WBaryNqAHiy) but then
Google announced _RecyclerView_ at I/O and everything changed.

At first sight, _RecyclerView_ seemed to be an exact overlap with the new
_TwoWayView_ API. After some digging though, it became clear that
_RecyclerView_ was a superset of what I was working on. So I decided to embrace
_RecyclerView_ and rebuild _TwoWayView_ on top of it.

The new _TwoWayView_ is functional enough now. Time to get some early feedback.
This post covers the upcoming API and the general-purpose layout managers that
will ship with it.

## Creating your own layouts

_RecyclerView_ itself doesn't actually do much. It implements the fundamental
state handling around child views, touch events and adapter changes, then
delegates the actual behaviour to separate components—_LayoutManager_,
_ItemDecoration_, _ItemAnimator_, etc. This means that you still have
to write some non-trivial code to create your own layouts.

_LayoutManager_ is a low-level API. It simply gives you extension points to
handle scrolling and layout. For most layouts, the general structure of a
_LayoutManager_ implementation is going to be very similar—recycle views out of
parent bounds, add new views as the user scrolls, layout scrap list items, etc.

Wouldn't it be nice if you could implement _LayoutManagers_ with a higher-level
API that was more focused on the layout itself? Enter the new _TwoWayView_ API.

_TwoWayLayoutManager_<sup><a
href="https://github.com/lucasr/twoway-view/blob/master/core/src/main/java/org/lucasr/twowayview/TWAbsLayoutManager.java">code</a></sup>
is a simple API on top of _LayoutManager_ that does all the laborious work for
you so that you can focus on how the child views are measured, placed, and
detached from the _RecyclerView_.

To get a better idea of what the API looks like, have a look at these sample
layouts:
[SimpleListLayout](https://gist.github.com/lucasr/391fbcb04479ebbe838c) is a
list layout and
[GridAndListLayout](https://gist.github.com/lucasr/8ea1832239dcc5119e77) is a
more complex example where the first N items are laid out as a grid and the
remaining ones behave like a list. As you can see you only need to override a
couple of simple methods to create your own layouts.

## Built-in layouts

The new API is pretty nice but I also wanted to create a space for
collaboration around general-purpose layout managers. So far, Google has only
provided _LinearLayoutManager_. They might end up releasing a few more layouts
later this year but, for now, that is all we got.

{% include figure.html src="/wp-content/uploads/2014/07/layouts.png"
alt="Built-in layouts: List, Grid, Staggered Grid, and Spannable Grid"
caption="Built-in layouts: List, Grid, Staggered Grid, and Spannable Grid" %}

The new _TwoWayView_ ships with a collection of four built-in layouts: _List_,
_Grid_, _Staggered Grid_, and _Spannable Grid_.

These layouts support all _RecyclerView_ features: item animations,
decorations, scroll to position, smooth scroll to position, view state
saving, etc. They can all be scrolled vertically and horizontally—this is
the _TwoWayView_ project after all ;-)

You probably know how the _List_ and _Grid_ layouts work. _Staggered Grid_
arranges items with variable heights or widths into different columns or rows
according to its orientation.

_Spannable Grid_ is a grid layout with fixed-size cells that allows items to
span multiple columns and rows. You can define the column and row spans as
attributes in the child views as shown below.

```xml
<FrameLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:colSpan="2"
    app:rowSpan="3">
    ...
</FrameLayout>
```

## Utilities

The new _TwoWayView_ API will ship with a convenience view (_TwoWayView_) that
can take a _layoutManager_ XML attribute that points to a layout manager class.

```xml
<org.lucasr.twowayview.widget.TwoWayView
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:layoutManager="ListLayoutManager"/>
```

This way you can leverage the resource system to set layout manager depending
on device features and configuration via styles.

You can also use _ItemClickSupport_ to use _ListView_-style item (long) click
listeners. You can easily plug-in support for those in any _RecyclerView_ (see
[sample](https://gist.github.com/lucasr/e7417474278ca0dd7783)).

I'm also planning to create pluggable item decorations for dividers, item
spacing, list selectors, and more.

* * *

That's all for now! The API is still in flux and will probably go through a few
more iterations. The built-in layouts definitely need more testing.

You can help by filing (and fixing) bugs and giving feedback on the API. Maybe
try using the built-in layouts in your apps and see what happens?

I hope _TwoWayView_ becomes a productive collaboration space for _RecyclerView
extensions and layouts_.
[Contributions](https://github.com/lucasr/twoway-view/) are very welcome!
