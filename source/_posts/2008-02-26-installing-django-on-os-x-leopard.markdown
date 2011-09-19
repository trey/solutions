---
date: 2008-02-26 06:34:43
title: Installing Django on OS X Leopard
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/02/installing-django-on-os-x-leopard/
---
If you haven't already, stick your Leopard disk in and install Xcode 3.0.

Make a home for Django:

	mkdir -p ~/src/django/core
	cd !$

Get the Django trunk from Subversion:

	svn co http://code.djangoproject.com/svn/django/trunk/

The Django trunk should now be in `~/src/django/core/trunk/`, and if you ever want to check out another branch, you have a nice spot to put it next to the trunk.

---

### If you've previously install Python yourself, pay attention here

Find out if you're using the right version of Python:

	which python

If you don't see:

	/usr/bin/python

then delete whatever version you have sitting in your path, such as one in /usr/local/:

	sudo rm /usr/local/bin/python

Once `which python` gives you `/usr/bin/python`, make sure your Python `site-packages` is in the right place.  Running this command:

    python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"

should give you:

    /Library/Python/2.5/site-packages

### End of previous Python caveat

---

Now make sure Python knows where to find Django:

    ln -s ~/src/django/core/trunk/django /Library/Python/2.5/site-packages/django

Put the `django-admin.py` script on your system path:

    sudo ln -s ~/src/django/core/trunk/django/bin/django-admin.py /usr/local/bin/

Now you should have Django installed and ready to go.  Run:

    django-admin.py startproject project_name

and see.

If it works, `cd` into the folder it creates and try:

    python manage.py runserver

Then go to `localhost:8000` in your browser.

### Django + MySQL:

If you want to use MySQL with Django, there's a bit more to do.  If you have MySQL ready to go, continue.  Otherwise, go [talk with Dan](http://hivelogic.com/articles/installing-mysql-on-mac-os-x/ "Hivelogic:   Installing MySQL on Mac OS X") for a bit and come back here when you're done.

Download the [MySQLdb package](http://www.djangoproject.com/r/python-mysql/).  Stick in in `/usr/local/src` if you're cool.  Open it and edit `site.cfg`.

Change line ~ 13 from:

    #mysql_config = /usr/local/bin/mysql_config

To:

    mysql_config = /usr/local/mysql/bin/mysql_config

In `_mysql.c`:

Remove these lines (~ 37-39):

    #ifndef uint 
    #define uint unsigned int 
    #endif

Go to the folder on the command line, then:

    sudo python setup.py build
    sudo python setup.py install

You might have to run the build command more than once.  Don't ask me why--I'm a copy and paster just like you. 

That should do it.  Try editing your `settings.py` file in your Django project and entering information for a MySQL database and see if it works.

If you experience something different than this or have any problems, please [let me know directly](http://trey.wufoo.com/forms/contact/) or leave a comment.

### Sources

- [Django documentation](http://www.djangoproject.com/documentation/install/)
- [The Django Book](http://www.djangobook.com/en/1.0/chapter02/)
- [Installing Django for Leopard with MySQL Support](http://projectmouse.org/2013/InstallingDjangoforLeopardwithMySQLSupport)
- [#django IRC group](irc://irc.freenode.net/django)

