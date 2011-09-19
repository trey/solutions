---
date: 2006-11-28 21:34:37
title: Changing the name of an app's cookie in Rails
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/11/changing-the-name-of-an-apps-cookie-in-rails/
---
While running [Tracks](http://www.rousette.org.uk/projects/) and another app on my localhost, I realized that every time I did something on one, it would log me out of the other.  Overwriting each other's cookies!

Add this line to your `config/environment.rb`:

    ActionController::Base.session_options[:session_key] = 'yourappnamehere_session_id'

Then restart the app.  All better now.

[Source](http://wiki.rubyonrails.org/rails/pages/HowtoChangeSessionOptions)