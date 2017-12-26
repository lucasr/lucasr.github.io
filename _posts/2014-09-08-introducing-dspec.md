---
id: 3982
title: Introducing dspec
date: 2014-09-08T13:52:02+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=3982
permalink: /2014/09/08/introducing-dspec/
image: /wp-content/uploads/2014/09/dspec.png
categories:
  - Android
  - Free Software
  - General
  - Mozilla
  - Software
tags:
  - android
  - androiddev
  - design
  - firefox
  - github
  - mozilla
  - open source
  - planet
  - ui
  - ui spec
---
With all the recent focus on [baseline grids, keylines, and spacing
markers](http://www.google.com/design/spec/layout/metrics-and-keylines.html)
from Android's material design, I found myself wondering how I could make it
easier to check the correctness of my Android UI implementation against the
intended spec.

Wouldn't it be nice if you could easily provide the spec values as input and
get it rendered on top of your UI for comparison? Enter
[dspec](https://github.com/lucasr/dspec), a super simple way to define UI specs
that can be rendered on top of Android UIs.

Design specs can be defined either programmatically through a [simple
API](https://github.com/lucasr/dspec/blob/master/library/src/main/java/org/lucasr/dspec/DesignSpec.java)
or via [JSON
files](https://github.com/lucasr/dspec/blob/master/sample/src/main/res/raw/main_activity_spec.json).
Specs can define various aspects of the baseline grid, keylines, and spacing
markers such as visibility, offset, size, color, etc.

<div id="attachment_3992" style="width: 1090px" class="wp-caption alignnone">
  <a href="http://lucasr.org/wp-content/uploads/2014/09/2014-09-08-13.02.51.png"><img class="size-full wp-image-3992" src="http://lucasr.org/wp-content/uploads/2014/09/2014-09-08-13.02.51.png" alt="Baseline grid, keylines, and spacing markers in action." width="1080" height="649" srcset="http://lucasr.org/wp-content/uploads/2014/09/2014-09-08-13.02.51-665x400.png 665w, http://lucasr.org/wp-content/uploads/2014/09/2014-09-08-13.02.51-532x320.png 532w, http://lucasr.org/wp-content/uploads/2014/09/2014-09-08-13.02.51-332x200.png 332w, http://lucasr.org/wp-content/uploads/2014/09/2014-09-08-13.02.51.png 1080w" sizes="(max-width: 1080px) 100vw, 1080px" /></a>
  
  <p class="wp-caption-text">
    Baseline grid, keylines, and spacing markers in action.
  </p>
</div>

Given the responsive nature of Android UIs, the keylines and spacing markers
are positioned in relation to predefined reference points (e.g. left, right,
vertical center, etc) instead of absolute offsets.

The JSON files are Android resources which means you can easily adapt the spec
according to different form factors e.g. different specs for phones and
tablets. The JSON specs provide a simple way for designers to communicate their
intent in a computer-readable way.

You can integrate a _DesignSpec_ with your custom views by drawing it in your
_View_'s _onDraw(Canvas)_ method. But the simplest way to draw a spec on
top of a view is to enclose it in a
[DesignSpecFrameLayout](https://github.com/lucasr/dspec/blob/master/library/src/main/java/org/lucasr/dspec/DesignSpecFrameLayout.java)—which
can take an _designSpec_ XML attribute pointing to the spec resource. For
example:

```
<DesignSpecFrameLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:designSpec="@raw/my_spec">
    ...
</DesignSpecFrameLayout>
```

I can't wait to start using _dspec_ in some of the new UI work we're doing
[Firefox for
Android](https://play.google.com/store/apps/details?id=org.mozilla.firefox)
now. I hope you find it useful too. The [code is
available](https://github.com/lucasr/dspec) on Github. As usual, testing and
fixes are very welcome. Enjoy!
