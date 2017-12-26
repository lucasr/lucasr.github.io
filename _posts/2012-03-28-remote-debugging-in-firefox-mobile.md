---
id: 2678
title: Remote Debugging in Firefox Mobile
date: 2012-03-28T15:43:27+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2678
permalink: /2012/03/28/remote-debugging-in-firefox-mobile/
image: /wp-content/uploads/2012/03/debugger1.png
categories:
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - community
  - debugger
  - development
  - devtools
  - fennec
  - firefox
  - javascript
  - Mobile
  - mozilla
  - Web
  - work week
---
As you probably know by now, the DevTools team [got
together](http://antennasoft.net/robcee/2012/03/26/firefox-devtools-team-in-london/)
here in London last week. I attended their work week with the specific mission
of getting remote debugging to work on Firefox Mobile (a.k.a Fennec).

The result? I wrote a couple of
[patches](https://bugzilla.mozilla.org/show_bug.cgi?id=739966) that allow you
to debug JavaScript code from web pages running on Firefox Mobile. You can add
breakpoints, step through your JS code, track the call stack and variable
values from the experimental script debugger in Firefox's Nightly build on
desktop.

The script debugger uses the [remote debugging
protocol](https://wiki.mozilla.org/Remote_Debugging_Protocol) to send commands
to Fennec via network. You have to connect your Android device to your computer
via USB and map a _localhost_ port using the follow _adb_ command:

`adb forward tcp:6000 tcp:6000`

This will map port 6000 on your computer with the same TCP port on your mobile
device. There's no UI in the script debugger to connect to a remote Firefox
instance yet but the DevTools team already have a [patch
series](http://hg.mozilla.org/users/rcampbell_mozilla.com/remote-debug) adding
that. My patches simply implement the necessary
[actors](https://wiki.mozilla.org/Remote_Debugging_Protocol#Actors) that expose
all browser tabs to the script debugger.

Remote debugging is especially important for mobile web developers. They need a
way to easily tweak pages on the mobile device and see the results instantly.
Right now, the remote debugging protocol only allows you to debug JavaScript
code but  the long-term goal is to allow web developers to do much more:
injecting code, inspecting DOM nodes, tweaking CSS rules, etc.

As you can see, there's a lot of exciting work in progress here and many
patches about to land in our repositories very soon. Stay tuned!
