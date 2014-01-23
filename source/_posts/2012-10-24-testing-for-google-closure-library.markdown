---
layout: post
title: "Testing JavaScript Code Running Google Closure Library using Mocha and PhantomJS (or Jasmine)"
date: 2012-10-24 12:24
comments: true
categories: ["JavaScript", "testing"]
---

Here are several options for setting up JavaScript unit testing for code built with the Google Closure Library, albeit these options are helpful for testing a wide variety of JavaScript projects.

Google Closure Library is self-described as a "broad, well-tested, modular, and cross-browser JavaScript library."

We're using the [LimeJS](http://www.limejs.com) HTML5 game framework, which is built on this library.

## Our Contestants

### 1. Headless testing with Jasmine 1.2

Jasmine works well. There are two approaches you can use: an HTML runner with jasmine.js, or the Ruby-based runner. Originally we were hoping to take the same approach as the Ruby-runner (with all batteries included, including easy headless testing) but using Mocha and Node.js instead to be on a full JavaScript stack.  Though we ended up having to go to an HTML runner + mocha.js to get the DOM testing to work, in scenario 3 below.

*In hindsight, by ending up with the HTML + JS approach in scenario 3, Jasmine and Mocha + PhantomJS are very similar approaches.*

### 2. Mocha testing on Node.js

Mocha testing on Node.js works well (easy setup, no html test runner required), but I wasn't able to get headless DOM working. If your tests don't require DOM, this is a good way to go. *One issue: It takes more effort to debug tests with breakpoints because the code is running on node.js. In the other scenarios, you can just add a `debugger` line and debug the tests in the browser.*

### 3. Headless testing with Mocha and PhantomJS

