---
layout: post
title: "Favorite Monday Talks at 360iDev 2012"
date: 2012-09-10 17:24
comments: true
categories: [iOS, JavaScript, 360iDev]
---
My favorite talks are the developer-heavy ones. Here were three I enjoyed today.

## Advanced Debugging Code (on Sunday)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Kendall Helmstetter Gelner, [@kendalldevdiary](http://twitter.com/kendalldevdiary), [Slides (pdf) and Sample Project on Github](https://github.com/KiGi/AdvancedDebuggingCode)

* This talk was chalk full of debugging goodness: logging, instruments, LLDB, breakpoints, ARC (less code == less to debug), Pony Debugger, Charles, Core Data.

## Developing for Reuse

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Andria Jensen, [@andriajensen](http://twitter.com/andriajensen), slides: [http://bit.ly/U3RA4V](http://bit.ly/U3RA4V)

* Andria had a great presentation and her slides are very useful for best practices in modularizing code for Objective-C and Xcode.

* This very topic was resonating with me last night ([iOS Automated Testing: Refactored](http://blog.evolvingbits.com/blog/2012/09/09/ios-automated-testing-refactored/)), and although she didn't cover the unit testing pieces, she went way beyond the first step of `git submodule` modularization and went into Xcode workspaces, static libraries, bundles, and categories.

## PhoneGap

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Andrew Trice, [@andytrice](http://twitter.com/andytrice)

* Andrew is a great resource and has some interesting projects on [Github](https://github.com/triceam) such as app-UI,  Lil-Doodle, Fresh-Food-Finder.

* "What's the difference between PhoneGap and Cordova?"  They're the same code base right now.  Cordova is the open source project, and PhoneGap is Adobe's distribution, and they own the PhoneGap name.

* Some libraries he uses are Backbone.js, and [Leaflet](http://leaflet.cloudmade.com) ("An Open-Source JavaScript Library for Mobile-Friendly Interactive Maps by CloudMade")

* He showed some good plugins, like [second screen support](https://github.com/triceam/phonegap-plugins/tree/master/iPhone/ExternalScreen) (native PhoneGap code to support multiple screens).  PhoneGap Plugins are nice since they give JavaScript access to anything you can do in the native layer, and there are many plugins that have already been developed.

* Presentation Suggestion I have: Many of the PhoneGap examples are business apps (Apple Store, LinkedIn, BBC Olympics, Zombie Jombie, Wikipedia, Untappd, Bit Timer, US Census Browser) though there are JavaScript libraries out there (such as lime.js) that make PhoneGap a nice platform for gaming too.

## "Stop it! That Hurts!" Common iOS Anti-Patterns

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;By Carl Brown, [@carlbrwn](http://twitter.com/carlbrwn), slides: [http://t.co/JRWPcd1B](http://t.co/JRWPcd1B)

* His whole talk is great. Topics include Error handling, Asynchronous, Date, Security, Caching, View tagging, Core Data results, don't mix read-only and read-write data.

* He's in Austin, home of SXSW Interactive where it "Looks like any idiot can make an App", sees a lot of (bad) code

### Suggestions

* Read good code -- and NOT these from Github Objective-C "Most Watched": three20, asi-http-request, AFNetworking, facebook-ios-sdk, Restkit.

* His "Rocket Engine" for Responsive Code (to make sure you're not doing much on main thread): `NSAssert(![NSThread isMainThread], @"BOOM");`

* Uses NMVC pattern ("N" for Network), essentially networking happens at the data layer and not throughout code.

* Carl had some criticisms with RestKit, so I asked him more details after the talk.  The criticism is more that Restkit tries to abstract what's local and what's remote, and it's not always clear what's happening. He turned me onto a nice recommendation: [MagicalRecord](https://github.com/magicalpanda/MagicalRecord) which is a Category for Core Data that handles fetching of remote data and adding to Core Data.

### Summary

* Program sober and rested, if possible

* Leave other language's patterns at the door

* Program idiomatically ("The specific grammatical, syntactic, and structural character of a given language.")

* Don't fight the frameworks