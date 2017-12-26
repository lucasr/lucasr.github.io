---
id: 3902
title: How Android Transitions Work
date: 2014-03-13T14:15:26+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=3902
permalink: /2014/03/13/how-android-transitions-work/
image: /wp-content/uploads/2014/03/transitions.png
categories:
  - Android
  - General
tags:
  - android
  - androiddev
  - animations
  - architecture
  - code
  - framework
  - mozilla
  - open source
  - planet
  - transitions
  - ui
---

One of the biggest highlights of the Android KitKat release was the new <a
href="https://developer.android.com/about/versions/kitkat.html#44-transitions">Transitions
framework</a> which provides a very convenient API to animate UIs between
different states.

The Transitions framework got me curious about how it orchestrates layout
rounds and animations between UI states. This post documents my understanding
of how transitions are implemented in Android after skimming through the source
code for a bit. I've sprinkled a bunch of source code links throughout the post
to make it easier to follow.


Although this post does contain a few development tips, this is _not_ a
tutorial on how to use transitions in your apps. If that's what you're looking
for, I recommend reading Mark Allison's <a
href="http://blog.stylingandroid.com/archives/category/animation/transition">tutorials</a>
on the topic.

With that said, let's get started.

## The framework


Android's Transitions framework is essentially a mechanism for animating
layout changes e.g. adding, removing, moving, resizing, showing, or hiding
views.


The framework is built around three core entities: _scene root_,
_scenes_, and _transitions_. A _scene root_ is an
ordinary _ViewGroup_ that defines the piece of the UI on which the
transitions will run. A _scene_ is a thin wrapper around a
_ViewGroup_ representing a specific layout state of the _scene
root_.


Finally, and most importantly, a _transition_ is the component
responsible for capturing layout differences and generating animators to switch
UI states. The execution of any transition always follows these steps:

  1. Capture start state
  2. Perform layout changes
  3. Capture end state
  4. Run animators

The process as a whole is managed by the _TransitionManager_ but most
of the steps above (except for step 2) are performed by the
_transition_. Step 2 might be either a scene switch or an arbitrary
layout change.
**

## How it works

Let's take the simplest possible way of triggering a transition and go through
what happens under the hood. So, here's a little code sample:

<pre style="font-size: smaller;">TransitionManager.beginDelayedTransition(sceneRoot);

View child = sceneRoot.findViewById(R.id.child);
LayoutParams params = child.getLayoutParams();
params.width = 150;
params.height = 25;
child.setLayoutParams(params);</pre>

This code triggers an _AutoTransition_ on the given _scene root_
animating _child_ to its new size.

The first thing the _TransitionManager_ will do in
_beingDelayedTransition()_ is checking if there is a pending delayed
transition on the same _scene root_ and just bail if there is one<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L356">code</a></sup>.
This means only the first _beingDelayedTransition()_ call within the
same rendering frame will take effect.

Next, it will reuse a static _<a
href="https://developer.android.com/reference/android/transition/AutoTransition.html">AutoTransition</a>_
instance<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L363">code</a></sup>.
You could also provide your own transition using a <a
href="http://developer.android.com/reference/android/transition/TransitionManager.html#beginDelayedTransition%28android.view.ViewGroup,%20android.transition.Transition%29">variant</a>
of the same method. In any case, it will always clone<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L365">code</a></sup>
the given transition instance to ensure a fresh start<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Transition.java#L1466">code</a></sup>—consequently
allowing you to safely reuse _Transition_ instances across
_beingDelayedTransition()_ calls.


It then moves on to capturing the start state<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L266">code</a></sup>.
If you set target view IDs on your transition, it will only capture values for
those<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Transition.java#L1006">code</a></sup>.
Otherwise it will capture the start state recursively for all views under the
_scene root_<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L366">code</a></sup>.
So, please, set target views on all your transitions, especially if your
_scene root_ is a deep container with tons of children.

An interesting detail here: the state capturing code in _Transition_ has
especial treatment for _ListViews_ using adapters with stable IDs<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L366">code</a></sup>.
It will mark the _ListView_ children as having <a
href="http://developer.android.com/reference/android/view/View.html#setHasTransientState%28boolean%29">transient
state</a> to avoid them to be recycled during the transition. This means you
can very easily perform transitions when adding or removing items to/from a
_ListView_. Just call _beginDelayedTransition()_ before updating
your adapter and an _AutoTransition_ will do the magic for you—see this
<a href="https://gist.github.com/lucasr/9508647">gist</a> for a quick sample.


The state of each view taking part in a transition is stored in
_TransitionValues_ instances which are essentially a _Map_ with
an associated _View_<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionValues.java">code</a></sup>.
This is one part of the API that feels a bit hand wavy.
Maybe _TransitionValues_ should have been better encapsulated?


