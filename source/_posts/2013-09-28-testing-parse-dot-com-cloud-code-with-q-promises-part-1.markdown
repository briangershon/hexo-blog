---
layout: post
title: "Testing Parse.com Cloud Code using Q Promises: Part 1"
date: 2013-09-28 17:07
comments: true
categories: ["Parse.com", "JavaScript"]
---
I've been playing with Parse.com Cloud Code, and wanted to write more code offline so I didn't have to keep pushing to the cloud, plus wanted to use Test Driven Development.

I also had seen their blog post [What’s so great about JavaScript Promises?](http://blog.parse.com/2013/01/29/whats-so-great-about-javascript-promises/) and decided that was the best way to go for handling async logic.

For testing and mocking, I discovered the `Q` promise library which is fantastic. For a great intro listen to the [037 JSJ Promises with Domenic Denicola and Kris Kowal](http://javascriptjabber.com/037-jsj-promises-with-domenic-denicola-and-kris-kowal/) podcast and see [Q Getting Started and Tutorial](http://documentup.com/kriskowal/q/).

The problem I ran into was that the Parse.com promise library handles error-handling differently than the Promises/A+ spec (instead it follows jQuery's implementation) so then started trying to create a mock of a Parse.com promise, but this was a bit tricky and I wasn't happy with result.

Then I finally had the thought to replace the Parse.com promise implementation with `Q`. That way I could implement my Cloud Code with `Q` and also write my tests with `Q`.

Here's an initial experiment of using `Q` with Parse.com Cloud Code.

<em>How to run: I just created a new Cloud Code project with the Parse command-line tool `parse new` and then grabbed q.js via an `npm install q` and copied q.js into the `./cloud` directory.</em>

{% gist 6747919 %}

[Here's the code on gist.github.com](https://gist.github.com/briangershon/6747919/)