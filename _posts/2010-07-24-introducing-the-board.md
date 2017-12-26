---
id: 1620
title: Introducing The Board
date: 2010-07-24T13:22:20+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=1620
permalink: /2010/07/24/introducing-the-board/
categories:
  - Free Software
  - General
  - GNOME
  - Software
  - Archived
tags:
  - clutter
  - community
  - Desktop
  - Free Software
  - gitorious
  - gjs
  - GNOME
  - GTK
  - hacking
  - Life
  - lined paper
  - mx
  - online
  - photos
  - planet
  - platform
  - sharing
  - Software
  - spare time
  - sticky notes
  - the board
  - tumblr
---
[<img class=" alignnone" src="http://farm5.static.flickr.com/4099/4784086741_9c151111db.jpg" width="500" height="313" />](http://vimeo.com/13601332)

[GUADEC 2010](http://2010.guadec.org) is about to begin and, unfortunately, [I
will not attend](http://lucasr.org/2010/07/08/not-going-to-guadec/) it this
year. But I think it's a good time to introduce a small cool project I've been
gradually working on in my (rare) spare time. I'd like to present you [The
Board](http://live.gnome.org/TheBoardProject).

**What is The Board?** It's a space for quickly placing daily records: photos,
video, audio, text, and more. Think of it as a combination of a note-taking
space, a photo or video booth, photo album, sketching board, a digital
diary, and (in the future) a nice way to quickly share stuff with your
friends. Click on the image above to watch a
[video](http://vimeo.com/13601332) showing how the app works now.

The focus is to provide a quick, simple and visually engaging way of keeping
small records of your day. I envision The Board as a sort of especial workspace
in GNOME. Something that's "always there" and is tightly integrated with the
desktop. For now, it's simply an app that always runs in full screen — so that
I can demonstrate the idea more accurately.

**Add to The Board.** The Board can be used a quick note taking app. Someone is
telling you a phone number you want to take note of? Switch to The Board, press
"s" (or use the toolbox) and quickly write down the phone number. You have a
favourite photo for the day? Switch to The Board, press "p" and select the
photo file (similar thing for video and audio). Want to write down some ideas
before you forget them? Switch to The Board, press "t", and you have a nice
lined note paper to write in. Want to record a quick video with a happy family
moment? Switch to The Board, press "v", and you can start recording the video.
You got the idea. For now, I have only implemented simple text elements (lined
paper and sticky note) and photo. There's more coming (see "Next steps"
below).

**One page at a time.** You don't need to remove old things or "manage" the
things on The Board. Once you filled the whole screen space, just create
another page! Your previous content will be saved and can be easily accessed
through the Pages toolbox. You don't even need to worry about saving your
content. The Board saves the latest content of your page every time your change
it by editing, adding or removing things, etc.

**What is it made of?** The Board is built on top of bleeding edge GNOME
platform. It's written in Javascript using the [GObject
Introspection](http://live.gnome.org/GObjectIntrospection)-based
[Gjs](http://live.gnome.org/Gjs). The UI is fully written with
[Clutter](http://clutter-project.org/) and
[Mx](http://gitorious.org/mx-toolkit) (with some small bits of GTK+ and
Clutter-GTK+). It's a nice example of how you can do cool apps using the GNOME
platform nowadays.

**What's the current state?** The initial core code and framework is in place.
But there are obviously tons of things to be done. The app is not even
installable yet! I'm still sketching the API to implement plugins. Video and
audio elements are not implemented yet. The graphic design is poor (as I did it
myself using some random graphics from internet) and there are lots of
open interaction design questions to be sorted out. In order to run the app for
development purposes, you'll need a full GTK+ 3 stack, and latest (as in git
clone master) clutter, clutter-gtk, mx, gobject-introspection, and gjs.
The official code is in [gitorious](http://gitorious.com/the-board) now.

**How can I help?** If you want to hack on The Board, grab the
[code](http://gitorious.com/the-board), build it and run it. Play with the app
and bring ideas, fix bugs, implement new features, etc. Business as usual. If
you're an interaction designer, you can help by solving some of the hard
questions still needing answers in terms of usability and user experience :-)
On the graphic design front, I'd really like to have better graphics for all UI
elements. I have to find a nice free (as in freedom) font to use in the UI. I'm
temporarily using this funny [freeware
font](http://www.fontsquirrel.com/fonts/Action-Man). Users can help by giving
constructive feedback on how we can make The Board more interesting, useful,
and exciting. In any case, contact me and we can discuss how and
what to do.

So, what are the next steps? As I said before, there are tons of things to be
done. Here's what I have in mind in terms of short-term and long-term roadmap.

**Come up with a simple Plugin API.** By plugins I mean either the
implementation of new types of things to be added to The Board's pages or new
types of background — which can contain animations and react to user events by
the way. For example, a background could be a wooden table with a light switch
that can be turned on and off. Or the background can change colour depending on
the current time of the day.

**Integration with other apps.** Basically, users should be able to add new
things to The Board through existing apps. For example, An <em>Add to the
Board</em> option in Nautilus when right-clicking image, video, audio, or text
files. Similar thing with apps like EOG or F-Spot — an <em>Add image to The
Board </em>option. Integration with web browsers would be nice too: saw an
interesting image on a webpage? Just add it to The Board. Or maybe add your
text selection as a sticky note in The Board. Still on the app integration
front, I'm doing some work to integrate a <a
href="http://projects.gnome.org/cheese/">Cheese</a> dialog into The Board so
that you can add photos and videos from webcam without having to switch apps.

**Online experience.** This is one area that I'm still unsure how to handle. My
initial idea is that you can share anything in The Board pages. From a user
perspective, you would just add something to The Board and click "Share". On
the server side, I'm thinking of having a WordPress instance with a plugin to
present The Board's custom types just like you see them in your desktop. i.e.
sticky notes in The Board should look exactly the same in your "Board webpage".
The advantage of implement this as a WordPress plugin is that it would be
installable in a large number of personal servers from day one. <a
href="http://www.tumblr.com/">Tumblr</a> is definitely the main inspiration in
terms of online experience here as it offers a rich media blogging approach.

Anyway, you probably got the idea after reading this (maybe too) long blog
post. If you got excited about The Board and want to help with code, graphics,
design ideas, or just simple feedback, post a comment here or [contact
me](http://lucasr.org/about) directly. I'll be hacking on The Board in my
spare time as usual. But things can definitely move much faster if it gets
more people involved. If you're into writing simple and beautiful software
using GNOME's latest technologies, this should be a fun project to
contribute to!
