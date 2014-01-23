---
date: '2009-09-14 17:21:10'
layout: post
slug: djangocon-2009-recap
status: publish
title: DjangoCon 2009 Recap
wordpress_id: '127'
categories:
- Django
- Python
---

After catching the great videos from last year's first DjangoCon I looked forward to attending this year.  I'm glad I went.

We'll be discussing "What did we learn at DjangoCon?" at this Thursday's Django Seattle. See [http://www.djangoseattle.org](http://www.djangoseattle.org) for more details.

In the meantime, here are some high-level take-aways:



	
  * Should JavaScript and RESTful services be part of the Django core?  JS is even more useful/powerful with the latest fast JS engines in Chrome, Firefox and Safari/Webkit. Competitor Rails builds in RESTful features - some promising ones for Django include django-piston and django-roa.  I liked how Ted Leung talked about "science experiments" and posed many ideas on what we may want to experiment with to get right before approaching Django core.

	
  * Git - Though this doesn't directly relate to Django, DVCS systems like Git and Mercurial are in wide use.  SVN is a given, but now feel I need to know Git and Mercurial well - since popular projects are using these.  I also wanted to pick a "pet" DVCS to use as my default too.  I've chosen Git (mainly because of git-svn and GitHub), but will be using Mercurial as well.

	
  * Django Tips and Tricks - Many to pick from, but I liked Query.as_sql() method to show the SQL the Django ORM generates on your behalf, the flexibility of using "signals" to loosely couple functionality (see django-signals-ahoy on bithub), reusing other Python WSGI middleware (such as repoze.bitblt, repoze.squeeze, repoze.profile), pylint/djangolint, class-based views, db schema migrations with South, much faster test speeds in Django 1.1, various test utilities floating around, talks on performance, etc.


* Django jobs are growing, and [Django also a popular platform for Start-ups](http://ping.fm/WpCf4).

* Check out the [DjangoCon2009 Wiki](http://djangocon.pbworks.com/Slides) for slides and presentations.