_<a
href="http://developer.android.com/reference/android/transition/Transition.html">Transition</a>_
subclasses fill the _TransitionValues_ instances with the bits of the
_View_ state that they're interested in. The _ChangeBounds_
transition, for example, will capture the view bounds (left, top, right,
bottom) and location on screen<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/ChangeBounds.java#L84">code</a></sup>.

Once the start state is fully captured, _beginDelayedTransition()_ will
exit whatever previous scene was set in the _scene root_<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L272">code</a></sup>,
set current scene to _null_<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L367">code</a></sup>
(as this is not a scene switch), and finally wait for the next rendering
frame<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L210">code</a></sup>.


_TransitionManager_ waits for the next rendering frame by adding an <a
href="http://developer.android.com/reference/android/view/ViewTreeObserver.OnPreDrawListener.html">_OnPreDrawListener_</a>__<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L250">code</a></sup>
which is invoked once all views have been properly measured and laid out, and
are ready to be drawn on screen (Step 2). In other words, when the
_OnPreDrawListener_ is triggered, all the views involved in the
transition have their target sizes and positions in the layout. This means
it's time to capture the end state (Step 3) for all of them<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L239">code</a></sup>—following
the same logic than the start state capturing described before.

With both the start and end states for all views, the transition now has enough
data to animate the views around<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/TransitionManager.java#L245">code</a></sup>.
It will first update or cancel any running transitions for the same
views<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Transition.java#L1243">code</a></sup>
and then create new animators with the new _TransitionValues_<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Transition.java#L1295">code</a></sup>
(Step 4).

The transitions will use the start state for each view to &#8220;reset&#8221;
the UI to its original state before animating them to their end state. This is
only possible because this code runs just before the next rendering frame is
drawn i.e. inside an _OnPreDrawListener_.

Finally, the animators are started<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Transition.java#L570">code</a></sup>
in the defined order (together or sequentially) and magic happens on screen.
**

##  Switching scenes


The code path for switching scenes is very similar to
_beginDelayedTransition()_—the main difference being in how the layout
changes take place.

Calling _go()_ or _transitionTo()_ only differ in how they get
their transition instance. The former will just use an _AutoTransition_
and the latter will get the transition defined by the
_TransitionManager_ e.g. _toScene_ and _fromScene_
attributes.

Maybe the most relevant of aspect of scene transitions is that they effectively
replace the contents of the _scene root_. When a new scene is entered,
it will remove all views from the _scene root_ and then add
itself to it<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Scene.java#L160">code</a></sup>.

So make sure you update any class members (in your _Activity_,
_Fragment_, custom _View_, etc.) holding view references
when you switch to a new scene. You'll also have to re-establish any dynamic
state held by the previous scene. For example, if you loaded an image from the
cloud into an _ImageView_ in the previous scene, you'll have to transfer
this state to the new scene somehow.

##  Some extras

Here are some curious details in how certain transitions are implemented that
are worth mentioning.

The _ChangeBounds_ transition is interesting in that it animates, as the
name implies, the view bounds. But how does it do this without triggering
layouts between rendering frames? It animates the view frame (left, top, right,
and bottom) which triggers size changes as you'd expect. But the view
frame is reset on every _layout()_ call which could make the transition
unreliable. _ChangeBounds_ avoids this problem by suppressing layout
changes on the _scene root_ while the transition is running<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/ChangeBounds.java#L171">code</a></sup>.

The _Fade_ transition fades views in or out according to their presence
and visibility between layout or scene changes. Among other things, it fades
out the views that have been removed from the _scene root_, which is an
interesting detail because those views will not be in the tree anymore on the
next rendering frame. _Fade_ temporarily adds the removed views to the
_scene root_'s overlay to animate them out during the transition<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/transition/Fade.java#L246">code</a></sup>.

## Wrapping up


The overall architecture of the Transitions framework is fairly simple—most of
the complexity is in the _Transition_ subclasses to handle all types of
layout changes and edge cases.

The trick of capturing start and end states before and after an
_OnPreDrawListener_ can be easily applied outside the Transitions
framework—within the limitations of not having access to certain private APIs
such as _ViewGroup_'s _supressLayout()_<sup><a
href="https://github.com/android/platform_frameworks_base/blob/kitkat-release/core/java/android/view/ViewGroup.java#L5373">code</a></sup>.

As a quick exercise, I <a
href="https://gist.github.com/lucasr/9508844">sketched</a> a
_LinearLayout_ that animates layout changes using the same
technique—it's just a quick hack, don't use it in production! The same idea
could be applied to implement transitions in a backwards compatible way for
pre-KitKat devices, among other things.

 That's all for now. I hope you enjoyed it!
