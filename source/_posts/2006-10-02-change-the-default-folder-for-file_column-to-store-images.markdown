---
date: 2006-10-02 20:44:19
title: Change the default folder for file_column to store images
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/10/change-the-default-folder-for-file_column-to-store-images/
---
**Update 2006-12-31:** I don't think this is quite right.  It keeps creating a folder in my Rails root as well as in `public/`.  I think I might switch to [acts\_as\_attachment](http://technoweenie.stikipad.com/plugins/show/Acts+as+Attachment) anyway.

* [General info](http://wiki.rubyonrails.org/rails/pages/HowToUseFileColumn)
* [How to get images to work](http://www.nabble.com/file_column-and-custom-store_dir-t1449776.html)

In your model, where you define the sizes and whatnot that you want, put:

    file_column :database_column_name,
      :store_dir => 'path/you/want',
      :base_url => 'path/you/want',
      (the rest of your configuration)

So what you end up with is images going into `rails_root/public/path/you/want/database_id_of_image/`