---
layout: post
title: "iOS Automated Testing: Refactored"
date: 2012-09-09 15:53
comments: true
categories:
- Programming
tags: [iOS, JavaScript, testing, 360iDev] 
---
My mobile projects lately include various combinations of JavaScript and Objective-C. Usually either 100% native iOS, or JavaScript running on a native iOS (or Android) layer.

I also like to dabble with various projects, and am tired of the heavy weight of setting up new Xcode projects when I just want to experiment with some concepts.  The JavaScript side is already much lighter.

I consider it heavy because:

* I have various snippets strewn across projects, and

* getting Xcode tests up and running sucks the life out of me when I just want to jump into some code. *True, new Xcode projects do create boilerplate tests, but still requires setup for including other 3rd-party libraries like OCMock.*

An example scenario:

* Today I'm dabbling with geofencing in an app, but tomorrow I may want to use that code in a hybrid Cordova/PhoneGap app, Thursday I might want to refactor geofencing into something else.

I'm very happy with Jasmine for testing JavaScript, since it's easy to setup and use.  I created a [jasmine-headless-boilerplate](https://github.com/briangershon/headless-jasmine-boilerplate) project that is a starting place for those wanting to setup and run Jasmine JavaScript tests with their projects, and also be able to run it headless on their CI server or on Travis CI.

## The New Plan

So for my Objective-C code, I have formulated a plan to deal with both of these at once:

* Modularization: I'm going to focus on moving code out of specific apps and into a personal library.  I'll then include that as a `git submodule` in any new project I begin, whether native or hybrid.  I've been doing some of this modularization already by avoiding the impulse to add too much code directly into UIViewControllers, but rather putting code into custom classes that are then used by the UIViewController.

* Testing: The personal library will also be housed in a bare bones Xcode project, which will only have unit tests and 3rd-party testing libraries (like OCMock), so that I can ensure that code is tested before it gets used in my projects.

When I'm done, I'll have a versatile and well-tested library that I can quickly add to any project or experiment.

### Here's a Starter Project to play with: [Enjoyable iOS Testing](https://github.com/briangershon/enjoyable-ios-testing)

## Other Xcode Testing Starter Projects and Resources

I'm now looking around for bare bones Xcode starter projects to use:

* [Xcode-Templates](https://github.com/magicalpanda/Xcode-Templates) looks interesting

* [Cedar](https://github.com/pivotal/cedar) looks even more interesting since it's closely related to Jasmine and looks like it will blend well with my JavaScript work.
