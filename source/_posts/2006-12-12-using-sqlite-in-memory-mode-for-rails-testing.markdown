---
date: 2006-12-12 03:47:01
title: Using SQLite in memory mode for Rails testing
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/12/using-sqlite-in-memory-mode-for-rails-testing/
---
Watching the [latest PeepCode](http://www.peepcode.com/articles/2006/11/26/test-first-development) at about the 15:00 mark, he mentions using SQLite in memory mode for your testing database.  Here's what you put in your `config/database.yml`:

    test:
      adapter: sqlite3
      database: ":memory:"
      verbosity: silent

Run these commands:

    $ script/plugin install memory_test_fix (use `--force` if you have any problems)
    $ rake db:migrate
    $ rake

Then you're ready to go.

###Sources:

* [nubyonrails.com](http://nubyonrails.com/articles/2006/06/01/san-francisco-sqlite3-memory-tests-asteroids)
* [PeepCode](http://www.peepcode.com/articles/2006/11/26/test-first-development)

See also [how to set up SQLite for Rails](http://solutions.treypiepmeier.com/2006/10/22/using-sqlite-with-rails/)