---
layout: post
title: "With Great JavaScript Comes Great Inspiration"
date: 2012-04-04 09:15
comments: true
categories:
- Programming
tags: ['JavaScript', 'jsconf2012', 'boot2gecko']
---
I'd say the theme of Day Two at JSConf 2012 was **inspiration**, and was another great day of talks:

* I think my favorite talk (best presentation, very pragmatic) was Jake Archibald's "Application Cache" -- why it's useful and the potholes you'll encounter while using it. You'll want to watch this video.

* The best demo for me was the presentation prior, Thomas Valletta's "The Web Game Console", where he talked about his experience developing his mobile game with HTML and JS. He wrote a Web Bowling game using HTML/JS on iOS as the controller, and a Node.js websocket server for displaying the bowling alley.  The source is on Github (so you can setup your own server if you want) and if multiple people play at the same time it turns into "battle bowling" with multiple balls at the same time.

* Project Bikeshed was a great demo too. Not only did its authors put on a great daily video series, but Bikeshed allows you to do many useful things such as importing Flash SWF files, automatically turning those into JavaScript and then allowing you to show, combine, manipulate, animate any of those elements and use them in your JavaScript projects.  He demo'd an iPad JavaScript game that was powered by Bikeshed.  You can also run Bikeshed on Node.js and send that to devices. With a one-line change, he showed running both scenarios.

* Ok, another great demo was on Open Data in the B-Track by Daniel Beauchamp & Edward Ocampo-Gooding. They actually packed about 7 small presentations into one and described their process of organizing a city hack-a-thon around Open Data and building a lot of apps for free for the benefit of your city and your community. Very inspired.

* The Node.js talk from Brian Ford inspired us with some interesting readings to check out (such as the "Thinking Fast and Slow" book) and the importance of leveraging communities outside of JavaScript, such as the experiences of the Ruby community.  He then had many concerns about Node.js repeating concurrency mistakes that Ruby had made. *Though I think I mainly left there with only some good book suggestions -- it felt like it ended abruptly since there was no time for questions (since presentation went long) and no specific next steps on how to avoid said concerns.*

* One of the **most inspirational** talks was 19-year-old James Whelton's "Changing the world one CoderDojo at a time". [CoderDojo](http://coderdojo.com/about-us/) is "a movement of free coding clubs for young people". Check out their site for a lot of inspiration and how to start a club yourself. Also turns out that JavaScript has been a very accessible language to use -- it requires no setup, is available everywhere, fun to work with, and can even land you a job down the road.

* Jacob Thornton's "Brûlons les musées" talk was also very entertaining, and you'll need to see the video. He led up to the power of the JavaScript community getting together more specifically around creating specs/tests (versus primarily getting together around an implementation), which then offer flexibility and healthy competition when implementing libraries that meet those specs. His example was creating Hogan.js, which is some ways was a rewrite of Mustache.js. The improvements were possible by leveraging the Mustache tests. Then Mustache was able to make improvements. By using the specs, separate projects were able to code and optimize independently.

* The final talk of the day was [Rick Falkvinge](http://falkvinge.net/)'s talk about politics, the Pirate Party and inspiration on how to change the world.  He told his story of how the Pirate Party has been able to make in-roads into mainstream politics, and what's possible.

## Green for Dinner

After the JSConf family photo, nine of us then went to a local vegetarian restaurant called [Green](http://greenvegetarian.com/) which was amazing.  The place was packed the whole time while the atmosphere was very easy going. They had a great variety of original and tasty foods.

## Boot2Gecko Phone

In the evening, I finally had a chance to play with Mozilla's Boot2Gecko phone and built a simple app. In [Accelo](https://github.com/briangershon/accelo) the JSConf logo floats around the screen and moves as you tilt the phone.

Development was fairly smooth and I was able to install my app as part of the Gaia update/install process, but didn't have luck yet setting it up to install as a stand-alone app.

Albeit since the app is solely HTML/CSS/JS it works just fine by visiting the site [http://accelo.evolvingbits.com/accelo/](http://accelo.evolvingbits.com/accelo/) on the Boot2Gecko phone (or even works on my Macbook Pro which apparently sends accelerometer events). However when viewing on iOS, the accelerometer events seem to be reversed, so not sure which implementation is off.

## Thank you

Thanks JSConf for another great year of new friends, bull-riding, great talks, tasty food and inspiration.  I will miss the sunshine and the playtime, but excited to jump into the all new tech-wonders that I can use for my web and mobile projects back in Seattle.  The Firesky Resort in Scottsdale was a perfect conference location, and I was also very happy with my stay next door at [Chaparral Suites](http://www.chaparralsuites.com/).

**Also a big thank you to my company [Saltbox.com](http://www.saltbox.com)** who have sponsored me to attend JSConf this year!  We're developers of an online communication and learning application that allows Sales organizations to keep a pulse on what happening with their products, their customers and their competitors.
