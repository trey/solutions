---
date: 2006-12-27 05:48:35
title: Pluralization of Database Models in Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/12/pluralization-of-database-models-in-django/
---
Part of the "magic-removal" was apparently [removing automatic pluralization](http://code.djangoproject.com/wiki/RemovingTheMagic#Overview).  That's a shame.  That's one thing I really dig about Rails.

In your `models.py` file:

    class Meta:
        verbose_name_plural = 'something'

So for a 'Person' model, you could put 'people'.  Now it will look right in the admin interface.