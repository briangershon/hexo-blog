---
date: '2010-09-14 15:33:03'
layout: post
slug: djangocon-2010-highlights-videos
status: publish
title: Highlights from DjangoCon 2010 (and videos to watch)
wordpress_id: '202'
categories:
- Django
---

Here were some DjangoCon 2010 highlights for me, along with talk titles so you can find the full presentations online at http://djangocon.blip.tv/posts?view=archive




"Creating better apps"




Both Eric Florenzano ("Why Django Sucks, and How We Can Fix It") and Alex Gaynor ("Rethinking the Reusable Application Paradigm") had many useful things to say about creating better and more reusable apps.  The videos are worth watching, here are some highlights:




* Narrower abstractions would make apps suck less -- such as not directly exposing models (create an API) so you can swap out model or implementation.  This was also a big part of Alex's talk.




* Class-based views are a nice way of creating an API and allow implementations to change over time.  There are various ways of doing class-based views and there isn't an official blessed way, but class-based views would be an improvement (and offer more flexibility) than current function-based views in Django.




"Databases other than SQL"




With the growth in non-relational databases out there, I enjoyed starting to play with MongoDB (pyMongo and django-nonrel).  After hearing experiences from the "NoSQL and Django Panel" it's obvious that these are new technologies (relative to SQL) and that they are quite varied in what they support and the problems they solve.  There are also pros and cons with schemaless databases.




Andrew Godwin ("Step Away From That Database") also presented a nice range of databases -- Document databases (MongoDB, CouchDB), Key-value stores (Cassandra, Redis), Message Queues (AMQP, Celery), Graph databases -- and reminds us that filesystems are also key-value stores, and that version-control systems can provide a versioned storage.




"Data Migration"




Brian Luft's talk ("Data Herding: How to Shepherd Your Flock Through Valleys of Darkness") will resonate with anyone looking for better methods of moving from a legacy system to Django. He also highlights the opportunity and flexibility that Django framework provides for clients in moving them off of their desktop and legacy systems.




"Website Security"




Adam Baldwin ("Pony Pwning") gave a great talk on website security and things to be thinking about while building Django sites.




Cross-Site Scripting ("xss") vulnerability are alive and well. Though Django offers protections, these can be turned off or it's easy to make a mistake in the template layer and open yourself up. You can learn more and play with xss vulnerabilities: http://owasp-esapi-python-swingset.appspot.com/xss/django




Adam suggests considering OWASP ESAPI, auditing templates, auditing reusable snippets, and educating designers.




For REST services, good to consider django-piston rather than writing your own.




Other things include checking upload extensions to avoid running arbitrary code, e.g. Django ImageField doesn't check extensions and could possibly run embedded code.  Apache "mod_security" as a nice monitoring tool that can let you know what's happening, as well as prevent some issues.




"Exclusionary Establishment"




Eric Florenzano hit on some issues on the social engineering side of Django.  Examples were presented that send messages of "your contributions aren't important" out to the larger Django community -- enhancements that went through all the steps but didn't make it into core (eg truncatechars), key contributors not given committer rights (eg Alex Gaynor), no non-core developer code accepted into django.contrib.




James Bennett's ("Topics of Interest") reflected some of this too in the fact that there are very few core committers (14) and even fewer than understand the ORM and that they're having a hard time growing core-committers.  Eric's mention of Guido van Rossum's quote (creator of Python) "give out more commit privileges sooner".




Participation could be easier and more inviting if more core devs are added and there is also less concern about breaking trunk.




Something I'll add to this is that there were many talks submitted for DjangoCon so some were turned away, yet some presenters had 3 slots.  Many of the talks were very good, but I think it would be healthy to have some opportunities for new faces to present, and not the same ones each year. (transparency note: our talk was one that wasn't accepted)




"Become a Django Core Developer"




Given the concern about lack of core committers, Russell Keith-Magee ("So you want to be a core developer?") was timely. In addition to going through the process of contributing code, he also mentioned that contributing to the Django community in the form of help (django-user list, stack overflow, etc) and writing new docs (tutorials, howtos, elaborating on existing docs) is key.




