---
id: 108
title: Hildon UI Development News
date: 2007-01-29T14:07:03+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2007/01/29/hildon-ui-development-news/
permalink: /2007/01/29/hildon-ui-development-news/
categories:
  - General
  - GNOME
  - Maemo
  - Archived
tags:
  - hacking
  - Hildon
  - hildon desktop
  - Maemo
  - news
  - nokia
  - plugin system
  - python
  - sardine
---
As you probably (don't) know, we, from the [Hildon UI
Framework](http://maemo.org/platform/docs/maemo_exec_whitepaper.html) team,
have been working hard in the new code for the next releases of
[Maemo](http://www.maemo.org) _(The "don't" is because even though the
development happens in a public repository, sometimes we're not very good in
communicating about what we're doing)_. Now, the heavy development work of
[maemo-af-desktop](https://stage.maemo.org/svn/maemo/projects/haf/trunk/maemo-af-desktop)
is taking place in a separate branch called
[hildon-desktop](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/hildon-desktop/)
(the new name of maemo-af-desktop).

Our main goals for the next releases is flexibility, scalability,
maintainability and developer-friendliness. The code of "maemo-af-desktop"
received a lot of improvements for the N800 and Bora release _(As you with
a N800 in hands have probably noticed!)_ but still it has some
serious problems. The layout of the UI is hardcoded (is was done for a
specific display with specific resolution) and the plugin
infrastructure is fragmented and (kind of) duplicated for each UI component
(Home, Statusbar and Tasknavigator). Also, the plugin API is not very
developer-friendly because it doesn't take full advantage of the [GNOME
Platform](http://developer.gnome.org/doc/guides/platform-overview/platform-overview.html)
knowlegde that developers interested in Maemo already have _(this is my
personal opinion)_. So, what are we doing to target those issues?
Let's see!

**Separating the generic parts from the specific ones**

We detached the "generic" parts of the UI into a library called
[libhildondesktop](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/hildon-desktop/libhildondesktop).
This lib has things like different kinds of panels, a generic widget for Home,
and interfaces for different kinds of desktop items that will reside in
the panels and Home. The window management code has been put into a
library called
[libhildonwm](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/hildon-desktop/libhildonwm)
which is intented for very specific cases where the developer need some
control over the windows behavior. For example, libhildonwm is used by
application switcher to show the list of active windows in the Task
Navigator panel.

So, what does this mean? This means that out future UI will be just a specific
application of libhildondesktop and libhildonwm for a specific device. In
hildon-desktop branch, we're about to finish the UI (based on libhildondesktop
and libhildowm, of course) that reproduces exactly what you have in
N800. Also, it's good to remark that this aproach makes it easier/faster to
prototype different UIs and increase the hacking possibilities for the UI! Yay!

**New plugin system**

We now have a common plugin system for all UI components. The new plugin system
is based on plugin loaders. Each type of plugin loader is reponsible for
loading desktop items from different "sources". For example, we have a plugin
loader that loads (Task Navigator, Statubar and Home) plugins written with the
current plugin API _(To keep backwards compatibility)_. However, we'll have a
new
[GTypeModule](http://developer.gnome.org/doc/API/2.0/gobject/GTypeModule.html)-based
API for developing desktop plugins so obviously we have a plugin loader for
this kind of plugin too. This aproach give us flexibility enough to even have
plugins written in different programming languages. We already have a Python
plugin loader and the bindings for libhildondesktop _(libhildonwm bindings yet
to come)_.

<img class=" alignnone" src="http://lucasr.org/wp-content/uploads/2007/01/python-plugin.jpg"/>

Plugin loaders can be dynamically loaded without needing to rebuild
hildon-desktop. We did this way because in the case of plugin loaders for
plugins written in programming languages other than C, we cannot ensure that
the runtime requirements will be available in the device by default. For
example, the Python loader resides in a different module together with the
libhildondesktop bindings so that in the future, if you want to add support for
Python desktop plugins, you just need to install the bindings, the Python
loader and Python debian packages. That's it!

The hildon-desktop Python support code is
[available](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/python-hildondesktop/),
of course. We've written some really [dummy example
plugins](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/example-plugins/)
with the new API and Python API just to give a taste of what is coming.

**Contribute!**

Any suggestions, comments, ideas, construtive critics and (specially!) patches
are welcome. Get the
[code](https://stage.maemo.org/svn/maemo/projects/haf/branches/maemo-af-desktop/hildon-desktop/)
from Maemo repository and play, brake, adapt, change, etc. If you want to use
the latest pre-built packages, you can always use
[Sardine](http://sardine.garage.maemo.org/).

**Important note!**

This is **unstable-under-heavy-development code**. You should **not** rely on
this code for anything. At this moment, hildon-desktop should only be used by
courageous developers who want to contribute/use the very latest UI framework
stuff.
