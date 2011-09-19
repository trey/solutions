---
date: 2008-03-11 03:46:34
title: Use Django's Permalink Decorator with Generic Views
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/03/use-djangos-permalink-decorator-with-generic-views/
---
[The permalink decorator](http://djangobook.com/en/1.0/appendixB/#cn280) is the way to keep your URLs DRY.  The only place you need to define where something lives is in your `urls.py`.  In your templates, just point to `{{ object.get_absolute.url }}`.  The problem with how they tell you to do it in [the book](http://djangobook.com/en/1.0/appendixB/#cn280), [the documentation](http://www.djangoproject.com/documentation/model-api/#the-permalink-decorator), and [elsewhere](http://cammacrae.com/blog/2007/08/20/permalink-decorator-pt-2/) is that it doesn't work right if you're using the same view function more than once in all your `urls.py` files (which is bound to happen if you're using a bunch of generic views).  That's because Django has no way of telling which one you mean.

[Named URL patterns](http://www.djangoproject.com/documentation/url_dispatch/#naming-url-patterns) to the rescue.

If you have a URLpattern that looks like this:

    (r'^(?P<slug>[-\w]+)/$', list_detail.object_detail, log_detail),

Change it to this:

    url(r'^(?P<slug>[-\w]+)/$', list_detail.object_detail, log_detail, name='log-detail'),

Note the addition of "`url`" to the start of the line and the "`name=`" bit at the end.

Now, in your model file(s), do the following:

Add this line to the top of the file:

    from django.db.models import permalink

At the bottom of the model class do something similar to this:

    @permalink
    def get_absolute_url(self):
        return ('log-detail', (), { 'slug': self.slug })

Any other question you have about this stuff is probably in the other sources.

### Sources:

- Magus- on the #django IRC channel
- [Django Book](http://djangobook.com/en/1.0/appendixB/#cn280) (print edition pages 324-325)
- [Django documentation (permalink decorator)](http://www.djangoproject.com/documentation/model-api/#the-permalink-decorator)
- [Django documentation (named URL patterns)](http://www.djangoproject.com/documentation/url_dispatch/#naming-url-patterns)
- [cam macrae](http://cammacrae.com/blog/2007/08/20/permalink-decorator-pt-2/)

