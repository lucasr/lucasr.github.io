---
id: 128
title: Writing a cool Python plugin for Hildon Desktop
date: 2007-03-29T14:03:29+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/03/29/writing-a-cool-python-plugin-for-hildon-desktop/
permalink: /2007/03/29/writing-a-cool-python-plugin-for-hildon-desktop/
categories:
  - Free Software
  - General
  - Maemo
  - Archived
tags:
  - hacking
  - Hildon
  - hildon desktop
  - Maemo
  - n800
  - plugin
  - python
  - resolution
  - screencast
---
Ok, now that I've shown [how easy is to have the basic code for a Python plugin
running in Hildon Desktop](http://blogs.gnome.org/view/lucasr/2007/03/22/0),
I'd like to demonstrate something more useful and cool. I did this screencast
presenting how to write a plugin which randomly shows images from your
&#8220;Images&#8221; directory in your Home area. Cool hun?

[<img class=" alignnone" style="border: 0px initial initial;" src="http://lucasr.org/wp-content/uploads/2007/03/plugin-howto-2.png" border="0"/>](http://www.gnome.org/~lucasr/misc/hildondesktop-plugin2.ogg)

Some (obvious) improvements for this plugin would be:

  * A configuration dialog where you can define the images directory and the
  delay for image switching.
  * Disable image switching when the device idle or when the Home area is not
  visible
  * Switch to next random image when clicking on the plugin.
  * What else do you want? :-P

Enjoy!

_Sidenote 1_: yes, the screencast shows Hildon Desktop running on a
800&#215;600 resolution. :-)

_Sidenote 2_: some people have been asking if [Hildon
Desktop](https://stage.maemo.org/svn/maemo/projects/haf/trunk/hildon-desktop/)
is available in N800 already. The answer is no. Hildon Desktop is a major
rewrite of maemo-af-desktop and will be shipped in the next major releases of
[Maemo](http://www.maemo.org). Of course you could run it on your N800 at your
own risk. :-P
