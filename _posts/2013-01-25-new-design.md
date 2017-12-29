---
title: New Blog Design
date: 2013-01-25T12:18:18+00:00
layout: post
permalink: /2013/01/25/new-design/
image: /wp-content/uploads/2013/01/refresh.png
categories:
  - Free Software
  - General
  - Software
  - Archived
tags:
  - 37signals
  - blog
  - caching
  - comments
  - design
  - github
  - mozilla
  - new year
  - opoloo
  - performance
  - picturefill
  - planet
  - readability
  - signal-vs-noise
  - theme
  - wordpress
---
New year, time for a long overdue design refresh on my blog! The new WordPress
theme that I've been slowly working on is now live. Here are some quick notes
about the making of it.

### Design

The main goal of the new design is to bring focus to the content, nothing else.
My main source of inspiration was definitely Opoloo's [Squirel
Park](http://blog.opoloo.com/) blog. You'll notice quite a few similarities in
terms of content structure. Other relevant sources: [Signal vs.
Noise](http://37signals.com/svn/), [Simon
Foster](http://simonfosterdesign.com/blog/), and [Ian Storm
Taylor](http://ianstormtaylor.com/).

### Typography

The new theme uses [FF Tisa Web
Pro](https://typekit.com/fonts/ff-tisa-web-pro), [FF Tisa Sans Web
Pro](https://typekit.com/fonts/ff-tisa-sans-web-pro), and [Futura
PT.](https://typekit.com/fonts/futura-pt) Tisa has a subtle modern character
without getting on the way. I love it. The fonts are served by
[Typekit](https://typekit.com). Their Personal plan is not that expensive and I
got to choose the fonts from a fairly large library.

### Implementation

My previous WordPress theme had some serious issues: it was full of weird
hacks, looked broken on certain browsers, and wasn't responsive at all. The new
theme is based on [Bootstrap](http://twitter.github.com/bootstrap/) and adapts
the content for different screen sizes nicely. Responsive images are
implemented using [picturefill](https://github.com/scottjehl/picturefill). Some
DB caching is done on the front page using WordPress' [Transient
API](http://codex.wordpress.org/Transients_API). I'm using the
[Hypercache](http://wordpress.org/extend/plugins/hyper-cache/) plugin for an
extra performance boost.

### Comments

I decided to disable comments as part of the switch to the new theme. I usually
don't get a lot of value from them anyway. Also, I don't feel like spending any
time moderating comments anymore. You can always find me on
[Twitter](https://twitter.com/lucasratmundo) and
[Google+](http://gplus.to/lucasr) if you got something to add or discuss.

The source code of the new theme is available on
[Github](https://github.com/lucasr/wp-lucasr). Enjoy!