"Interesting Apps and Projects"




The lightning talks and Eric Holscher's talk ("Large Problems in Django, Mostly Solved") were a good source of Django apps to try if you're not already using them.




Eric also shares his measure of what makes a solid reusable app -- needs to have an easy setup, a good upgrade path, good documentation and well-tested.




Apps he mentioned were Haystack (search), Sphinx (documentation), South (db migration), Celery (delayed execution), Fabric (deployment), gunicorn.org (async server), pip and virtualenv (packaging), TastyPie and Piston (RESTful), Taggit (tagging), Hudson (continuous integration tool), django-filter (django admin filtering), djangopackages.com (for finding new apps).




Some interesting things from the lightning talks:




* http://djangopackages.com (a Django Dash project)




* http://readthedocs.org  (a Django Dash project)




* logbook - http://github.com/mitsuhiko/logbook




"Performance"




Frank Wiles' talk ("Alice in Performanceland -- Down the Rabbit Hole") was full of a lot of tasty morsels to help you "do less" and "remove pressure on your server" that ultimately increases the performance and responsiveness of your site.




"Code Quality"




Human code review is best says Peter Baumgartner in his talk ("Monitoring Code Quality in Your Django Project"). There are also many great code quality tools out there that many of us use: test suites, code coverage, link/pep8, profiling, code complexity metrics, value -- and pulling this together via Hudson.  Also, creating a build in one step is offers new developers a fast way to get started on a project.




"Managed Django Hosting"




I missed Nate Aune's lightning talk on his DjangoZoom.com cloud deployment solution, but looks interesting. http://djangozoom.com/ponyexpress/




One of the lightning talks discussed the django-servee project: http://www.servee.com/features/ http://github.com/servee/servee




"Seeing some New Faces"




It was nice meeting new people who are using Django in Washington State outside of Seattle, such as in Richland and Spokane, and reconnecting with friends from the Plone and greater Python communities.


