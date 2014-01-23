---
date: '2009-09-02 21:11:57'
layout: post
slug: snow-leopard-smooth-except-python-3264-cocktail
status: publish
title: Snow Leopard Smooth Except Python 32/64 Cocktail
wordpress_id: '88'
categories:
- Django
- Plone
- Python
- Snow Leopard
- Zope3
---

**UPDATE: Thanks to the helpful commenters, I found success getting an older Zope instance running on Python 2.4 on Snow Leopard using buildout.**

**NOTE: This post is for installing Python 2.4 on a brand new Snow Leopard Instance.** If upgrading on top of Leopard, you may have to update easy_install, macports, etc.  More Googling around may be required.**
**

Though I had to create two buildouts to get this to work -- is there a way to get this into one buildout?

I first tried to create one buildout by combining  Florian Schulze's buildout recipe with a standard Zope recipe -- but since initial bootstrap was run by Python 2.5, I couldn't get the Zope instance to use the new Python 2.4. **So I first ran a buildout to build Python 2.4 (using OSX-installed Python 2.5), then used that new Python 2.4 to run bootstrap.py on the Zope 2.8.x buildout.**

Here's the recipe I used to just build Python 2.4 (requires Florian's buildout, see Alexander Limi's comment below for where to find this):

    
    [buildout]
    #extends = src/snowleopard.cfg     # no longer required as Joe mentions below
    python-buildout-root = ${buildout:directory}/src
    parts -=
       ${buildout:python25-parts}
       ${buildout:python26-parts}
    
    [install-links]
    prefix = /opt/local


Then I ran a simple Zope 2.8 buildout to see if it would compile (using new Python 2.4 to bootstrap), and it did!

    
    [buildout]
    parts =
       zope2
       instance
    
    [zope2]
    recipe = plone.recipe.zope2install
    url = http://www.zope.org/Products/Zope/2.8.9.1/Zope-2.8.9.1-final.tgz
    
    [instance]
    recipe = plone.recipe.zope2instance
    zope2-location = ${zope2:location}
    user = admin:admin
    http-address = 8080
    debug-mode = on
    verbose-security = on




* * *



Here is my initial post:

I have to say -- most everything I've installed on a fresh Snow Leopard install has worked flawlessly and swiftly -- except for (the minor inconvenience of) iStat not working.  **UPDATE: iStat 2.0 is available for Snow Leopard now.** _There's a new beta of MenuMeters too for Snow Leopard_.

There are also nice subtle improvements, see Mac Life's [100 Top Snow Leopard Tips, Trick and Features](http://www.maclife.com/article/feature/100_snow_leopard_tips_tricks_and_features) for improvements to Preview, Expose, Stacks, etc.  I've very happy with the upgrade.

Now for the bad news for those like myself who depend on Python 2.4 for Plone, since many versions of Zope require Python 2.4.  _I also use Python for Django, though that should run fine on Python that shipped with Snow Leopard._

You can read many of the initial details around the web, but here's what I've experienced and have been able to put together:



	
  * Note that these details are for a fresh Snow Leopard install - there are a different set of issues if you're upgrading over your existing Leopard.  **NEW: "Clark's Tech Blog" has a nice write-up about **[upgrading Python after upgrading Leopard to Snow Leopard](http://www.libertypages.com/clarktech/?p=719).

	
  * Snow Leopard ships with Python 2.5.4, and this runs as a 32-bit application.

	
  * I also need 2.4 branches of Python too, so I tried rolling my own (as usual) and it didn't compile.  I then followed that thread for awhile.

	
  * I then thought I pulled a fast one when I compiled from MacPorts and everything ran great!

	
  * ... but then I compiled Zope, and attempted to run an instance.  I saw a mysterious "No such file or directory" error.  Hmmm, I can navigate to that file, but running the script with my new Python interpretor was causing this error.

	
  * After digging around with Activity Monitor, I discovered that the Python I built from scratch was running as a 64-bit app -- while the Python that comes with Snow Leopard was only running 32-bit -- which is telling, since most everything else on Snow Leopard is running 64-bit.

	
  * Guessing that the the mysterious "No such file or directory" (when the file and directory did indeed exist) was due to a **weird cocktail of 32-bit pieces living with 64-bit pieces**.

	
  * My latest theory was that I needed to figure out how to build Python as 32-bit.  I played with Macports and various architecture settings to hardwire this, but long-story-short -- the architecture override isn't used everywhere -- so parts still compile natively as 64-bit on Snow Leopard.

	
  * **The best thread on the topic (that's steadily growing) is here: [http://bugs.python.org/issue6802](http://bugs.python.org/issue6802) with msg92153 left today**, which basically offers some additional settings for compiling Python as a 32-bit app (for Python 2.6).  Also mentions that Snow Leopard did some magic to get Python 2.5 working as a 32-bit app.**
**

	
  * My hope is that once "32-bit" Python 2.4 happens, the rest of the Zope install, etc, will be back to the good ol' days in Leopard.


**Plan B's:**

Otherwise, to save some headache, I'm wondering about installing a small Linux distro on VMWare as a local mini web-server where I can easily install Python and Zope -- though that's a bit of a pain too.

Luckily I also have my old Leopard in a separate partition (see my [Extra life for my MacBook Pro with Snow Leopard and inexpensive hardware](http://www.evolvingbits.com/2009/08/29/extra-life-for-my-macbook-pro-with-snow-leopard-and-inexpensive-hardware/) blog entry) and can boot that if necessary to work on various Zope/Plone sites (that required Python 2.4) while this is all being sorted out.

Now time to see if I can get 32-bit Python 2.4.6 compiled and installed, while waiting for more patches and information to appear...
