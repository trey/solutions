---
date: 2006-10-05 08:41:43
title: Making a POST link in Rails
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/making-a-post-link-in-rails/
---
You know you shouldn't be using GETs (URLs) for deleting things, right?  Here's how you do it in Rails:

`<%=  link_to "Destroy account", { :action => "destroy" }, :confirm => "Are you sure?", :post => true %>`

(example is from [the API docs](http://api.rubyonrails.org/))

`:post => true`!  That's awesome.  Of course, it's not unobtrusive, but maybe [UJS](http://www.ujs4rails.com/) could fix that.