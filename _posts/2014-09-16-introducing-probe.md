---
id: 4000
title: Introducing Probe
date: 2014-09-16T10:32:49+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=4000
permalink: /2014/09/16/introducing-probe/
image: /wp-content/uploads/2014/09/probe.png
categories:
  - Android
  - Free Software
  - General
  - Software
tags:
  - android
  - androiddev
  - bounds
  - layout
  - Mobile
  - mozilla
  - overmeasure
  - performance
  - planet
  - probe
  - toolkit
  - traversal
---
We&#8217;ve all heard of the best practices regarding layouts on Android: keep your view tree as simple as possible, avoid multi-pass layouts high up in the hierarchy, etc. But the truth is, it&#8217;s pretty hard to _see_ what&#8217;s actually going on in your view tree in each UI traversal (measure → layout → draw).

We&#8217;re well served with developer options for tracking graphics performance—debug GPU overdraw, show hardware layers updates, profile GPU rendering, and others. However, there is a big gap in terms of development tools for tracking layout traversals and figuring out how your layouts actually behave. This is why I created [Probe](https://github.com/lucasr/probe/).

Probe is a small library that allows you to intercept view method calls during Android&#8217;s layout traversals e.g. _onMeasure()_, _onLayout()_, _onDraw()_, etc. Once a method call is intercepted, you can either do extra things on top of the view&#8217;s original implementation or completely override the method on-the-fly.

Using Probe is super simple. All you have to do is implement an _Interceptor_. Here&#8217;s an interceptor that completely overrides a view&#8217;s onDraw(). Calling super.onDraw() would call the view&#8217;s original implementation.

<pre style="font-size: smaller;">public class DrawGreen extends Interceptor {
    private final Paint mPaint;

    public DrawGreen() {
        mPaint = new Paint();
        mPaint.setColor(Color.GREEN);
    }

    @Override
    public void onDraw(View view, Canvas canvas) {
        canvas.drawPaint(mPaint);
    }
}</pre>

Then deploy your Interceptor by inflating your layout with a Probe:

<pre style="font-size: smaller;">Probe probe = new Probe(this, new DrawGreen(), new Filter.ViewId(R.id.view2));
View root = probe.inflate(R.layout.main_activity, null);</pre>

Just to give you an idea of the kind of things you can do with Probe, I&#8217;ve already implemented a couple of built-in interceptors. [OvermeasureInterceptor](https://github.com/lucasr/probe/blob/master/library/src/main/java/org/lucasr/probe/interceptors/OvermeasureInterceptor.java) tints views according to the number of times they got measured in a single traversal i.e. equivalent to overdraw but for measurement.

[LayoutBoundsInterceptor](https://github.com/lucasr/probe/blob/master/library/src/main/java/org/lucasr/probe/interceptors/LayoutBoundsInterceptor.java) is equivalent to Android&#8217;s &#8220;Show layout bounds&#8221; developer option. The main difference is that you can show bounds only for specific views.

Under the hood, Probe uses Google&#8217;s [DexMaker](https://code.google.com/p/dexmaker/) to generate dynamic View proxies during layout inflation. The stock [ProxyBuilder](http://dexmaker.googlecode.com/git/javadoc/com/google/dexmaker/stock/ProxyBuilder.html) implementation was not good enough for Probe because I wanted to avoid using reflection entirely after the proxy classes were generated. So I created a specialized [View proxy builder](https://github.com/lucasr/probe/blob/master/library/src/main/java/org/lucasr/probe/ViewProxyBuilder.java) that generates proxy classes tailored for Probe&#8217;s use case.

This means Probe takes longer than your usual _LayoutInflater_ to inflate layout resources. There&#8217;s no use of reflection after layout inflation though. Your views should perform the same. For now, Probe is meant to be a developer tool only and I don&#8217;t recommend using it in production.

The [code](https://github.com/lucasr/probe/) is available on Github. As usual, contributions are very welcome.
