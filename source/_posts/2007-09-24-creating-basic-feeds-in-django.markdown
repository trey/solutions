---
date: 2007-09-24 01:05:10
title: Creating Basic Feeds in Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/09/creating-basic-feeds-in-django/
---
This is actually pretty straight-forward if you've got things set up properly.  I had a [hard time](http://groups.google.com/group/django-users/browse_thread/thread/1f90e00045e9fb3f "Simple Feeds Not Working - Django users | Google Groups") at first, because I had the ["sites" framework](http://www.djangoproject.com/documentation/sites/ "Django | The &#8220;sites&#8221; framework | Django Documentation") enabled but I wasn't using it the right way.  Basically, if you've got anything but the default `example.com` in the `django_sites` table, the [syndication feed framework](http://www.djangoproject.com/documentation/syndication_feeds/ "Django | The syndication feed framework | Django Documentation") will be unhappy with you (presumably, unless you're using the framework the right way).

Here's what to do:

Put this in the urlpatterns in your base `urls.py`:

	(r'^feeds/(?P<url>.*)/$', 'django.contrib.syndication.views.feed', {'feed_dict': feeds}),

Put this in the top of your base `urls.py` (replace `your_project_name` and `FeedName` with your stuff):

	from your_project_name.feeds import FeedName

	feeds = {
	    'feedurl': FeedName,
	}
	
Create a file called `feeds.py` and put it in the root of your project folder.  This is what goes in it (`your_project_name` and `FeedName` are the same as the example above, replace `ModelName` and `date_field` with your stuff as well):

	from django.contrib.syndication.feeds import Feed
	from your_project_name.models import ModelName

	class FeedName(Feed):
	    title = "Title of the website"
	    link = "/whatever/"
	    description = "What's the feed about, anyway?"

	    def items(self):
	        return ModelName.objects.order_by('-date_field')[:5]

You can change the `[:5]` to whatever number of items you want to show up in the feed, in case that wasn't apparent.

The last step is to create templates for the feed just like you create for normal page views.  Create a folder in your templates folder called `feeds`.  The naming convention goes like this (`feedurl` is the same as you put in `urls.py`--like 'blog' or 'latest', etc.).

	templates/feeds/feedurl_title.html
	templates/feeds/feedurl_description.html

What goes in feedurl_title.html (at a minimum):

	{{ obj.name }}
	
And `feedurl_description.html`:

	{{ obj.description }}

Replace `.title` and `.description` with whatever the fields are called in your model.  I usually use 'name' instead of 'title', for example.

I think it will work without having those templates, but you can customize what shows up in your feed pretty easily using that format.  You can even rename what template files to use by putting this in your Feeds class (right below `class FeedName(Feed):`)

	title_template = 'feeds/whatever.html'
	description_template = 'feeds/whatever_else.html'

When you're all done, you'll be able to view your feeds at:

	yoursite.tld/feeds/feedurl/

On a side note--the feed won't show up in Safari while you're viewing the feed on localhost for some reason.  I've heard it works OK when it's on a live server.  Check it out in Firefox or something.

### Sources:

- [Official documentation](http://www.djangoproject.com/documentation/syndication_feeds/ "Django | The syndication feed framework | Django Documentation")
- [Fun With Django Feeds](http://www.andrlik.org/blog/2007/aug/03/fun-with-django-feeds/ "Ministry of Intrigue")
- [Digging Into Django's Syndication Framework](http://blog.michaeltrier.com/2007/8/5/digging-into-django-syndication-framework "Empty Thoughts")