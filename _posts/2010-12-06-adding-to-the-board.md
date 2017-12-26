---
id: 1972
title: Adding to The Board
date: 2010-12-06T01:40:48+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=1972
permalink: /2010/12/06/adding-to-the-board/
categories:
  - Free Software
  - General
  - GNOME
  - Software
  - Archived
tags:
  - add
  - browser
  - chrome
  - clipboard
  - Desktop
  - firefox
  - Free Software
  - GNOME
  - gnome shell
  - gtkstatusicon
  - hacking
  - nautilus
  - patch
  - planet
  - status icon
  - the board
---
[<img class=" alignnone" src="http://farm5.static.flickr.com/4144/5221020969_049bb09f76.jpg" width="500" height="313" />](http://vimeo.com/17506246)

When I first [introduced](http://lucasr.org/2010/07/24/introducing-the-board/)
[The Board](http://live.gnome.org/TheBoardProject), I generally described how I
envisioned things being added to the pages—have a look at the "Add to The
Board" and "Integration with other apps" sections in the intro post. I decided
to spend some time implementing a few interesting ways of adding content to The
Board so that the app concept gets a bit more clear in practical terms. Click
on the image above to see a [video](http://vimeo.com/17506246) demonstrating
all features described here. Here's the user story I have in mind:

> Henry is a journalist who writes gadget reviews. He was assigned to write a
> review of this new Android phone. He needs to do a bit of research before
> starting to write. He activates The Board and creates a new page called
> "Android article".
>
> He opens the web browser to search for reviews, pages, images, and videos
> about the product. For each relevant page, image, video or piece of text he
> finds useful for his article, he simply right-clicks on them and adds them
> directly to The Board.
>
> He also has a few local documents about competing products which might be a
> good source for his article. He opens some of those documents, copies the
> related pieces of text, activates The Board, and pastes them as notes.
>
> He then remembers he had already downloaded some photos of the phone a few
> days ago. He opens Nautilus to access the folder containing the images,
> right-clicks on the images and adds them to The Board as well. He
> activates The Board again, presses 't' to add a new note, a quickly
> writes down a few ideas on how the article can be structured.
>
> Henry is now ready to start writing his article.

**Browser.** I've implemented extensions for Chrome and Firefox. The [Chrome
extension](http://git.gnome.org/browse/the-board/tree/src/chrome) can only add
links and text selections as I couldn't find a good way to handle photo and
video downloads—I hope to get this implemented soon. The [Firefox
extension](http://git.gnome.org/browse/the-board/tree/src/firefox) is more
complete and allows you add links, text selections, images, and videos (using
HTML's video tag, not flash) from the browser.

These extensions add a context menu item when right-clicking on the cited web
content. In case of images and videos, they automatically download the file to
a proper [user
directory](http://library.gnome.org/devel/glib/stable/glib-Miscellaneous-Utility-Functions.html#GUserDirectory)
before adding a respective element on The Board's current page. The extensions
communicate with The Board via HTTP. A notification is shown when content is
successfully added.

One big missing feature is a toolbar button which intelligently adds the
current page to The Board. This means that if you're in, say, Google Maps, if
you hit this toolbar button, it adds the map to The Board. If you hit this
button while viewing a photo on Flickr, the photo itself is added to The Board.
You got the idea.

**File Manager.** The Board's integration with Nautilus is done through an
[extension](http://git.gnome.org/browse/the-board/tree/src/nautilus). The
extension adds a context menu item every time the files can be added to The
Board. For now, it only allows adding images. Videos should be coming soon. A
notification is also shown when content is successfully added from Nautilus.
This was the first time I wrote code based on the
new [GDBus](http://library.gnome.org/devel/gio/2.25/gdbus-lowlevel.html) API.
Pretty simple to use.

**Clipboard.** I added some initial code to handle paste command on The Board's
window. In practice, this means that if you copy text from somewhere, you can
just use the usual Ctrl+V keyboard shortcut on The Board to paste it as a label
or note. Still need to implement URI and image pasting.

**Keyboard shortcuts.** It should be simple and fast to add things to The Board
while using it directly. The current keyboard shortcuts are 'l' for label, 't'
for note, 'p' for photo, and 'v' for video. When something is added to the
current page, the new element is activated straight away and you can start
typing even before it reaches its final position.

This is all very initial code. It's definitely a bit buggy and missing
features. But it's in a dogfoodable state—for developers at least. In fact,
I've been dogfooding The Board full time for a few weeks now. I added this
temporary [status
icon](http://www.flickr.com/photos/lucasrocha/5185877990/) that shows and
hides The Board's main window—you can see it in the video. Works well
enough for daily usage.

I still haven't decided how to integrate The Board with [GNOME
Shell](http://live.gnome.org/GnomeShell) yet. That means figuring out how the
"activate The Board" part of the user story above would actually happen. I've
been playing with some
[mockups](http://www.flickr.com/photos/lucasrocha/5169105323/) but nothing
solid came up so far. Ideas—especially from GNOME Shell guys—are
welcome. Patches for all the missing stuff I mentioned above—or for anything
else really—are more than welcome too.
