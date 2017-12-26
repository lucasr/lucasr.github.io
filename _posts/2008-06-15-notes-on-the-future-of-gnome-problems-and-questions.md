---
id: 214
title: 'Notes on the Future of GNOME: Problems and Questions'
date: 2008-06-15T19:56:56+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2008/06/15/notes-on-the-future-of-gnome-problems-and-questions/
permalink: /2008/06/15/notes-on-the-future-of-gnome-problems-and-questions/
categories:
  - Free Software
  - General
  - GNOME
  - Archived
tags:
  - apps
  - article
  - community
  - future
  - GNOME
  - gnome3
  - ideas
  - innovation
  - problems
  - Roadmap
---
Ok, now that I've already made my point about our [great
achievements](http://blogs.gnome.org/lucasr/2008/06/09/notes-on-the-future-of-gnome-the-great-achievements/),
it's time to talk about the big questions. I ended up writing too much, sorry
:-P I won't discuss about solutions or practical actions in this post because
(obviously, I don't have all the answers and) I prefer to separately talk
about solutions and practical actions in another post. I'll try to bring the
topics that have been looping in my head (for a quite long time already) with
regards to our beloved project. They overlap in many ways with
[the](http://log.ometer.com/2008-06.html#11.2)
[opinion](http://wayofthemonkey.com/?date=2008-06-11)
[of](http://blogs.gnome.org/hughsie/2008/06/11/jumping-over-the-wall/)
[some](http://www.jonobacon.org/?p=1196)
[people](http://blogs.gnome.org/tthurman/2008/06/11/on-holy-wars-and-a-plea-for-decadence/)
[who](http://aruiz.typepad.com/siliconisland/2008/06/breaking-assumt.html)
[have](http://blogs.gnome.org/johannes/2008/06/10/create-the-vision/)
[already](http://wingolog.org/archives/2008/06/10/regarding-decadence)
[commented](http://ywwg.com/wordpress/?p=426)
[on](http://blogs.gnome.org/uraeus/2008/06/09/new-times-new-paradigmes/)
[the](http://blogs.gnome.org/calum/2008/06/07/rockstars-and-decadence/)
"[decadence](http://wingolog.org/archives/2008/06/07/gnome-in-the-age-of-decadence)".

One the most important steps on the process of finding a good solution for a
problem is to define the problem. People have different expectations and
perspectives about GNOME and hence they define the "decadence" and,
consequently, the possible solutions, in different ways. First of
all, a more fundamental question: do we have a problem? We already
have a great desktop environment for the current standards and
demands. So, what is "wrong" here? From what I can see, the
problem can be defined in terms of three aspects: Audience,
Position and Process. All those have something to do with
the fact that GNOME is getting "out of sync" with...
something. I fully agree with
[Rodney](http://wayofthemonkey.com/?date=2008-06-11),
[Havoc](http://log.ometer.com/2008-06.html#11.2),
[Mikkel](http://www.grillbar.org/wordpress/?p=278) and others
here: the whole desktop concept itself is some sort of dead-end
(even though we could be innovating much more in this area) and
is, in a certain way, getting outdated (considering the new ways
people have been using technology nowadays). Because of
that, I think it's quite dangerous to exclusively stick with the
"desktop" goal because we may be missing a lot of opportunities
(and even get into an actual decadence situation) in the near
future if we keep doing the same things in the exact same way.
(One might argue that we already have GNOME Mobile and all.
However, I'd say that this is not enough because 1) the
mobile front has been done in a kind of "marginal" way inside the
project 2) "mobile" is just one among many possible paths). So,
yes, we do need to open GNOME for a whole new range of
possibilities in a consistent way but first we need to create
the right environment for innovation.

Anyway, let me talk about each part of this problem. Those might sound a little
abstract sometimes but, in my opinion,  they summarize the big questions we
need to answer now.

Audience is about who we're targetting and, consequently, the
fundamental definition and goals of GNOME. I've just said that we already
have a great desktop. However, we can see quite often people complaining about
the lack of innovation, the need for new apps and more eye-candy, and so on.
Consequently, we have quite often those endless discussions about the future of
GNOME and where we should be heading towards: 3D desktop? Online desktop?
Corporate desktop? Topaz? The thing is: everyone is right in a way. Why?
Because we don't have a clearly-defined audience (something that [Havoc
said 3 years
ago](http://mail.gnome.org/archives/desktop-devel-list/2006-February/msg00174.html)).

When I look at what we've done so far, I would say we got to develop a simple,
intuitive, functional desktop environment that works pretty well on the
corporate world and good enough for home users. From my perspective, in
terms of user experience, we're somewhere between MS Windows and MacOS:
we're not as boring as MS Windows (that works relatively well as a
productivity/corporate type experience) and not as stylish as
MacOS (that aims to provide a more nichey media/life experience on
computers). Also, we're not clearly the best of breed on any of
those areas: corporate, life, media, or any other experiences (Don't get
me wrong here: I think we do an amazing work in general. I just
consider that we don't provide an extremely appealing experience
on any of those areas \*yet\*). I'm talking about desktop user
experiences here but we can't ignore the big changes in the personal
computing field through the countless types of mobile devices, smart
appliances, online apps and services, etc, that demand more and more the
hability to customize, adapt and extend existing open source/free
technologies in order to deliver competitive and exciting products. With
that said, some fundamental questions arise:

  1. Is it doable to stick only with development a desktop environment in
     GNOME?
  2. Which kind of desktop do we aim to develop? A corporate type? A media
     experience type? Something else? Do we really have to choose?
  3. Are we responding properly to the demand for the creation of custom user
     experiences (for distros, mobile devices, online services, etc) with a
     consistent, productive and powerful software platform?

About 1 and 3, yes, we have GNOME Mobile — which aims to provide a
standard architecture and platform that can be used by companies to develop
GNOME-based mobile devices. But how strongly does GNOME Mobile define GNOME as
a whole? There are some good lessons we can take from GNOME Mobile in terms of
development process and organization (more on that in the next post). It's
pretty clear that the strongest point of connection between GNOME Mobile and
GNOME is our platform. However, GNOME Mobile is not working as integrated as it
should inside GNOME because we still define us as a "desktop project". So, my
short answers to those questions are:

  1. No, we should expand the definition and goals of GNOME to embrace the
     diversity of ways people are (and will be) using technology today (and
     in the near future).
  2. I don't think we need to choose. What we need is to clearly define and
     maybe separate different products around different GNOME audiences.
  3. No, I think we're not properly organized to provide a powerful platform
     for different user experiences because, as I said, we still define
     ourselves as a "desktop project". In my opinion, the platform should be
     the core of GNOME and GNOME Mobile should be closer and share more
     inside the major activities of the project.

The Audience issues presented above have a tight connection with the
relationship between GNOME and distributors. That takes me to the Position
issues.

Position is about where we place GNOME in the innovation ecosystem. So
far, the relationship between GNOME and distributors is so that we release our
official modules (organized inside the desktop, platform, admin, devtools and
bindings suites) and distributors adapt and package those modules to
integrate in their systems. Normally, they also add a bunch of modules that
were (fully or partially) developed with GNOME platform but are not officially
part of GNOME suites. Then, when everything is integrated and stable,
distributors release their products with GNOME. This model has two
interesting aspects.

The first one is: GNOME is invisible to users. From end-users perspective,
they are using Ubuntu, Fedora, openSUSE, Foresight, Debian, Gentoo,
(add-your-favorite-distro-here) on their personal computers, not GNOME.
(Note that I'm not talking about geeky users but about real end-users who
don't know much about technology). This is (and will be) even
stronger on consumer products using GNOME platform such as internet
tablets, cell phones, PDAs, etc. To verify that, just pretend you're just
an end-user and have a look at the websites of most of desktop distros:
they talk about desktop but rarely mention GNOME. (Note that I'm not
making any judgements about this here. I'm trying to just bring the
fact to the table).

The second aspect is that distributors redefine the user experience. Most
of distributors change in some way the default GNOME desktop to fit and
integrate nicely with their products. openSUSE has a completely different panel
layout and use gnome-main-menu. Most of distros use Firefox instead of
Epiphany. Latest releases of the major desktop distros ship with Compiz by
default instead of Metacity. Also, they integrate desktop modules that are not
directly provided by GNOME: Pidgin for instant messaging, Rhythmbox or Banshee
for music management, F-Spot or GThumb for photo management,  Beagle or Tracker
for desktop search, and the long list continues.

So, based on those aspects, what can we say? First: even with our current
development process where we release suites of official modules to
distributors, it's not clear inside GNOME whether we are "user experience
definers" or "component providers for custom user experiences". Currently,
we're defining most of the desktop user experience through our official
modules. However, because of the way we define our final product (the
suites of official modules) there are certain areas where we simply
don't reach an agreement (more on that later). Why haven't we ever chosen
a "official" music player? Why no photo management app in the desktop?
Gimmie or gnome-main-menu or just keep the menu bar? Why is there so much
discussion around the inclusion of Empathy? The fact is, for some reason,
there are certain topics around the user experience that we just prefer to
not decide about. This makes us stay in a unclear position: we kind of
define the experience — but only on certain topics (this has a lot
to do with the lack of a defined audience and our development
process). That brings me the following questions:

  1. Should GNOME be a "user experience definer" or "component provider"? Do we
     need to choose?
  2. Does the GNOME decisions about the official modules really matter? If so,
     at what level?

My answers to those questions are:

  1. We should be component providers—but in a special way. In my
     opinion, we should platformize the user experience in a way that our
     modules can be easily reused in different contexts or products. In
     practice, this means: providing highly configurable and pluggable core
     components; well-defined services D-Bus APIs so that we easily replace
     compliant implementations with same interface; refreshed toolkit which
     embeds sexy UI elements and interactions; and more. In order to properly
     be component providers, we would need to provide a super-powerful platform
     though. Yes, that would be a big challenge (more on that in the next
     post).
  2. Yes, our module decisions matter. But they only \*really\* matter if they
     are related either to platform or to the "core" desktop components (panel,
     session, nautilus, keyring, settings daemon, capplets, etc).

So, in reality, the ecosystem around GNOME is demanding a lot of flexibility in
the platform and desktop — specially from stakeholders producing mobile devices
and other custom user experiences based on GNOME. We need to clarify our
position and goals inside this ecosystem so that we can embrace all the great
possibilities we have inside our community. We should redefine GNOME as a
platform for intuitive and exciting user experience with several reference
products for different audiences around it. In order to redefine the project,
we need to rethink the way we do things. Let's talk about the Process
problem.

Process is about how we do things. As I said in my last post, the same
process that brings so many benefits is the one that's making GNOME stall
somehow. Why? Because our current process is organized around the fact that
we're in deep maintenance mode. Actually, in a way, we've been in
maintainance mode since the 2.0 release. The main problem with this mode is
that all decisions in GNOME are done based the tacit assumption that we
should never break anything (as if the maintenance mode is a given). This
brings a very good feeling that everything is stable and predictable most the
time. And that's very true actually. However, having stability in sense of "no big changes so everything works,
cool") for a too long period is boooooring and brings all the
problems of Audience and Position (because with technology, everything gets
outdated very quickly). Let me talk about some aspects of this
maintenance mode in GNOME

The first one is that we don't have a "big picture" to base our decisions on
2.x. Yes, we are basically "adding or replacing stuff" in the same good old
stack for quite some time already. The problem here is: the big picture of 2.x
is kind of "done", "given". We're basically in passive mode, just waiting for
contributors to decide to propose and include random modules in one of our
suites. Some people may argue that we're constantly improving the platform and
desktop by revamping certain components every now and then and that shows we're
moving the project forward. In my opinion, this is not entirely true. Yes,
we've been doing some nice improvements in 2.x but the requirement to
never break anything (associated with the Audience and Position
problems) almost completely blocks innovation inside GNOME and
very often moves the cool innovation work to distributors side (because
they can break and change anything as they want anyway). And,
unfortunately, many times we end up not being able to accept distros'
innovation work because we can't break anything. Note that I'm not
saying that stability is bad. My point here is that we should have
official long-term break points in GNOME. That would be an enforcement
for the community to rethink the big picture from time to time (and not
wait for some magic "vision" to change the direction of the
project).

The second aspect is the decision making problem. In our current organization
of the development process, no one has the official role of deciding about the
general direction of the project. Some people say we have a problem of
leadership in GNOME. This is partially true. We have the core contributors who
are the ones who define the project's direction in practice. So, we have
leaders. However, this leadership is quite fragmented and doesn't have any
official position in our development process. Therefore, the real problem is in
the process: the release team is responsible for maintaining the correctness
and coherence of the development but not for defining the content. There's no
one in charge of getting the big picture and proposing a development agenda.
We need to accept the fact that we need domain/suite maintainers who
are responsible for proposing and having the last word about the content and
roadmap for certain domains/suites. The recent [Roadmap
process](http://live.gnome.org/RoadMap/Process) was a nice achievement on
spreading the word (inside and outside our community) about what we're doing.
Not enough to drive the project to a new direction because we're in
maintainance mode after all.

Lastly, the maintenance mode involves a specific definition of our suites
and hence the way we deal with third-party applications. The current
definition of our suites is too closed and not so flexible. There's a large
amount of apps being developed based on our platform that are simply ignored by
us. Of course, there's is a lot of crappy stuff our there but, on the other
hand, there's a good number of high-quality GNOME-based horizontal and vertical
apps (photo managers, media managers, recipes managers, book collection
managers, stock managers, web widgets, sexy panel replacements, etc)
that we don't keep close to us in any way. Because of that, we miss the
opportunity to get more contributors and all the potential sinergy that those
apps could bring to GNOME and our distributors. We need to provide a more
clear and interesting place for high-quality third-party apps in GNOME. Those
apps are an important part of our innovation ecosystem.

So, from my perspective, considering those three aspects of the problem
(Audience, Position and Process), a good solution for it should involve:

  1. Expading the definition and goals of GNOME in order to embrace the
     diversity around us;
  2. Defining clear audiences for our products;
  3. Redefining the position of GNOME inside our ecosystem so that we bring
     innovation inside through a powerful platform;
  4. Rethinking the development process so that we can: a) have an efficient
     decision-making chain b) "think from scratch" and break things from time
     to time c) bring third-party development closer to us.

Also, it's pretty clear to me (and I know other people agree with me) that
GNOME 3.0 should not be just "a next generation desktop" but a new way of
defining, organizing and developing GNOME. I'm pretty confident that if we do
it properly, innovation will naturally take place. Yes, I know that there are
big challenges involved here in terms of resources and community consensus.
But those are part of any big change. One of the goals of this post is also to
try to propose a (kind of) well-defined set of topics for this "decadence"
discussion.

I know that dealing with all questions brought here involves a huge amount of
work. However, if we manage to respond in practice at least to a good part of
those, I would be extremely happy. :-) Therefore, it's quite important that we
take the opportunity brought by this discussion to draw some concrete proposals
for GNOME 3.0. In my opinion, the Release Team has an important role on the
coordination of the discussions about the needed process changes and the GNOME
Foundation Board should support the community by sponsoring hackfests, bringing
advisory board members to actively participate on this discussion, and much
more. Coincidentaly, I'm part of both (yay!) and I'll do my best (together
with my fellow release team and board members and the community in
general) to make this happen. Honestly, I don't know yet when I'm
gonna write the next post about possible solutions and practical actions
because, just like my [evil
twin](http://www.vuntz.net/journal/2008/06/12/473-future-of-gnome-evolution-revolution-words-words-words),
I'm still "still working with some great people on expressing our opinion in a
understandable way". I'm sure GUADEC will be a great opportunity to boost this
discussion.

If you read all this, you're my hero! Thanks! :-)
