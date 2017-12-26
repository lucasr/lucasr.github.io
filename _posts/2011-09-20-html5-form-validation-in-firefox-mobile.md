---
id: 2501
title: HTML5 Form Validation in Firefox Mobile
date: 2011-09-20T14:38:18+00:00
author: Lucas Rocha
layout: post
guid: http://lucasr.org/?p=2501
permalink: /2011/09/20/html5-form-validation-in-firefox-mobile/
image: /wp-content/uploads/2011/09/html5-form-fennec.png
categories:
  - Free Software
  - General
  - Mozilla
  - Software
  - Archived
tags:
  - development
  - feature
  - fennec
  - forms
  - Free Software
  - html
  - html5
  - javascript
  - Mobile
  - mozilla
  - planet
  - Software
  - validation
  - Web
---
My [patches](https://bugzilla.mozilla.org/show_bug.cgi?id=605365) to add HTML5
form validation support to Firefox Mobile have landed in trunk yesterday. This
feature has been available on desktop since Firefox 4 but it wasn't implemented
in Firefox Mobile until now.

In case you haven't heard about it, HTML5 supports [automatic input
validation](https://developer.mozilla.org/en/HTML/Forms_in_HTML#Constraint_Validation).
This means that your browser can take care of validating form fields for you—no
need to write custom JavaScript code to check for required fields or validate
common types of input such as numbers, emails, URLs, etc.

So, how does HTML5 form validation look in Firefox Mobile? Very similar to
Firefox on desktop. If you submit a form that contains any invalid data—an
invalid email address, a required field that was not filled in, and so on—the
form will not be submitted, all invalid fields will be marked with a subtle red
border, and the first invalid element will be automatically focused showing its
respective validation message (see image above).

As far as I know, the only mobile browsers that support HTML5 form validation
right now are Firefox and Opera. You can try this feature on our mobile
[nightly build](http://nightly.mozilla.org/). As usual, general feedback, [bug
reports](https://bugzilla.mozilla.org/enter_bug.cgi?product=Fennec), and
patches are welcome!
