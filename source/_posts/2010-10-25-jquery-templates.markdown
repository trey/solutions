---
date: 2010-10-25 16:22:56
title: jQuery Templates
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/10/jquery-templates/
---
- [Download jquery-tmpl](http://github.com/jquery/jquery-tmpl)

### Create a Template (most basic way):

	<script id="book-template" type="text/x-jquery-tmpl">
	    <li>${name} (${year})</li>
	</script>

Note that the `type` attribute is set to `text/x-jquery-tmpl` (`text/html` would do the trick as well). Anything other than `text/javascript` is ignored by the browser. Also, leaving it out entirely will default to `text/javascript` (thank you, HTML5 for making it OK to do that).

### Data:


``` javascript
var books = [
    { name: 'The Gunslinger',               year: '1982' },
    { name: 'The Drawing of the Three',     year: '1987' },
    { name: 'The Waste Lands',              year: '1991' },
    { name: 'Wizard and Glass',             year: '1997' },
    { name: 'The Wolves of the Calla',      year: '2003' },
    { name: 'Song of Susannah',             year: '2004' },
    { name: 'The Dark Tower',               year: '2004' },
    { name: 'The Wind Through the Keyhole', year: '2012' }
];
```

### Load the template with data:

	$('#book-template').tmpl(books).appendTo('#book-list');

To be totally explicit: the first selector is the ID of the template (script tag), the argument being passed to `.tmpl` is the array, and then we're appending the whole thing to the `#tower-list` object in the DOM.

Now don't forget some HTML:

	<ul id="book-list"></ul>


### Source
- [jQuery API](http://api.jquery.com/jquery.tmpl/)
- [Wikipedia](http://en.wikipedia.org/wiki/Dark_Tower_series#Series)
