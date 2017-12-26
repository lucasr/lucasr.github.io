---
id: 111
title: Error/Warning UI in Eog-Ng
date: 2007-02-05T22:37:06+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/02/05/errorwarning-ui-in-eog-ng/
permalink: /2007/02/05/errorwarning-ui-in-eog-ng/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - claudio saavedra
  - EOG
  - eog-ng
  - error
  - gedit
  - GNOME
  - hacking
  - news
  - ui
  - warning
---
Currently, EOG is really crappy on reporting errors/warnings to the user.
Basicaly, you only get feedback about errors on image loading, nothing else.
Also, it uses dialogs for this which is kind of invasive and specially annoying
on a collection-based UI application like EOG. I really like the UI aproach
adopted by [gedit](http://www.gnome.org/projects/gedit/) with this cute yellow
message area. So, I borrowed gedit's code to use the same aproach in eog-ng. If
something goes wrong with the image loading, you can easily browse other images
from the same directory without needing to close EOG. Here's the result:

<img class=" alignnone" src="http://lucasr.org/wp-content/uploads/2007/02/eog-error.png"/>

I still need to add the code for different kinds of error/warnings for cases
like opening a directory with no images, opening unrecognized formats, not
found files, etc. This will be piece of cake with the new code base though.

Claudio pointed me to this [blog
post](http://pollycoke.wordpress.com/2007/01/23/eye-of-gnome-ng-il-visore-dimmagini-definitivo-howtodeb/)
from this italian guy who seems to be really excited about eog-ng. Good to know
that users are enjoying the EOG development news. :-)

**Update:** don't worry about the odd "Cancel" button. I'll fix
this ASAP. :-)
