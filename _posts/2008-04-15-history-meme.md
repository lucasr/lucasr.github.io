---
id: 210
title: History meme
date: 2008-04-15T20:47:05+00:00
author: Lucas Rocha
layout: post
guid: http://blogs.gnome.org/lucasr/2008/04/15/history-meme/
permalink: /2008/04/15/history-meme/
categories:
  - Free Software
  - General
  - Archived
tags:
  - git
  - history meme
  - vim
---
<pre>history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
130 vim
106 cd
74 ls
33 make
28 git
24 grep
19 sudo
18 rm
12 svn
11 touch</pre>

Yeah, yeah, I love vim!
