---
layout: post
title: "Favorite Tuesday Talks at 360iDev 2012"
date: 2012-09-12 11:46
comments: true
categories:
- Programming
tags: [iOS, 360iDev]
---
Here were four talks I enjoyed, plus Game Jam.

## Poking a Hole in the Sandbox, using URLs on iOS

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Greg Pierce, [@agiletortoise](http://twitter.com/agiletortoise), [Slides](http://agiletortoise.com/blog/2012/9/11/360idev-poking-a-hole-in-the-sandbox-using-urls-on-ios.html)

* Lightweight local messaging between apps.

* A way to test if certain apps are installed, great for cross promotion too.

* A protocol for iOS interapp communication [http://x-callback-url.com](http://x-callback-url.com)

## It’s All in the Tools

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Nathan Eror, [@neror](http://twitter.com/neror), [Slides](http://neror.us/JNhY)

* How to wield Xcode with keyboard shortcuts (Jump bar: `^[1-6]`, learn keys from top menu items `View` and `Navigation`), Behaviors, breakpoints (logging, sounds, shell scripts, llvm allows breakpoints without restarting app), and powerful lldb debugging (formatters, summarizers, python integration, `.lldbinit`).

* Uses `make` to automating (things like removing sqlite databases), supports autocompletion. See his blog entry on this.

* Mountain Lion has Python bindings for Cocoa -- see a nice Quartz example in his slides.  This was news to me, and after Googling around didn't find much into about this.

## Creating Container View Controllers

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Bob McCune, [@bobmccune](https://twitter.com/bobmccune)

* These are now easier to create in iOS 5+. A subtle API for adding/removing child controllers, get children, new callbacks. Only use this API within your container. Avoid common mistakes: Outside callers (since invalidates containers view of the world), disobedient children, meddling parents (let children be children)

* Demo code is here: [https://github.com/tapharmonic](https://github.com/tapharmonic)

## Galcon

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Phil Hassey, [@philhassey](https://twitter.com/philhassey)

* Phil following his gaming development passions with [Galcon](http://www.galcon.com) and other games, including his new [Dynamite Jack](http://www.oneclickmac.com/dynamite-jack-for-mac-review/).

## Game Jam (7pm to 7am)

* Phil Hassey's Galcon talk motivated me to give Game Jam a try.

* I enjoyed this for several hours before drinking and socializing set in.

* Had fun with cocos2d and box2d. 