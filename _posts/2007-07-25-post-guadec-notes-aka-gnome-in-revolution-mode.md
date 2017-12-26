---
id: 155
title: Post GUADEC notes (aka GNOME in revolution mode)
date: 2007-07-25T17:04:48+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/07/25/post-guadec-notes-aka-gnome-in-revolution-mode/
permalink: /2007/07/25/post-guadec-notes-aka-gnome-in-revolution-mode/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - bling
  - conduit
  - empathy
  - event
  - GNOME
  - gsettings
  - GTK
  - GUADEC
  - mallard
  - Online Desktop
---
This GUADEC brought a lot of momentum to GNOME: fresh new ideas and nice
discussions and plans about our future platform and desktop. For the first time
in the last 2 years, I have the strong feeling that GNOME is about to switch to
a "revolutions mode". This means that several small and big revolutionary
things will start to bubble inside the project from now on. I'm really excited
about it! _(Obviously, I'm not saying that nothing interesting happened before
this GUADEC. It's just that now I see more cohesion around some goals_
_inside community__.)_

**The Online Desktop**

The Online Desktop is something that, if done right, can bring a big and
positive impact on the GNOME user experience. What I like about this idea:

  * It takes advantage of the whole world of cool web services out there
  * It makes the GNOME Desktop much more **fun** (I remember Vincent
  [commented](http://www.vuntz.net/journal/2005/10/19/328-make-it-fun)
  about it 2 years ago&#8230; He is totally right!)
  * Consequently, it brings GNOME much closer to the user who uses the computer
  to strengthen his/her social and emotional ties

I don't think we should work on an "online mode" (with a special UI) for GNOME
Desktop though. IMO, the way to go is to turn GNOME into a "web-aware" desktop
environment. some examples:

  * If you're viewing some photos or watching a video, it should be easy and
  seamless to upload them to your favorite photo/video sharing web service
  * It should be natural to keep track of what your friends are doing on web
  (what Mugshot does)
  * When you import some photos from your camera, it should be possible to
  upload them straight away to the web

Bringing web-awareness to GNOME involves creating a basic platform (mostly a
set of D-Bus services and GTK+ widgets) that could be shared by any
desktop component who wants to be web-aware. This way those bits can be used on
GNOME Mobile as well.

We should not limit ourselves on the data sharing on web services because, in
essence, what we want (as users) is to share media with other people. We should
consider having an integrated communication framework as part of the Online
Desktop effort. Some examples:

  * If you're viewing some photos or watching a video, it should be easy and
  seamless to share them with one or two friends (via messenger, e-mail, local
  network share, etc). If your friends are online you can simply start
  chatting with them after you shared something with them. Something like Web
  Swarm (in Mugshot) does for links but for any shared media
  * There should be some central place to start communicating with someone. it
  doesn't matter if it's via e-mail, messenger or whatever else
  * It should be easy to make collaborative work on the same content (documents
  and media). OLPC is doing a great job on this subject

We already have a lot of code available for covering some of those use cases.
Some of them: [Conduit](http://www.conduit-project.org/) for easy syncing with
web services, [Empathy](http://live.gnome.org/Empathy) and [Mission
Control](http://mission-control.sourceforge.net/) for a
[Telepathy](http://telepathy.freedesktop.org)-based integrated communication in
the desktop, [Mugshot](http://developer.mugshot.org/wiki/Mugshot_Project)
(server and client) stack for web services activities tracking,
[Soylent](http://live.gnome.org/Soylent) for "people browsing", and so on.
There will be this big effort to add the "online" bits to applications and
other desktop components.

**"Bling!" on GNOME**

There were some nice talks about adding more "Bling!" to GNOME. It was nice to
see things like [Clutter](http://clutter-project.org/),
[Lowfat](http://macslow.thepimp.net/?page_id=18), GTK+ 3.0 (oops, 4.0!)
discussions, compositing, etc. There two things I'd like comment on:

  * We have this challenge of making GNOME sexier. Ok, cool! But let's keep
  this in mind though: we should **not** make GNOME unusable on a computer
  without 3D acceleration. At the same time that we want to impress the user
  with cool effects (which should improve the usability btw), we need keep in
  mind that there are lots of people using low-power/old computers with GNOME
  on social projects out there (Brazil has many of those).
  * In order to bring "Bling!" to GNOME in a consistent way, those bits should
  be in the platform level with components that could be easily reused among
  applications. Also, we would need to have clear guidelines in HIG. Otherwise
  we'll end up in a "Bling!" hell!

**GNOME Platform**

It was nice to see that important changes are about to come in our platform.
Most of them I've already
[commented](http://blogs.gnome.org/lucasr/2007/07/01/on-gnome-222-the-rise-of-a-revamped-platform-and-desktop/)
before: GVFS, GTK+ 3.0, New applet API, GSettings, Mallard and others. Next
year will be really nice for GNOME Platform!

**People**

  * [Danilo](http://danilo.segan.org/),
  [Andreas](http://www.andreasn.se/blog/), [Vincent](http://www.vuntz.net/) and
  [Etrunko](http://etrunko.blogspot.com/): you made my GUADEC much more fun!
  Thanks!
  * [Claudio](http://www.gnome.org/~csaavedra/news.html),
  [Pedro](http://blogs.gnome.org/pvillavi) and
  [Fernando](http://blogs.gnome.org/fsmw): it's always nice to meet you!
  * [Diego](http://blogs.gnome.org/diegoe), thanks for the scarf! It will be
  very useful here in Finland!

That's GNOME: a bunch of extremely talented and generous people working on the
common goal of creating free, easy-to-use, and innovative technologies to
everyone!
