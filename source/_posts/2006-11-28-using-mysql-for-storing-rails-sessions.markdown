---
date: 2006-11-28 21:27:00
title: Using MySQL for storing Rails sessions
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/11/using-mysql-for-storing-rails-sessions/
---
    $ rake db:sessions:create
    $ rake db:migrate

Possibly use `-c` on the first command to add the migration file to SVN?

Uncomment this line in your `config/environments.rb`:

    config.action_controller.session_store = :active_record_store

Then restart your app.

Doing this is supposed to be more better than the default of using the file system.