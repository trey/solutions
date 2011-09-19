---
date: 2008-06-09 23:10:21
title: Using Something Other Than the Site Root for a Wordpress Posts Page
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/06/wordpress-posts-page/
---
This is so you can use something like `/blog/` for a list of your blog entries, and the home page for a static page (or something fancier).

Under Settings &gt; Reading &gt; Posts page, pick the page template you want to use.

![Setting WordPress Posts page](http://solutions.treypiepmeier.com/wp-content/uploads/2008/06/wp_posts_page.png)

If you're using a static page template for the home page, be sure **not** to name it `home.php`.  Name it something like `homepage.php` and choose that template for the home page (you can still call it "Home" inside the template).

The "Posts page" will use `index.php` whether you like it or not.  I couldn't find a way to override that inside of Post management in WordPress.

