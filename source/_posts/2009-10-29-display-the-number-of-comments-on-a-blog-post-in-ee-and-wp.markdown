---
date: 2009-10-29 22:13:18
title: Display the Number of Comments on a Blog Post in EE and WP
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/10/display-the-number-of-comments-on-a-blog-post-in-ee-and-wp/
---

``` php ExpressionEngine
<a href="{comment_url_title_auto_path}#comments">{comment_total} {if comment_total == 1}Comment{if:else}Comments{/if}</a>
```

``` php WordPress
<?php comments_popup_link('0 Comments', '1 Comment', '% Comments'); ?>
```
