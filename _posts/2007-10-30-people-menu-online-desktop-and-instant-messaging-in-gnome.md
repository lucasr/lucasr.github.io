---
id: 176
title: 'People menu: online desktop and instant messaging in GNOME'
date: 2007-10-30T15:08:18+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/10/30/people-menu-online-desktop-and-instant-messaging-in-gnome/
permalink: /2007/10/30/people-menu-online-desktop-and-instant-messaging-in-gnome/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - big board
  - Desktop
  - GNOME
  - GUADEC
  - idea
  - Online Desktop
  - people menu
  - ui
---
Just after GUADEC, I made some [general
comments](http://blogs.gnome.org/lucasr/2007/07/25/post-guadec-notes-aka-gnome-in-revolution-mode/)
about this whole "online desktop" idea that was nicely presented by Havoc and
Bryan in Birmingham. My main argument is that we should not have a separate
"online desktop mode" but try to turn our desktop into a web-aware environment.

Now that Empathy has been
[proposed](http://mail.gnome.org/archives/desktop-devel-list/2007-September/msg00301.html)
for GNOME 2.22, I think it's time to start thinking about interesting ways of
integrating the instant messaging stuff and online desktop stack in the desktop
_(note that there's no garantee that Empathy and online desktop will be
accepted as official modules but, as a strong supported, I still think
it makes sense to bring those ideas at this moment)_. [In my
opinion](http://mail.gnome.org/archives/desktop-devel-list/2007-September/msg00565.html),
we should take advantage of the fact that Empathy is a framework-ish aproach
for instant messaging (not simply a standalone application) to bring a seamless
integration of its features in the desktop environment.

So, I had this idea _(that should be more detailed and discussed)_ of a
possible (and feasible) way of integrating Empathy and online desktop stuff in
the desktop: a **People menu** in main menu bar.

<div style="width: 402px" class="wp-caption alignnone">
  <img src="http://www.lucasr.org/wp-content/uploads/2007/10/gnome-people-menu.jpg" width="392" height="322" />
  <p class="wp-caption-text">
    People menu mockup
  </p>
</div>

Some general comments:

  * The People menu should be optional and only activated if online desktop
  and/or Empathy are available. There will be many users who still want to use
  their favorite messenger and don't want to use this online desktop thing
  anyway
  * The "About me" would run the "About me" capplet which would need to have
some additional features for setting up messenger accounts and defining your
web presence on several online services (online desktop integration)
  * The "Contacts" menu item could run an application like
  [Soylent](http://live.gnome.org/Soylent) with easy access to your messenger
and Evolution contacts to start different communication ways (e-mail, chat,
  video call, etc)
  * The "Messenger" menu item would connect you to your configured messenger
  services and show an icon the notification area
  * The "Home page" would open the browser in your GNOME online desktop home
  page
  * The "Web activities" would start the now called Mugshot client which
  notifies you about the web activities of your friends
  * The "Web board" would activate the Bigboard sidepanel with lots of cool web
  stuff _(I think Web board is a more appropriate name from the user point of
  view)_
  * The "Recent talks" is obvious :-)

This is just an initial/rough idea with the aim of setting some kind of
direction on how we could integrate instant messaging and online desktop in
GNOME. There are still many things to discuss and decide.

Comments?
