---
date: 2008-01-17 03:11:49
title: MySQL Commands You Should Have Committed to Memory Already
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/01/mysql-commands-you-should-have-committed-to-memory-already/
---
### Dump the database

	mysqldump -h database_host -uUsername -p database_name > dump.sql 

### Restore from the dump

If you need to create the database first:

    mysqladmin -h database_host -uUsername -p create database_name

Then load the SQL file:

    mysql -h database_host -uUsername -p database_name < dump.sql
    
### Source

[Build Your Own Database Driven Website Using PHP &amp; MySQL](http://www.sitepoint.com/books/phpmysql1/), 2nd Edition (Page 133)
