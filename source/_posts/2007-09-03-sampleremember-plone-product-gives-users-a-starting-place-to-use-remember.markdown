---
date: '2007-09-03 16:31:11'
layout: post
slug: sampleremember-plone-product-gives-users-a-starting-place-to-use-remember
status: publish
title: Build your own remember-based content with sampleremember Plone product
wordpress_id: '12'
categories:
- Plone
---

Back in March, Andrew Burkhalter and I wrote a tutorial for creating new content-types based on _remember_, and as part of that created the _sampleremember_ Plone product.  Since then, I've had a couple of live project opportunities to put _sampleremember_ through its paces.

By September, I fixed bugs in _sampleremember_ and added some unit tests, so feel this is now a solid working example of  how to create your own remember-based content types.



**What is _remember_ (and _membrane_)?**

_The membrane_ product allows you to create Plone users (and groups) that are actually content-types - so you can workflow them, add attributes to them, etc.  _remember_ is based on _membrane_ and also adds the replacement Plone templates and functionality so that you can manipulate, reset passwords, login, etc using these new content types. Martin Aspeli uses _membrane_ in his [b-org](http://plone.org/documentation/tutorial/borg) tutorial if you want more info.

**You can find the _sampleremember_ product in the /examples folder inside of _remember_ as well as a walk-through tutorial in the /docs folder of _remember_. ** Note that the tutorial is a bit-dated, so the most up-to-date implementation is in _sampleremember_.

How do I automate setup of _sampleremember_ to use portal_quickinstaller?

One final issue I ran into that I didn't solve was trying to make my remember-based products quickinstall the three profiles it needs: _membrane_, _remember_, and its own.  I discovered that _remember_ didn't like to be uninstalled then installed again. _If you don't uninstall, but just reinstall, there isn't a problem -- but then an accidental uninstall seems like a time bomb waiting to happen._

So the best solution seems to be manually installing _membrane_ and _remember_ via portal_setup **only once for a site** and then add an Install.py script that simply runs my own product's generic setup profile.
