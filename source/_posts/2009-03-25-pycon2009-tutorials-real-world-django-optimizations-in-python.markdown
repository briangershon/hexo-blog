---
date: '2009-03-25 19:54:27'
layout: post
slug: pycon2009-tutorials-real-world-django-optimizations-in-python
status: publish
title: 'PyCon2009 Tutorial Recap: Real World Django / Optimizations in Python'
categories:
- Programming
tags:
- Django
- Plone
- Python
- Zope3
---

I primed the pump on the flight to PyCon by catching up on my reading. "Expert Python Programming" (Tarek Ziade) reminded me that I wanted to play with ipython shell and virtualenv (just learned today about the handy extension "virtualenvwrapper"), and reinforced and offered many great Best Practices.

**Optimization Tutorial**

I then got on my geek at "Faster Python Programs through Optimization" (Mike Müller of Python Academy), where we dove deeper into profiling and tips on improving speed or saving memory.

Some paraphrased guidelines to consider before you start optimizing (which were also reinforced in the "Real World Django" tutorial which I'll chat about next):



	
  * Make sure your program is really too slow - could be other factors like network traffic, database, etc.

	
  * Don't optimize as you go - might ultimately not need to spend that time.  Also working code is always important first.

	
  * Only consider realistic use cases and user experience


We played with the profiling tools (profile, cProfile, time, pystone, heapy) and used them to compare various techniques:

	
  * xrange and also Generators shaved off time by not having to allocate memory for large data sets.

	
  * use built-in types as much as possible (including some newer collection classes)

	
  * iterating and appending strings by first appending to lists, then using a join statement to create large strings (versus building strings via += and loops)

	
  * One new one for me was converting lists to Sets before testing for membership of an item in the list, which is fast due to Set optimizations.

	
  * The tutorial also covered pysco, processing and numpy modules, as well as caching techniques.


**Real-world Django Tutorial**

This very aptly named presentation by Jacob Kaplan-Moss and James Bennett was excellent for those of us who develop and deploy Django websites.  The full skinny (with link to slides) is here: [http://jacobian.org/speaking/2009/real-world-django/](http://jacobian.org/speaking/2009/real-world-django/)

Some highlights for me included:



	
  * Focus on tight Django Applications that promote reuse while also breaking a website into components. Benefits of also leveraging packaging up your own components.

	
  * Gain flexibility by leveraging Django Managers, and they help encapsulate behavior behind an API.

	
  * Can extend models via new (in Django 1.1) Proxy subclasses.

	
  * Lots of discussion and recommendations for testing -- from unit testing, through functional testing, and then browser-based functional testing. Yep, you need them all. I'd like to play more with Twill and Windmill.

	
  * Automating deployment - including options like virtualenv (and virtualenvwrapper), Ian Bicking's [pip](http://blog.ianbicking.org/2008/10/28/pyinstall-is-dead-long-live-pip/) ("pip installs packages"), zc.buildout, and [Fabric](http://pypi.python.org/pypi/Fabric/).  _zc.buildout's power was emphasized (with its recipes, etc) was a bit overshadowed by comments on lack of documentation._ I'd like to give pip and Fabric a try.

	
  * Apache + mod_wsgi is now a preferred platform for server Django sites (or at least much more consistent performance and memory-usage wise than Apache + mod_python).

	
  * Definitely flip through the session slides!  _These were just some highlights for me out of 189 slides of useful information._


Various tidbits for the next few days here at PyCon:

	
  * Open Space sessions come highly recommended

	
  * There's a [heavy testing thread](http://us.pycon.org/2009/conference/talks/?filter=testing) throughout conference (10 sessions worth!)

	
  * [Friday 11am](http://us.pycon.org/2009/conference/schedule/event/P37/): Using Windmill

	
  * [Saturday 4:15p](http://us.pycon.org/2009/conference/schedule/event/76/): Ian Bicking's session (creator of PIP and virtualenv, among many other topics)

	
  * [Sunday 10:35a](http://us.pycon.org/2009/conference/schedule/event/88/): Panel: Functional Testing Tools in Python

	
  * ... though it will ultimately be tough to pick and choose from all the great topics!


Time for some sleep... more tutorials tomorrow, then 3 days of conference, then 4 days of sprints!

ps: It's been great to see familiar faces from the Zope and Plone communities, which is often where I "get my Python on".  Lately I'm also doing a lot of Django, so enjoying all the synergy around Python here at PyCon2009!