Here were some DjangoCon 2010 highlights for me, along with talk titles so you can find the full [presentation videos online](http://djangocon.blip.tv/posts?view=archive).


## Creating better apps


Both Eric Florenzano ("Why Django Sucks, and How We Can Fix It") and Alex Gaynor ("Rethinking the Reusable Application Paradigm") had many useful things to say about creating better and more reusable apps.  The videos are worth watching, here are some highlights:



	
  * Narrower abstractions would make apps suck less -- such as not directly exposing models (create an API) so you can swap out model or implementation.  This was also a big part of Alex's talk.

	
  * Class-based views are a nice way of creating an API and allow implementations to change over time.  There are various ways of doing class-based views and there isn't an official blessed way, but class-based views would be an improvement (and offer more flexibility) than current function-based views in Django.




## Databases other than SQL


With the growth in non-relational databases out there, I enjoyed starting to play with djangon-nonrel with MongoDB.  This project also supports Google App Engine.

After hearing experiences from the "NoSQL and Django Panel" it's obvious that these are new technologies (relative to SQL) and that they are quite varied in what they support and the problems they solve.  There are also pros and cons with schemaless databases that you should be aware of when picking your solution.

Andrew Godwin ("Step Away From That Database") also presented a nice range of databases -- Document databases (MongoDB, CouchDB), Key-value stores (Cassandra, Redis), Message Queues (AMQP, Celery), Graph databases -- and reminds us that filesystems are also key-value stores, and that version-control systems can provide a versioned storage.


## Data Migration to Django


Brian Luft's talk ("Data Herding: How to Shepherd Your Flock Through Valleys of Darkness") will resonate with anyone looking for better methods of moving from a legacy system to Django. He also highlights the opportunity and flexibility that Django framework provides for clients in moving them off of their desktop and legacy systems.


## Website Security


Adam Baldwin ("Pony Pwning") gave a great talk on website security and things to be thinking about while building Django sites.

Cross-Site Scripting ("xss") vulnerability are alive and well. Though Django offers protections, these can be turned off or it's easy to make a mistake in the template layer and open yourself up. You can learn more and play with xss vulnerabilities: [http://owasp-esapi-python-swingset.appspot.com/xss/django](http://owasp-esapi-python-swingset.appspot.com/xss/django)

Adam suggests considering OWASP ESAPI, auditing templates, auditing reusable snippets, and educating designers.

For REST services, good to consider django-piston rather than writing your own.

Other things include checking upload extensions to avoid running arbitrary code, e.g. Django ImageField doesn't check extensions and could possibly run embedded code.  Apache "mod_security" as a nice monitoring tool that can let you know what's happening, as well as prevent some issues.


## An Exclusionary Establishment?


Eric Florenzano hit on some issues on the social engineering side of Django.  He provided examples of situations that can send the messages of "your contributions aren't important" out to the larger Django community -- enhancements that went through all the steps but didn't make it into core (eg truncatechars), key contributors not given committer rights (eg Alex Gaynor), no non-core developer code accepted into django.contrib.

James Bennett's ("Topics of Interest") reflected some of this too in the fact that there are very few core committers (14) and even fewer than understand the ORM and that they're having a hard time growing core-committers.  Eric's mention of Guido van Rossum's quote (creator of Python) "give out more commit privileges sooner".

Participation could be easier and more inviting if more core devs are added and there is also less concern about breaking trunk.

Something I'll add: My understanding is that too many talks were submitted for DjangoCon so of course some were turned away, yet some presenters had more than 1 slot.  Many of the talks were very good, but I think it would be healthy to open up more opportunities for community members to present.


## Improving Django and Becoming Core Developer


Given the concern about lack of core committers, Russell Keith-Magee ("So you want to be a core developer?") was timely. In addition to going through the process of contributing code, he also mentioned that contributing to the Django community in the form of help (django-user list, stack overflow, etc) and writing new docs (tutorials, howtos, elaborating on existing docs) is key.


## Interesting Apps and Projects


The lightning talks and Eric Holscher's talk ("Large Problems in Django, Mostly Solved") were a good source of Django apps to try if you're not already using them.

Eric also shares his measure of what makes a solid reusable app -- needs to have an easy setup, a good upgrade path, good documentation and well-tested.

Apps he mentioned were Haystack (search), Sphinx (documentation), South (db migration), Celery (delayed execution), Fabric (deployment), gunicorn.org (async server), pip and virtualenv (packaging), TastyPie and Piston (RESTful), Taggit (tagging), Hudson (continuous integration tool), django-filter (django admin filtering), djangopackages.com (for finding new apps).

Some interesting things from the lightning talks:



	
  * [http://djangopackages.com](http://djangopackages.com) (reusable apps, sites, tools -- a Django Dash project. Nice work [Daniel Greenfeld](http://pydanny.com/)!)

	
  * [http://readthedocs.or](http://readthedocs.org)g  (hosted help documents -- a Django Dash project)

	
  * [logbook](http://github.com/mitsuhiko/logbook) - an easier way to add logging to Django




## Performance


Frank Wiles' talk ("Alice in Performanceland -- Down the Rabbit Hole") was full of a lot of tasty morsels to help you "do less" and "remove pressure on your server" that ultimately increases the performance and responsiveness of your site.


## Improving your Code Quality


Human code review is best says Peter Baumgartner in his talk ("Monitoring Code Quality in Your Django Project"). There are also many great code quality tools out there that many of us use: test suites, code coverage, link/pep8, profiling, code complexity metrics, value -- and pulling this together via Hudson.  Also, creating a build in one step is offers new developers a fast way to get started on a project.


## Managed Django Hosting


I missed Nate Aune's lightning talk on his DjangoZoom.com cloud deployment solution, but looks interesting. [http://djangozoom.com/ponyexpress/](http://djangozoom.com/ponyexpress/)

One of the lightning talks discussed the django-servee project: [http://www.servee.com/](http://www.servee.com/)


## Thanks DjangoCon!


It was nice meeting new people using Django in Seattle and in other areas of Washington State, such as in Richland, Wenatchee and Spokane -- and reconnecting with friends from the Plone and greater Python communities.

Thank you to the organizers, presenters and supporters for another great DjangoCon!
