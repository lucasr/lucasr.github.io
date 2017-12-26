---
id: 2088
title: Micro Commits
date: 2011-01-29T02:47:34+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2088
permalink: /2011/01/29/micro-commits/
image: /wp-content/uploads/2011/01/branches.png
categories:
  - Free Software
  - General
  - Software
tags:
  - bisect
  - cherry-pick
  - code
  - code base
  - code review
  - development
  - discipline
  - dvcs
  - Free Software
  - git
  - GNOME
  - hacking
  - micro commits
  - planet
  - review
  - Software
  - store
  - subversion
  - svn
---
It's been a few years since I became a full-time git user both at work and in
the FLOSS projects I contribute to. I guess there's no need to argue in favour
of git at this point as it has become a sort of given on any sane software
project—along with some other DVCS. I can't really remember anymore how my life
with Subversion was. Sad, I guess...

One of my favourite cultural shifts in software development brought by DVCS is
the use of micro commits. JP has just
[blogged](http://blog.jprosevear.org/2011/01/28/git-micro-commits-and-workflow/)
about it. Here are what I consider the most useful benefits of micro commits.

**Tell a story.** When you send one huge patch implementing a feature or fixing
a bug, you're completely hiding the incremental process through which you
reached your final solution. On the other hand, a well written series of micro
commits tell the reviewers the whole story of your code changes, step by step.

**Discipline.** If you want to tell a coherent story with your commits, you
obviously need to organize them properly. Each commit should be a
self-contained step towards the new feature or bug fix. Writing good patch
series requires quite a bit of practice. It's a very good exercise in terms of
splitting a complex solution into a well-defined sequence of code
changes—leading to more disciplined development practices.

**Better code reviews.** Because micro commits are, well, small, they are much
easier to review because they do only one thing at a time. You get better code
reviews as a consequence because the patches tend to contain no unrelated code
changes.

**Bisect and cherry-pick.** Huge commits makes bisect and cherry-pick close to
useless. And you don't want that! Micro commits make it much easier to spot
what caused a regression. Plus, they make it very easy to cherry-pick commits
from one branch to another.

Git makes it utterly simple to move, split, squash, reorder, and remove commits
providing the best ways to write good series of micro commits. It allows you
to [look like the perfect
developer](http://people.gnome.org/~federico/news-2008-08.html#git-rebase-interactive)
to the outside world by incrementally fixing your commits before submitting
your patches for review. If you're not micro-committing yet, you should.
