---
date: '2007-09-03 12:20:40'
layout: post
slug: removing-existing-users-after-migrating-a-plone-site-to-remember
status: publish
title: Removing existing users after migrating a Plone site to 'remember'
wordpress_id: '11'
categories:
- Plone
---

Existing users on a Plone 2.5 site (before migration to _remember 1.0_) can't be deleted via the User and Group Administrator form.  You'll see _'Runtime Error: No adapter found for user_' when you try to delete one.

You can delete manually though via 'zopectl' or Clouseau.

    
    
    $ ./bin/zopectl debug
    >>> source_users = app.YOURPLONESITE_ID_HERE.acl_users.source_users
    >>> # view all users:
    >>> source_users.getUsers()
    >>> [source_users.doDeleteUser(m.getName()) for m in source_users.getUsers()]
    >>> import transaction; transaction.get().commit()


Note: the getUsers() function doesn't return new _remember_ users so conveniently you don't kill those new users during this process (but you'll want to double-check first!)
