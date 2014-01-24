---
date: '2009-09-25 22:23:52'
layout: post
slug: open-tagging-on-osx-a-powerful-way-to-organize
status: publish
title: 'Open Tagging on OSX: A Powerful Way to Organize'
categories:
- Apple
tags:
- GTD
- OSX
- Snow Leopard
---

For each project I work on, I have a multitude of files, folders, applications, and web pages.

My goal is to have shortcuts in one place, organized by project, as the ultimate launcher.

Here were some good initial attempts:



	
  * Firefox bookmarks might be a nice way to go, but doesn't make it easy to link to local files, so that solution was quickly dismissed.

	
  * [Butler](http://www.manytricks.com/butler/) did this well -- a quick click in the menu bar pulls up a hierarchical list of projects and shortcuts to resources for each project.  You could easily drag and drop URLs as well as local file shortcuts to Butler as well.  This approach basically created a nice external bookmark manager not tied to any one browser and able to link to files of all types.

	
  * Recently I noticed that Snow Leopard's improved Grid (in the Dock) now allows for navigating down a hierarchy of folders quickly, so though about putting my shortcuts there.  The only problem is that the dock is "way down there" (irregardless of where you put the dock) and takes time to mouse around.


Each tool took their own approach, and I had to pick one since I couldn't easily use multiple ones. Also, graphical solutions still take precious time to drag your mouse and navigate through the hierarchy.

Then a better idea.

Spotlight is quick and fast for searching so is ideal (just press apple-spacebar) though typing in search phrases still brings up lots of extra information I don't want.

So how do I universally "tag" resources and bring them up quickly?

First, the cool 2006 (and still usable) [metadata solution mentioned on LifeHacker](http://lifehacker.com/169971/metadata-as-a-filing-system): Apple-I on files you want to tag, then add a custom tag into the comment box. Prefix with & so it's quick to find without bringing up a lot of other crap.  For my common Web Collective company shortcuts, I used &wc.  Now, when I jump to Spotlight and type &wc, I instantly see all my shortcuts.

This was great, but then I found tagging nirvana on OSX.

**An ecosystem of tagging tools has popped up around a free and open source [OpenMeta Tag](http://code.google.com/p/openmeta/) standard.**

**OpenMeta means that you can now tag files, folders, emails, web pages, etc, with an assortment of tools, and then search for them with an assortment of tools.** No need for custom tagging in the file "comment" field, and no need to use a proprietary tagging system that locks you into one tool. (Btw, for web pages, I drag a shortcut from the browser to my file system, then tag the resulting .webloc file)

The simplest workflow consists of tagging files by dragging/dropping them onto [Tagger](http://hasseg.org/tagger/), then pulling them up quickly in Spotlight.  To pull up all my shortcuts tagged with "wc" you just type "tag:wc".  This is a free solution and works well.

![Tagger window](/images/post/2009/09/tagger_window.png)

![Spotlight Search using tags](/images/post/2009/09/Screen-shot-2009-09-25-at-10.31.39-PM.png)

**Next in the evolution are tools such as [Tags](http://gravityapps.com/tags/overview/) or [Punakea](http://www.nudgenudge.eu/punakea) or [Leap](http://www.ironicsoftware.com/leap/index.html) -- which make it easy to tag, while also having nice integrated search features.** Tags makes it easy to tag email (in addition to files and folders), Leap (the creator of OpenMeta) is interesting because it has a very fast and flexible searching mechanism and basically does all the work of the Finder with the powerful addition of tagging and rating.  These are all paid applications -- well worth it if they help you to better organize.

I'm still playing around to find the right combination of tools for my own workflow.  See [http://code.google.com/p/openmeta/wiki/OpenMetaApplications](http://code.google.com/p/openmeta/wiki/OpenMetaApplications) for a nice list.

Tagger and Spotlight are working well for quick shortcuts -- Tags, Punakea and Leap start to show what a world would be like when relying less on hierarchy and more on tags.

Hmmm, [TagFolders](http://web.me.com/jonstovell/Tag_Folders/Tag_Folders_Home.html) looks pretty interesting too...
