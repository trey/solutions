---
date: 2010-01-05 03:03:20
title: Getting Django + MySQL running again on Snow Leopard
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/01/django-on-snow-leopard/
---
### [Previously&hellip;](/2008/02/26/installing-django-on-os-x-leopard/)

- Install the latest Xcode Tools from your Snow Leopard installation DVD
- Re symlink things to `/Library/Python/2.6/site-packages` (Leopard used 2.5)
    - Django
    - Any other thing you had symlink'd in 2.5

### MySQL + Python

- [Install MySQL from source like Dan says](http://hivelogic.com/articles/compiling-mysql-on-snow-leopard/) but use the [latest version of MySQL ](http://dev.mysql.com/downloads/mysql/5.1.html#source) (5.1.42 in my case) instead of the version he says to use.
- Install MySQL-Python like [the top answer on this Stack Overflow question](http://stackoverflow.com/questions/1299013/problem-using-mysqldb-symbol-not-found-mysqlaffectedrows/1303895#1303895).

After all that [Sequel Pro](http://www.sequelpro.com/) is still showing the version of MySQL as 5.1.33, but it seems to be working&hellip;

### PIL

This was by far the biggest headache. I finally found [a solution](http://ronny.haryan.to/archives/2008/09/12/psycopg2-and-64-bit-apache-on-leopard/):

Install [like this](/2008/02/26/things-you-probably-want-to-install-to-get-the-most-out-of-django/), but before running `sudo python setup.py install`, do this:

    LDFLAGS="-arch ppc -arch i386 -arch x86_64" CFLAGS="-arch ppc -arch i386 -arch x86_64" python setup.py build

If you already had PIL installed and had the source files you compiled from before, be sure to delete them and start fresh from a new [Imaging-1.1.6.tar.gz](http://effbot.org/downloads/Imaging-1.1.6.tar.gz).