---
date: 2007-02-28 01:40:42
title: Howto Upload Images in Django
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/02/howto-upload-images-in-django/
---
[Previously](http://solutions.treypiepmeier.com/2006/09/30/image-uploads-in-django/)

I've chosen to keep my media in the `/media/` folder of the same site (I know Django-people prefer to keep media on a separate server, but I don't want to do that for a small-ish site, which is why I'd be likely to use Django).

In `settings.py`:

    ADMIN_MEDIA_PREFIX = '/admin_media/'

This defaults to `/media/`, but I want that for my own media.

In `urls.py`:

    (r'^media/(?P<path>.*)$', 'django.views.static.serve', {'document_root': '/Users/username/django/django_projects/project_name/media'}),

This is recommended **against** [here](http://www.djangoproject.com/documentation/static_files/).  But that's because they want you to serve all your static files from a separate server/domain as I mentioned before.

Set the other media configuration things:

    MEDIA_ROOT = '/Users/username/django/django_projects/project_name/media/'
    MEDIA_URL = '/media/'

In `models.py`:

    logo = models.ImageField(upload_to="images/logos/", blank=True, help_text="Should be 50px wide")

[This guy](http://groups.google.com/group/django-users/browse_thread/thread/777395738834d536/b303510899af45c4?lnk=gst&q=media+display&rnum=1#b303510899af45c4) was having the same problem.
