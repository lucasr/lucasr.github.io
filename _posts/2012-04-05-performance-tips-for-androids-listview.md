---
id: 2672
title: "Performance Tips for Android's ListView"
date: 2012-04-05T11:24:21+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2672
permalink: /2012/04/05/performance-tips-for-androids-listview/
categories:
  - Free Software
  - General
  - Mozilla
  - Software
tags:
  - adapterview
  - android
  - api
  - code
  - development
  - fennec
  - firefox
  - Free Software
  - hacking
  - java
  - layout
  - listview
  - mozilla
  - native
  - performance
  - planet
  - scrolling
  - Software
  - tips
---
I've been messing around with Android-based code for a few months now while
hacking on [Native Firefox for
Android](http://lucasr.org/2011/11/15/native-ui-for-firefox-on-android/) and
[Pattrn](https://play.google.com/store/apps/details?id=org.lucasr.pattrn). I
noticed that the performance tips for _ListViews_ are a bit scattered in
different sources. This post is an attempt to summarize the ones I found most
useful.

I'm assuming you're already familiar with _ListViews_ and understand the
framework around
[_AdapterViews_](http://developer.android.com/reference/android/widget/AdapterView.html).
I've added some Android source code pointers for the curious readers willing to
understand things a bit deeper.

## How it works

_ListView_ is designed for scalability and performance. In practice, this
essentially means:

  1. It tries to do as few view inflations as possible.
  2. It only paints and lays out children that are (or are about to become)
     visible on screen<sup><a
     href="https://github.com/android/platform_frameworks_base/blob/dcce1216b0066f3f9ed1b01a485684e8617e7ea4/core/java/android/widget/ListView.java#L1594">code</a></sup>.

The reason for 1 is simple: layout inflations are expensive operations<sup><a
href="https://github.com/android/platform_frameworks_base/blob/93dc642eaf48e3db58c4929df26283fbc5fd663f/core/java/android/view/LayoutInflater.java#L424">code</a></sup>.
Although layout files are compiled into binary form for more efficient
parsing<sup><a
href="https://github.com/android/platform_frameworks_base/blob/613989772f7d7f7317349568a4809bf08b942bd7/core/java/android/content/res/Resources.java#L2116">code</a></sup>,
inflations still involve going through a tree of special XML blocks<sup><a
href="https://github.com/android/platform_frameworks_base/blob/60201f2b4ee3fcf222310b5bf91d1d150470cab7/core/java/android/content/res/XmlBlock.java">code</a></sup>
and instantiating all respective views. _ListView_ solves this problem by
recycling<sup><a
href="https://github.com/android/platform_frameworks_base/blob/43ee0ab8777632cf171b598153fc2c427586d332/core/java/android/widget/AbsListView.java#L5764">code</a></sup>
non-visible views—called "ScrapViews" in Android's source code—as you pan
around. This means that developers can simply update the contents of recycled
views<sup><a
href="https://github.com/android/platform_frameworks_base/blob/43ee0ab8777632cf171b598153fc2c427586d332/core/java/android/widget/AbsListView.java#L2012">code</a></sup>
instead of inflating the layout of every single row—more on that later.

In order to implement 2, _ListView_ uses the view recycler to keep adding
recycled views below or above the current viewport and moving active views to a
recyclable pool as they move off-screen<sup><a
href="https://github.com/android/platform_frameworks_base/blob/dcce1216b0066f3f9ed1b01a485684e8617e7ea4/core/java/android/widget/ListView.java#L2884">code</a></sup>
while scrolling. This way _ListView_ only needs to keep enough views in memory
to fill its allocated space in the layout and some additional recyclable
views—even when your adapter has hundreds of items. It will fill the space with
rows in different ways—from top, from bottom, etc—depending on how the viewport
changed<sup><a
href="https://github.com/android/platform_frameworks_base/blob/dcce1216b0066f3f9ed1b01a485684e8617e7ea4/core/java/android/widget/ListView.java#L1594">code</a></sup>.
The image below visually summarizes what happens when you pan a _ListView_
down.

<p style="text-align: center;">
  <img class="size-full wp-image-2725 aligncenter" style="border: 0px none;" src="http://lucasr.org/wp-content/uploads/2012/04/listview1.png" width="537" height="267" srcset="http://lucasr.org/wp-content/uploads/2012/04/listview1-300x149.png 300w, http://lucasr.org/wp-content/uploads/2012/04/listview1.png 537w" sizes="(max-width: 537px) 100vw, 537px" />
</p>

With this framework in mind, let's move on to the tips. As you've seen above,
_ListView_ dynamically inflates and recycles tons of views when scrolling
so it's key to make your adapter's
[_getView()_](http://developer.android.com/reference/android/widget/Adapter.html#getView%28int,%20android.view.View,%20android.view.ViewGroup%29)
as lightweight as possible. All tips resolve around making _getView()_
faster in one way or another.

## View recycling

Every time _ListView_ needs to show a new row on screen, it will call the
_getView()_ method from its adapter. As you know, _getView()_ takes three
arguments arguments: the row position, a _convertView_, and the parent
_ViewGroup_.

The _convertView_ argument is essentially a "ScrapView" as described earlier.
It will have a non-null value when _ListView_ is asking you recycle the row
layout. So, when _convertView_ is not null, you should simply update its
contents instead of inflating a new row layout. The _getView()_ code in your
adapter would look a bit like:

<pre style="font-size: smaller;">public View getView(int position, View convertView, ViewGroup parent) {
    if (convertView == null) {
        convertView = mInflater.inflate(R.layout.your_layout, null);
    }

    TextView text = (TextView) convertView.findViewById(R.id.text);
    text.setText("Position " + position);

    return convertView;
}</pre>

## View Holder pattern

Finding an inner view inside an inflated layout is among the most common
operations in Android. This is usually done through a _View_ method called
[_findViewById()_](http://developer.android.com/reference/android/view/View.html#findViewById%28int%29).
This method will recursively go through the view tree looking for a child with
a given ID<sup><a
href="https://github.com/android/platform_frameworks_base/blob/f93bb6d8fd81d8938b16cf40259f97c336e9ef3a/core/java/android/view/ViewGroup.java#L3059">code</a></sup>.
Using _findViewById()_ on static UI layouts is totally fine but, as you've
seen, _ListView_ calls the adapter's _getView()_ very frequently when
scrolling. _findViewById()_ might perceivably hit scrolling performance in
_ListViews_—especially if your row layout is non-trivial.

The View Holder pattern is about reducing the number of _findViewById()_ calls
in the adapter's _getView()_. In practice, the View Holder is a lightweight
inner class that holds direct references to all inner views from a row. You
store it as a
[tag](http://developer.android.com/reference/android/view/View.html#setTag%28int,%20java.lang.Object%29)
in the row's view after inflating it. This way you'll only have to use
_findViewById()_ when you first create the layout. Here's the previous code
sample with View Holder pattern applied:

<pre style="font-size: smaller;">public View getView(int position, View convertView, ViewGroup parent) {
    ViewHolder holder;

    if (convertView == null) {
        convertView = mInflater.inflate(R.layout.your_layout, null);

        holder = new ViewHolder();
        holder.text = (TextView) convertView.findViewById(R.id.text);

        convertView.setTag(holder);
    } else {
        holder = convertView.getTag();
    }

    holder.text.setText("Position " + position);

    return convertView;
}

private static class ViewHolder {
    public TextView text;
}</pre>

## Async loading

Very often Android apps show richer content in each _ListView_ row such as
images. Using [drawable
resources](http://developer.android.com/guide/topics/resources/drawable-resource.html)
in your adapter's _getView()_ is usually fine as Android caches those
internally<sup><a
href="https://github.com/android/platform_frameworks_base/blob/613989772f7d7f7317349568a4809bf08b942bd7/core/java/android/content/res/Resources.java#L1880">code</a></sup>.
But you might want to show more dynamic content—coming from local disk or
internet—such as thumbnails, profile pictures, etc. In that case, you probably
don't want to load them directly in your adapter's _getView()_ because, well,
you should [never ever block UI thread with
IO](http://blog.ometer.com/2008/09/07/synchronous-io-never-ok/). Doing so
means that scrolling your _ListView_ would look anything but smooth.

What you want to do is running all per-row IO or any heavy CPU-bound routine
asynchronously in a separate thread. The trick here is to do that and still
comply with _ListView_&#8216;s recycling behaviour. For instance, if you run an
_[AsyncTask](http://developer.android.com/reference/android/os/AsyncTask.html)_
to load a profile picture in the adapter's _getView()_, the view you're loading
the image for might be recycled for another position before the _AsyncTask_
finishes. So, you need a mechanism to know if the view hasn't been recycled
once you're done with the async operation.

One simple way to achieve this is to attach some piece of information to the
view that identifies which row is associated with it. Then you can check if the
target row for the view is still the same when the async operation finishes.
There are many ways of achieving this. Here is just a simplistic sketch of one
way you could do it:

<pre style="font-size: smaller;">public View getView(int position, View convertView,
        ViewGroup parent) {
    ViewHolder holder;

    ...

    holder.position = position;

    new ThumbnailTask(position, holder)
            .executeOnExecutor(AsyncTask.THREAD_POOL_EXECUTOR, null);

    return convertView;
}

private static class ThumbnailTask extends AsyncTask {
    private int mPosition;
    private ViewHolder mHolder;

    public ThumbnailTask(int position, ViewHolder holder) {
        mPosition = position;
        mHolder = holder;
    }

    @Override
    protected Cursor doInBackground(Void... arg0) {
        // Download bitmap here
    }

    @Override
    protected void onPostExecute(Bitmap bitmap) {
        if (mHolder.position == mPosition) {
            mHolder.thumbnail.setImageBitmap(bitmap);
        }
    }
}

private static class ViewHolder {
    public ImageView thumbnail;
    public int position;
}</pre>

## Interaction awareness

Asynchronously loading heavier assets for each row is an important step to
towards a performant _ListView_. But if you blindly start an asynchronous
operation on every _getView()_ call while scrolling, you'd be wasting a lot of
resources as most of the results would be discarded due to rows being recycled
very often.

We need to add interaction awareness to your _ListView_ adapter so that it
doesn't trigger any asynchronous operation per row after, say, a fling gesture
on the _ListView_—which means that the scrolling is so fast that it doesn't
make sense to even start any asynchronous operation. Once scrolling stops, or
is about to stop, is when you want to start actually showing the heavy content
for each row.

I won't post a code sample for this—as it involves too much code to post
here—but the classic [Shelves app](http://code.google.com/p/shelves/) by Romain
Guy has a pretty [good
example](http://code.google.com/p/shelves/source/browse/trunk/Shelves/src/org/curiouscreature/android/shelves/activity/ShelvesActivity.java).
It basically triggers the async book cover loading once the _GridView_ stops
scrolling among other things. You can also balance interaction awareness with
an in-memory cache so that you show cached content even while scrolling. You
got the idea.

## That's all!

I strongly recommend watching Romain Guy and Adam Powell's
[talk](http://www.youtube.com/watch?v=wDBM6wVEO70) about _ListView_ as it
covers a lot of the stuff I wrote about here. Have a look at
[Pattrn](https://play.google.com/store/apps/details?id=org.lucasr.pattrn) if
you want to see these tips in action. There's nothing new about the tips in
this post but I thought it would be useful to document them all in one place.
Hopefully, it will be a useful reference for hackers getting started on Android
development.

**Quick update.** I've just announced
[Smoothie](http://lucasr.org/2013/01/06/introducing-smoothie/), a tiny library
that that offers an easy way to do async loading in _ListViews_/_GridViews_. It
incorporates most of the tips described in this blog post behind a very simple
API. Have a look!
