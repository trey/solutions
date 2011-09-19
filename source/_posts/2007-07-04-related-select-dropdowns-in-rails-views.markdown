---
date: 2007-07-04 20:05:08
title: Related `select` Dropdowns in Rails Views
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/07/related-select-dropdowns-in-rails-views/
---
This is a pretty common scenario (I would think).  You have a nested model that you want to be able to select the item that the current item depends on (the client for a project, the manufacturer for an appliance).  Using `form_for`, you can do something like this.

### Chat with [JTJ](http://blog.postpostmodern.com):

> What you do is create a select tag with the "`select`" method like so: (using the client/project scenario)

> `f.select(:client_id,`

> The next value you pass to the select method has to be an array of text/value pairs

> like this: `[ [ "Jason Johnson", 1], ["Trey Piepmeier", 2], ["Royall", 3] ]`

> In order to create this array, you do a find on your clients table and use Ruby's "`collect`" method.

> like so:

> `Client.find(:all).collect {|c| [ c.name, c.id ]}`

> So, altogether now:

    f.select(:client_id, Client.find(:all).collect {|c| [ c.name, c.id ] })

### Other sources:

- [Rails API](http://api.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html#M000506)
- [Ruby's `.collect` method](http://www.rubycentral.com/book/ref_c_array.html#Array.collect)
- [Ruby 101 for .NET Developers: .map and .collect](http://softiesonrails.com/2007/3/2/ruby-101-for-net-developers-map-and-collect)