**Our winner**: Headless testing with Mocha and PhantomJS via [mocha-phantomjs](https://github.com/metaskills/mocha-phantomjs) allows us to use JavaScript tooling, headless DOM testing and a nice Jasmine BDD style for writing tests.

### 4. Testing with the Google Closure Library testing framework

You can use the Google Closure Library testing framework, which is more of a traditional JUnit style framework and not a BDD-style framework like Jasmine or Mocha. Please check out the Closure documentation for more info.

## Let's Get Testing

Here's how each can be setup.

Assume you keep your tests in a `my-project/spec` folder and your code is under a peer `my-project/scripts` folder. Assume all test-related files discussed below are in the `./spec` folder and that tests are kicked off via a script in that folder.

### 1. Jasmine

This is a personal favorite. It has all batteries included and doesn't need a separate HTML runner for DOM testing if using the Ruby Gem. We liked this approach, and tried to do it with Mocha + node.js (to get the same features as the Ruby Gem, but on a JavaScript stack) though ultimately went with Scenario 3 below.

For general setup of headless Jasmine testing, see my [jasmine-headless-boilerplate](https://github.com/briangershon/headless-jasmine-boilerplate) repository.

Once setup, to tailor for Google Closure Library, in `javascripts/support/jasmine.yml` (setup by default with `jasmine init`) add your project's base.js and generated deps.js file to `./spec`.

    src_files:
        - scripts/libs/closure/closure/goog/base.js
        - scripts/deps.js

You can then just create a standard Jasmine test file with goog.require() statements at the top to bring in the module dependencies:

    goog.require('the.module.I.am.testing');
    goog.require('a.dependency');

    describe("the.module.I.am.testing", function () {
        
    });

### 2. Mocha Testing on Node.js

After setting up node.js and npm, you can create a package.json file to make it easy to setup all the dependencies by just running `npm install` in your `./spec` folder.

If you have a script that kicks off the tests, you can optionally add that to the "scripts > tests" key like seen below so that you can just run `npm test`.

Also, you'll need to use the [nclosure](https://github.com/gatapia/nclosure) library to allow node.js to bring in dependencies via goog.require().

In `./spec` create 3 files:

* closure.json to tell nclosure library where your files are

* package.json to setup all your node.js dependencies

* a run script

Here are examples:

closure.json

    {
      additionalDeps:['../scripts/deps.js'],
      closureBasePath:'/this/has/to/be/an/absolute/path/in/my/experience/scripts/libs/closure/'
    }

**It took some time to figure out the right file paths**. Basically:

* "additionalDeps" should be a relative path from where you're running the script that runs the tests. If you're running tests from a `./spec` folder, and the code lives in a peer (to `./spec`) ../scripts folder, use the example above.

* However the closureBasePath only worked as an absolute path, plus you leave off the trailing `/closure/goog` (since often closure is in a lib/closure/closure/goog directory structure).

I assume this could be fixed with either a patch to nclosure or maybe I wasn't doing something correctly. I also tried setting this as a parameter to the actual `require('nclosure').nclosure();` call at the top of the tests, but no difference. This would need to be solved to make it easy for a team to run tests locally.

package.json

    {
      "name": "our-test-framework",
      "version": "0.0.0",
      "description": "## Unit Tests",
      "main": "index.js",
      "scripts": {
        "test": "sh runtests.sh"
      },
      "repository": "",
      "author": "",
      "license": "BSD",
      "dependencies": {
          "chai":"~1.3",
          "sinon": "~1.5",
          "nclosure": "~0.4",
          "mocha": "~1.6"
        }
    }

runtests.sh

    #!/bin/sh
    ./node_modules/.bin/mocha --recursive --timeout 10000 --reporter spec your/folder/to/your/specs

Here's an example test file:

    require('nclosure').nclosure();

    goog.require('my.module.goes.here');
    goog.require('one.of.your.dependencies');

    describe("my.module.goes.here test", function () {
        
    });

### 3. Mocha Testing on PhantomJS (node.js not required)

This is the current winner for our specific needs. It's mainly JavaScript based, runs headless DOM tests, and supports a nice BDD syntax.

This has some additional dependencies beyond the setup above:

* Install PhantomJS, which on OSX is as easy as `brew install phantomjs` via Homebrew.

* Bring down mocha-phantomjs.coffee and the mocha-phantomjs folder from [mocha-phantomjs](https://github.com/metaskills/mocha-phantomjs) and put those in your `./spec` folder.

* Bring in dependencies mocha.js and mocha.css from root of [mocha repository](https://github.com/visionmedia/mocha)

* Bring in third-party libraries like [expect.js](https://github.com/LearnBoost/expect.js/) and [sinon.js](http://sinonjs.org) used by test runner HTML below. (We started with Chai's "expect" assertion framework, but the assertion code didn't nicely pass linting, so went with the very similar expect.js)

Instead of using the ./mocha test runner, your run-script can call each test like so:

    phantomjs mocha-phantomjs.coffee javascripts/mycontroller_spec.html
    
In addition to your test js file, you need an html file test runner to setup DOM for your tests.

Here's an example of mycontroller_spec.html:

    <html>
      <head>
        <title>Unit Tests</title>
        <meta charset="utf-8">
        <link rel="stylesheet" href="../../../node_modules/mocha/mocha.css" />
      </head>
      <body>
        <div id="mocha"></div>
        <script src="../../../../scripts/libs/closure/closure/goog/base.js"></script>
        <script src="../../../../scripts/deps.js"></script>
        <script src="../../../javascripts/support/sinon-1.4.2.js"></script>
        <script src="../../../javascripts/support/mocha.js"></script>
        <script src="../../../javascripts/support/expect.js"></script>
        <script>
          mocha.ui('bdd'); 
          mocha.reporter('html');
        </script>
        <script src="mycontroller_spec.js"></script>
        <script>
          if (window.mochaPhantomJS) {
            mochaPhantomJS.run();
          } else {
            mocha.run();
          }
        </script>
      </body>
    </html>

The mycontroller_spec.js test file doesn't require any special code, just using the normal goog.require():

    goog.require('my.module.goes.here');
    goog.require('one.of.your.dependencies');

    describe("my.module.goes.here test", function () {
    
    });

## Other thoughts and ideas

* For tests requiring DOM: Is it possible to substitute zombie.js instead of phantomjs?  The main reason is that then the whole stack could be in node.js and has fewer dependencies (since it wouldn't require phantomjs and mocha-phantomjs).

* Selenium is another option for testing code against DOM on real browsers.

## References To Bookmark

* [expect.js](https://github.com/LearnBoost/expect.js/)

* [Sinon.JS](http://sinonjs.org/docs/)

* [Mocking Requests With Mocha, Chai and Sinon](http://robdodson.me/blog/2012/05/28/mocking-requests-with-mocha-chai-and-sinon/)
