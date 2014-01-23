---
date: '2009-02-01 16:18:44'
layout: post
slug: packed-house-at-northwest-python-day-2009
status: publish
title: Packed House at Northwest Python Day 2009
wordpress_id: '52'
categories:
- Google App Engine
- Python
- Seattle
- Web Collective Inc
---

I enjoyed hanging with the local Python crowd yesterday in Seattle for [Northwest Python Day 2009](http://www.seapig.org/NorthwestPythonDay).

As usual, Python is popular in many realms.


## Who attended?


We started with quick introductions - a nice mix of folks with some traveling from Portland OR, Vancouver BC and even one from Chicago and DC.  Many folks using Python -- several announcing Python job openings.  People were from various organizations such as University of Washington, NOAA, ONENW, Web Collective, NPower, LexisNexis, Microsoft, Sun, and many interesting companies I didn't catch the names of.


## Quick Highlights


We started with a lightning talk with tips on moving your code toward Python 3.0 (running Python 2.6 with -3 option; using __future__, running 2to3).

Then saw a light-weight web framework called [Werkzeug](http://werkzeug.pocoo.org/) - I like its idea of decorating a Python view function with its URL mapping [e.g. @expose('/') to connect a view with the root of the site].

We then heard about the ease of leveraging [buildbot](http://buildbot.net/trac) for testing.

NOAA started the presentations with their CAMEO Chemical modeling application, "a Pylons-based web app wrapped in a wxPython interface for desktop use."  There were various complications making this work cross-platform on both IE and Safari, but overall successful.  Chris has high hopes for upcoming wxWebKit (which wasn't quite mature enough at the time they were developing their app), and might consider pyQT or pyGTK for future projects.

University of Washington's Beraber was interesting - a way to offer open source cloud computing (via a Python-based VM) by sharing your computer safely with others, and being able to run programs on many computers around the world.

After lunch, lightning talks resumed with Sphinx, an RST based system for writing documentation for your code (used for Python's documentation).

We then saw NodeBox, "a Mac OS X application that lets you create 2D visuals (static, animated or interactive) using Python programming code and export them as a PDF or a QuickTime movie."  I checked out their website -- some cool plugins like modeling of flocks.  You could probably make some very cool desktop wallpapers with this too.

If you'd like to play with virtualization and open source, [Derek Simkowiak](http://cool-st.com/wordpress/) is working on a program called "vmshell" that allows you to more easily manage virtual sandboxes.  Management of VMs was mentioned as something missing from many open source VM solutions.

Our first afternoon presentation talked about the benefits of high-level languages like Python and benefits over lower-level languages like C++ or Java.  Mark McWiggins presented good arguments for why organizations may want to consider Python over these other languages.

[Sage](http://www.sagemath.org/), and its 5+ million lines of code, offers open source math modeling.  For those that need Mathematica, Magma, Maple, or Matlab power, Sage was impressive -- from interacting with and showing complex math formulas in Python and Javascript, to live 2D/3D plotting, to importing the library into your own Python program and going to town.  One of its innovative features (from a web dev perspective) is writing a math function (in Python) which you want to interact with it on the web -- instead of creating your own web form, you can decorate your function with @interact, which introspects the function parameters and automatically creates a web form for that function.

After having played a bit with Google App Engine, it was nice to hear a real-world experience about using this in a production project.  Web 2.0 apps can be a sweet spot for GAE, though there are differences with other traditional web development methods that may help determine if your app fits GAE or not.  I won an online O'Reilly book on this topic.

I had seen mention of Cython, but hadn't investigated.  Cython is a way to compile your Python code in C code for major speed improvements.  It has some cool profiling features like an interactive web-based code display that uses light-to-dark color-coding to show which Python code lines are the slowest, and allows you to click on the line to see the actual C code that was generated.

The last presentation was by Sun, who are investing in Python (and other languages in addition to Java) due to their popularity by programmers.  They are also investing in Jython (adding more resources than before) to bring this up to latest versions of Python 2.x, and some work on the JVM to support languages other than Java.


## Pycon


[Registration just opened for PyCon 2009](http://us.pycon.org/2009/about/) (in March) in Chicago.

I plan on attending this year, hope to see you there!


## Thanks!


Thank you Seattle Python and the University of Washington for hosting!
