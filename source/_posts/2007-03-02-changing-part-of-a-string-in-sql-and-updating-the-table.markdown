---
date: 2007-03-02 17:20:53
title: Changing Part of a String in SQL and Updating the Table
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2007/03/changing-part-of-a-string-in-sql-and-updating-the-table/
---
Something like this:

    update `table_name` set `field_name` = replace(`field_name`, 'text_to_replace', 'new_text')

### Sources
* [MySql replace command](http://www.webmasterworld.com/forum10/8113.htm)
* [Using MySQL, Built-In Functions](http://www.keithjbrown.co.uk/vworks/mysql/mysql_p9.php)