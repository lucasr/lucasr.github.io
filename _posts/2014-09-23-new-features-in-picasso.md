---
title: New Features in Picasso
date: 2014-09-23T15:52:54+00:00
layout: post
permalink: /2014/09/23/new-features-in-picasso/
image: /wp-content/uploads/2014/09/picasso.png
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
tags:
  - mozilla
  - planet
---
I've always been a big fan of [Picasso](https://github.com/square/picasso/),
the Android image loading library by the Square folks. It provides some
powerful features with a rather simple API.

Recently, I started working on a set of new features for Picasso that will make
it even more awesome: request handlers, request management, and request
priorities. These features have all been merged to the main repo now. Let me
give you a quick overview of what they enable you to do.

### Request Handlers

Picasso supports a wide variety of image sources, from simple resources to
content providers, network, and more. Sometimes though, you need to load images
in unconventional ways that are not supported by default in Picasso.

Wouldn't it be nice if you could easily integrate your custom image loading
logic with Picasso? That's what the new [request
handlers](https://github.com/square/picasso/pull/512) are about. All you need
to do is subclass _RequestHandler_ and implement a couple of methods. For
example:

```java
public class PonyRequestHandler extends RequestHandler {
    private static final String PONY_SCHEME = "pony";

    @Override public boolean canHandleRequest(Request data) {
        return PONY_SCHEME.equals(data.uri.getScheme());
    }

    @Override public Result load(Request data) {
         return new Result(somePonyBitmap, MEMORY);
    }
}
```

Then you register your request handler when instantiating Picasso:

```java
Picasso picasso = new Picasso.Builder(context)
    .addRequestHandler(new PonyHandler())
    .build();
```

_Voilà_! Now Picasso can handle pony URIs:

```java
picasso.load("pony://somePonyName")
       .into(someImageView)
```

This pull request also involved rewriting all built-in bitmap loaders on top of
the new API. This means you can also override the built-in request handlers if
you need to.

### Request Management

Even though Picasso handles view recycling, it does so in an inefficient way.
For instance, if you do a fling gesture on a _ListView_, Picasso will keep
triggering and canceling requests blindly because there was no way to make it
pause/resume requests according to the user interaction. Not anymore!

The new [request management APIs](https://github.com/square/picasso/pull/665)
allow you to tag associated requests that should be managed together. You can
then pause, resume, or cancel requests associated with specific tags. The first
thing you have to do is tag your requests as follows:

```java
Picasso.with(context)
       .load("http://example.com/image.jpg")
       .tag(someTag)
       .into(someImageView);
```

Then you can pause and resume requests with this tag based on, say, the scroll
state of a _ListView_. For example, Picasso's sample app now has the following
scroll listener:

```java
public class SampleScrollListener implements AbsListView.OnScrollListener {
    ...
    @Override
    public void onScrollStateChanged(AbsListView view, int scrollState) {
      Picasso picasso = Picasso.with(context);
      if (scrollState == SCROLL_STATE_IDLE ||
        scrollState == SCROLL_STATE_TOUCH_SCROLL) {
        picasso.resumeTag(someTag);
      } else {
        picasso.pauseTag(someTag);
      }
    }
    ...
}
```

These APIs give you a much finer control over your image requests. The scroll
listener is just the canonical use case.

### Request Priorities

It's very common for images in your Android UI to have different priorities.
For instance, you may want to give higher priority to the big hero image in
your activity in relation to other secondary images in the same screen.

Up until now, there was no way to hint Picasso about the relative priorities
between images. The new [priority
API](https://github.com/square/picasso/pull/666) allows you to tell Picasso
about the intended order of your image requests. You can just do:

```java
Picasso.with(context)
       .load("http://example.com/image.jpg")
       .priority(HIGH)
       .into(someImageView);
```

These priorities don't guarantee a specific order, they just tilt the balance
in favour of higher-priority requests.

* * *

That's all for now. Big thanks to Jake Wharton and Dimitris Koutsogiorgas for
the prompt code and API reviews!

You can try these new APIs now by fetching the [latest Picasso
code](https://github.com/square/picasso/) on Github. These features will
probably be available in the 2.4 release. Enjoy!
