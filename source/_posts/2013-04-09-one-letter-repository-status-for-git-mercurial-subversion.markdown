---
layout: post
title: "One Letter Repository Status for Git, Mercurial and Subversion"
date: 2013-04-09 08:53
comments: true
categories: ["git", "mercurial", "subversion"]
---

These days we're using a variety of version control systems and switching between them regularly.

My most used command is checking my working directory status, so I've distilled it down to a one-letter shortcut that determines which type of repository I'm in, then does an appropriate status for that system.

I just setup an alias like this:

    s='~/s/s.sh'

So just type `s` and don't worry about which version control you're in.

{% gist 5118028 %}

[Here's the code on gist.github.com](https://gist.github.com/briangershon/5118028/)
