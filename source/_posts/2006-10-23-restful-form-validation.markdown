---
date: 2006-10-23 22:42:35
title: RESTful form validation?
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/restful-form-validation/
---
So I hear there's not a straightforward way to do validation with a RESTful setup.  Is that true?

If not, how do you do it?

**Update (Oct 29, 2006):** How about this:

> in order to get the error messages âwe have all grown to loveâ back, all you need to do is take this code & throw it at the end of the function above:

    rescue ActiveRecord::RecordInvalid

    render :action => ânewâ

Found that [here](http://metaatem.net/2006/07/31/rest-and-rails-no-reason-to-be-scared/#comment-2460).

So you put that at the very end of your create or update action, and it puts everything back the way it used to be: lists all errors and adds `<div class="fieldWithErrors">` around the field with errors.

Can someone explain to me why this is necessary?  Something about the way that RESTful things pass information back and forth?  Is this going to be fixed (back to the way it used to be) before Rails 1.2?

Most importantly, does doing this hurt any of the `respond_to` stuff?

**Update x2 (Oct 29, 2006):** ... Ok it's late and maybe I'm seeing things, but it looks like just putting `<%= error_messages_for "model" %>` in the view is making everything work.  Jeez.