---
date: '2008-08-19 02:01:49'
layout: post
slug: collectivegtd-for-plone-31-beta-2-released
status: publish
title: CollectiveGTD for Plone 3.1 (Beta 2 Released)
categories:
- Programming
tags:
- GTD
- Plone
---



This is a Plone product that implements an Open Source version of the Getting Things Done (GTD) methodology.

**New in this release:**
This version fixes all known unicode issues, so that non-ascii characters can now be used throughout interface for editing, viewing, and KSS inline editing.

For download, please visit [http://plone.org/products/collectivegtd-thoughts/releases/1.0b2](http://plone.org/products/collectivegtd-thoughts/releases/1.0b2)

**Change log:**



	
  * NEW: Fixed all known unicode issues which were causing context/project tagging to break when editing and when viewing, and were preventing KSS from updating the UI. Language-to-date features are still only supported in English.  Templates have not been internationalized.

	
    * Future Plan is to replace home-grown language-to-date functionality with the parsedate python module, which also supports multiple languages.




	
  * NEW: Added new getAllActiveActions(outputFormat="xml) method to spit out all ActionItems, Context tags and Project tags for use by a desktop application.

	
  * INCOMPLETE: Started to build an iPhone interface. Partially complete. Further work on this postponed.



