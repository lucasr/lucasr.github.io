---
id: 2107
title: Animate Wisely
date: 2011-02-04T23:42:56+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2107
permalink: /2011/02/04/animate-wisely/
image: /wp-content/uploads/2011/02/motion1.jpg
categories:
  - General
  - Software
  - Archived
tags:
  - animations
  - clutter
  - design
  - development
  - fluid
  - GNOME
  - gnome shell
  - guidelines
  - litl
  - meego
  - netbook
  - planet
  - Software
  - the board
  - ui
  - ux
---
I've been hacking on rich UIs with animations for a few years—both in the [litl
OS](http://litl.com) and in my [pet
project](http://live.gnome.org/TheBoardProject). There was a time, not too long
ago, that doing animations in your web, mobile or desktop app was not so common
or convenient to do. You had to mess with weird lower-level APIs or write a lot
of cryptic ad hoc code. We just didn't have nice high-level APIs for
animations.

Nowadays fluid UIs with animations are relatively easy to do on pretty much all
major platforms out there—jQuery, Clutter, Core Animation, WPF, QML, Tweener,
etc. Things like fading, sliding, zooming, rotating, scaling are all just
a few of lines of code away. So it's very easy to fall on the trap of
overusing animations just for the sake of eye-candiness. But animations
can have a very negative impact on the user experience if not done
properly.

## Delayed interaction

Using UI animations often means that you're making your app take more time to
go from state A to B. For example, by using this [ribbon-like
effect](http://lucasr.org/wp-content/uploads/2011/02/modal-dialogs.ogg) on
modal dialogs—motion mockup by [Jakub
Steiner](http://jimmac.musichall.cz/)—instead of just popping them up
immediately, you're adding a delay between the user request and the dialog
being ready for interaction. The animation in this case is not a bad idea as it
helps the user understand the UI and it's fast enough. But if you consistently
delay interaction with animations for no good reason, the UI quickly gets very
annoying to use. So, getting the timing of your animations right is very
important.

## Distraction

When animations are not subtle enough, they cause users to move their attention
from the current task to the animation itself. It's like the UI is saying
"Look! I'm animating now!". Google's [particle similator
logo](https://www.rubypay.com/google/Google.htm) is an extreme example of a
distracting animation. Every time you add an animation just because you can or
because it's "cool", you're probably just distracting your users.

## Confusion

Animations might actually confuse users. One recent example is the Twitter for
Mac's [continuous slide out
transitions](http://riscfuture.tumblr.com/post/2626504717/app-store-twitter-ui-failures)
that create a strange sensation of infinite "stacking". Confusing animations
might seed wrong assumptions and uncertainty about how the UI works: "Why does
it slide to right again when I click on the previous tab? Am I doing something
wrong?".

## Repetition

Certain animations look cool on the first few times you see them but become
quite annoying later on. The repetition problem is aggravated when the
repetitive animation is also confusing, distracting or delays interaction. For
example, the [tooltips animation](http://www.youtube.com/watch?v=1P5DHjSLj8s)
in MeeGo's Netbook UX is both repetitive and distracting—Intel guys
are [aware](http://bugzilla.clutter-project.org/show_bug.cgi?id=2263) of this
issue. Commonly used UI elements should have very subtle or no animations at
all.

And I guess there are many other ways animations are just done wrong. Bottom
line is: with all the simple ways of filling your UI with all types of
animations these days, it's quite easy to end up overusing them. Resist the
temptation! Animations work best when they highlight the underlying mental
model of your software and improve UX. Animate wisely.
