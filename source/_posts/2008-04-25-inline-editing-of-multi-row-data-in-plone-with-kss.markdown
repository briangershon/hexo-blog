---
date: '2008-04-25 14:53:52'
layout: post
slug: inline-editing-of-multi-row-data-in-plone-with-kss
status: publish
title: Inline Editing of Multi-row Data in Plone with KSS
wordpress_id: '34'
categories:
- GTD
- KSS
- Plone
---

Here is how I added inline editing for multiple rows of data to my CollectiveGTD Plone 3.0 product using KSS.

This was challenging in that it was my first KSS project, plus most of the KSS editing examples I've found deal with editing just one piece of content (instead of multiple rows).

**Here is a screencast to whet your appetite for inline editing.**  Basically, CollectiveGTD has many rows of Action Items (each with Name, Start Date, Due Date, etc) that needed to be edited.



[![collectivegtd_screencast_thumbnail.png](/images/post/2008/04/collectivegtd_screencast_thumbnail.png)
Screencast: Example of Inline Editing in CollectiveGTD](/images/post/2008/04/collectivegtd_inline.mov)

Here were the issues that needed to be solved:



	
  * How do we capture KSS events for a specific field in a specific row?

	
  * How do we display inline editing forms?

	
  * How do we handle the same row of content if it shows up in multiple places? e.g. CollectiveGTD also has a portlet which might display the same content in both the multi-row form


**Here are highlights, issues and lesson's learned:**

Note: If you generally want to see all of the new KSS code in one place:
_svn diff -r59525:60742 https://svn.plone.org/svn/collective/CollectiveGTD/trunk_

**1. Converting from a plain old HTML form to a nice KSS template**

Prior to adding KSS, I started with a single HTML form that allowed users to check "Done" or "Starred" fields and click "Submit" to update all the pieces of content.  The goal was to replace that with KSS, plus add inline editing. To do this, I had to remove the one HTML form since you can't have mini-inline forms inside of a big form.

![warning.jpg](/images/post/2008/04/warning.jpg) Issue: Not sure how to degrade this functionality nicely if someone doesn't have JavaScript enabled.

I recommend creating macros for each field you're editing, and a unique naming scheme for your inline fields.

I created 4 TAL macros (in collectivegtd_kss.pt) - one for each field to be edited with KSS.  There is a lot of HTML to put in, so doing this simplifies the main page template which then just generates the page and repeats through multiple rows of data (actions_view.pt).

The first goal was to uniquely id each editable field, even if the same piece of content shows up in more than one place on the page.

To do this, each field's CSS ID was based on the content's short-name (to represent the specific piece of content, aka "row") with a 'prefix' string (to represent the specific fieldname in case it appears in many places).  For CollectiveGTD there are 4 prefixes for the main page (main_startdate, main_duedate, main_complete, main_flag) and 4 prefixes for the portlet (portlet_startdate, portlet_duedate, portlet_complete, portlet_flag).

![warning.jpg](/images/post/2008/04/warning.jpg) Issue: A period in the field's CSS ID breaks KSS.  A period can appear because the short-name for a Plone piece of content can contain periods, and I'm using the short-name as the unique identifier.  I haven't fixed this one yet.

The macros require two pieces of information: 'actionItem' and 'prefix'.  ActionItem is a single piece of content that has all the fields a row needs.    These prefix also allowed the KSS code to be able to update multiple fields if the same piece of content appears more than once.  e.g. Changing Start date on the form, should also update the Start date for that items if it also appears in the portlet.

**2. Inline Editing Issues**

The initial tricky part of multi-row data (specifically with inline-editing) is that you can't dynamically create KSS events for every row (nor would you want to!), so you need to structure your HTML and CSS a specific way so that when you trigger a KSS event it is smart enough to know which fields are connected with that row. My first version ended up showing and hiding all the rows forms instead of just the one I wanted.

How to hide and show the inline form:

Since inline text editing requires grouping several elements together, it's important to group everything in one tag (e.g. <div>) and make sure all the KSS selectors for that inline form starts with that tag.  The reason is that you want the parent of all the forms to be the same, so that when your KSS action fires, you can capture it within that form -- and not all forms.  You do all this magic via the "parentnode" function in your KSS selector.

I also set each form to have these two classes to start with (editform hiddenform) so that all the form default to being hidden.

Here's the example of the "Due Date" field:

![collectivegtd_kss.png](/images/post/2008/04/collectivegtd_kss.png)

![collectivegtd_pt.png](/images/post/2008/04/collectivegtd_pt.png)

**3. What happens after submitting an inline-edit form?**

New ActionItemListKSS view for handling the server-side content updates

I created a new ActionItemListKSS (which subclasses PloneKSSView) to provide the server-side code to update content, and also reflect the changes back to the webpage (via those unique IDs we generated in the templates).

The unique IDs are used by our ActionItemListKSS.

The methods of my view are connected to the form via KSS (in collectivegtd.kss).  The major methods include: update_dueDate(), update_startDate(), update_complete(), update_flag().  This is where a lot of code duplication happens (similar code in all 4 methods), but easy to understand.

They all basically are passed a ActionItem ID (content short-name) and the new value (via KSS magic).  The method then updates the piece of content, reindexes the content to make sure the catalog is updated, then updates the webpage by doing an HTML replace for both prefixes ("main" and "portlet").  It the content only exists in one place, the other replace is ignored.  Finally, a Portal Message is sent to the user to let them know what was changed.  The two "inline edited" fields are naturally more complex.

![warning.jpg](/images/post/2008/04/warning.jpg) Issue: This still seems like too much duplicate code is needed in ActionItemListKSS. Once I had one field working, I found myself refactoring common code as I learned KSS and discovered which code to reuse across fields.  The refactoring is leading toward a view class useful for inline editing though!

Lesson Learned: I ended up adding helper functions in ActionItemListKSS to handle the individual field-level updates of content, because updating fields like Start Date and Due Date were complex because of the complex date conversion code -- converting strings to dates, then converting dates back to strings. This was largely because I didn't build individual field update code in CollectiveGTD.  I started with formlib code which created new ActionItems all at once.  In hindsight, it would be good to have a view that allows updating of each individual field -- then it could be reused in both formlib and KSS without having to duplicate code.  I still may do this refactoring at some point.

4. CSS file (collectivegtd.css)

The CSS was straight-forward.  Minor note: The only reason some of the selectors have a lot of options is that I was playing with CSS rollovers (where one image has both rollover states) and found some boilerplate code that looks like it works for all browsers imaginable.  I'm sure some of those could be removed.

5. Tests

I added tests for the ActionItemListKSS methods, but haven't tried UI testing yet.

**Conclusion**

Therefore, thus...

* It's worth learning KSS because of the power it brings you without having to write JavaScript code directly.

* The tricky piece was learning how the various pieces work together (KSS, PloneKSSView, and figuring out best-practices for structuring HTML and CSS), though once that is understood, it was easy to maintain the pieces separately by breaking the templates up into macros (to keep things simple and reusable), put all the server-side code in one Python class, with one KSS file that connects the two.

I hope this example provides you with what you need to avoid some of that initial learning curve.

I'm also interested in learning from KSS gurus if there is a way to simplify any of these pieces.
