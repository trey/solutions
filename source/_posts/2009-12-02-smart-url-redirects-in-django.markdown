---
date: 2009-12-02 23:50:07
title: Smart URL Redirects in Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/12/smart-url-redirects-in-django/
---
While building [ComicBinder][cb]'s URLs, I wanted a way to differentiate a volume of a title other than one, and a printing of an issue other than one. So, for example, a URL to the second printing of the second volume of Amazing Spider-Man #1 would look like:

    /marvel/amazing-spider-man_2/1_2/

That's easy enough with some `URLconf` wrangling. What I'm talking about today is automatically redirecting a request for `_1` in any of those places to the same URL without the `_1`. While technically correct, I want the lack of underscore + number to mean one, and for there to be only one URL for a resource (someone send me a link to a clever article that talks about this). 

`django.views.generic.simple.redirect_to` to the rescue. Try something like this:

    (r'^(?P<publisher>[-\w]+)/(?P<title>[-\w]+)_1/(?P<number>\d+)_1/$', 'django.views.generic.simple.redirect_to', {'url': '/%(publisher)s/%(title)s/%(number)s/'}),

I made a few of these to account for situations where it was the first volume, but nothing specified for printing, and vise versa.

Not too bulky, and since I have that sitting near the normal rule, it shouldn't put me out too much to update it if I make any changes.

### Source

- [Django Documentation](http://docs.djangoproject.com/en/dev/ref/generic-views/#django-views-generic-simple-redirect-to)

[cb]: http://comicbinder.com