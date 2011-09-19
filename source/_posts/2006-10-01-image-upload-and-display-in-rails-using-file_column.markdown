---
date: 2006-10-01 07:27:20
title: Image upload and display in Rails using file_column
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/image-upload-and-display-in-rails-using-file_column/
---
[This is important:](http://wiki.rubyonrails.org/rails/pages/HowToUseFileColumn)

> just a note about using url_for\_file\_column inside an iteration

> this won't work:

	<% for contact in @contacts %>
	<%= image_tag url_for_file_column "contact", "picture", "thumb"  %>
	<% end %>

> this will:

	<% for @contact in @contacts %>
	<%= image_tag url_for_file_column "contact", "picture", "thumb"  %>
	<% end %>

I don't understand that, but it works.

The stuff about requiring adding stuff to **environment.rb** isn't necessary.

I still haven't configured it to upload where I want or to rename the files.  But it's working, by golly.