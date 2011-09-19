---
date: 2006-10-22 08:43:02
title: Using SQLite with Rails
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/using-sqlite-with-rails/
---
After watching the [RESTful Rails PeepCode presentation](http://peepcode.com/articles/2006/10/08/restful-rails), I had to try using [SQLite](http://www.sqlite.org/) for development.  That's nice to not have to set up a database for every little thing you want to play with.

SQLite 3 is already installed on OS X.  To get it to work with Rails:

	$ sudo port install swig
	$ sudo gem install sqlite3-ruby
	
That will bring up a prompt to choose a gem.  Choose the highest version number that says (ruby) after it.

Then you can do things like this in your `database.yml`:

	development:
	  adapter: sqlite3
	  database: db/development.sqlite3

**Source: [Rails wiki](http://wiki.rubyonrails.org/rails/pages/HowtoUseSQLite)**