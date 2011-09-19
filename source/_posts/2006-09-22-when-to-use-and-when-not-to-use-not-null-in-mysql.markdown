---
date: 2006-09-22 23:44:26
title: When to use and when not to use NOT NULL in MySQL / Rails Migrations
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/09/when-to-use-and-when-not-to-use-not-null-in-mysql/
---
This is somewhat academic.  Most times, the default (NULL) is just fine.  I've been talking with [JJ](http://blog.postpostmodern.com/), and he has some specific preferences--that's what this is based on.

Usually, having a database attribute default to NULL makes it easy to check to see if a field has information.  If it doesn't, it's just NULL--you don't have to check for an empty string or 0.

The main reason you would want to specifically set an attribute to NOT NULL would be if it's a field that would be used for computation.  Example: you can't multiply by NULL.

Rails makes most NULL/NOT NULL issues easier.

* Rails (Ruby) handles NULL (NIL) strings as empty strings--so it doesn't give you errors if you're outputting results and get a NULL.  It just shows up as blank.
* Rails sets blank form fields as NULL--unlike PHP which sets them as empty.  This makes it easier to check if an item has been set (as mentioned above).

###NULL Database Associations

NULL associations are another matter (and not really related to this issue).  You should have a way to catch Rails exceptions if you have a record with a NULL association.  Example: a car model (Corvette) without a make (Chevrolet) might make your application throw up.  Check for it, and handle it appropriately.

**Update 2007.7.5:** Handle it like this if you want an optional association:

	<%=h @project.client.name rescue nil %>

Or you could just check for it with an `if` or `unless` statement:

	<% unless @project.client.nil? %>

###Better way?

If you have a differing opinion / think this is full of crap, please leave a comment.  I'm open to suggestions on this.