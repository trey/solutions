---
date: 2006-10-11 19:11:56
title: Basic CRUD using REST in Rails
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/basic-crud-using-rest-in-rails-incomplete/
---
First, get on Edge Rails.  Easiest way:

    rake rails:freeze:edge
    rake rails:update

Then generate some new-school scaffolding:

    script/generate scaffold_resource ModelName

This generates a migration template for you.  Use that to fill in the details then run `rake db:migrate`.

In `app/views/ModelName`, you'll have to add the details of your model to the different forms.  Something like this:

    <div><label>Name: <%= f.text_field :name %></label></div>
    <div><label>Description: <%= f.text_area :description %></label></div>

<del datetime="2006-10-21T19:20:53+00:00">I still haven't figured out how to get things to actually work.</del>

<ins datetime="2006-10-21T19:20:53+00:00">**Update 21.10.2006:** My problem in getting things to work was a matter of putting my RESTful routes information at the top of the `config/routes.db` file.  Top == higher priority.</ins>

## Sources

* [PeepCode tutorial](http://www.peepcode.com/articles/2006/10/08/restful-rails).  It is *so* nice to be able to watch someone go through all this from start to finish.
* I got most of this information [here](http://www.softiesonrails.com/2006/09/25/quick-guide-to-the-new-scaffold_resource-generator)
* [DHH Keynote (slides)](http://www.loudthinking.com/arc/000593.html)
* [DHH Keynote (video)](http://blog.scribestudio.com/articles/2006/07/09/david-heinemeier-hansson-railsconf-2006-keynote-address)
* [Details about `form_for`](http://api.rubyonrails.org/classes/ActionView/Helpers/FormHelper.html#M000387) (this took me forever to figure out)

[Continued here](http://solutions.treypiepmeier.com/2006/11/05/basic-crud-for-nested-elements-using-restful-rails/)...