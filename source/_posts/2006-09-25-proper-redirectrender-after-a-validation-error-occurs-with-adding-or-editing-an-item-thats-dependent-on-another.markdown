---
date: 2006-09-25 08:20:00
title: Proper redirect/render after a validation error occurs with adding or editing an item that's dependent on another
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/09/proper-redirectrender-after-a-validation-error-occurs-with-adding-or-editing-an-item-thats-dependent-on-another/
---
Pass the ID of the model above what you're validating (Publisher if you're editing Title) in the URL (GET).  Like so:

    <%= start_form_tag :action => 'create_title', :id => @publisher.id %>

On the `else` for if the item doesn't save (doesn't pass validation), just put:

    redirect_to :action => 'name_of_the_action_where_you_started'

Using `redirect_to` will mean that you don't have to specify the ID of the model above what's being validated, because it doesn't redirect the whole page--just the part of the view that corresponds to that action.  <small>(is that right?)</small>