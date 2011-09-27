---
date: 2010-06-09 20:43:20
title: Create a JavaScript Object with Overwrite-able Settings
category: JavaScript
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/06/create-a-javascript-object-with-overwrite-able-settings/
---

```javascript
var Fancy = {
	settings: {
		something: 'one',
		somethingElse: 'two'
	},
	init: function(options){
		var s = $.extend({}, this.settings, options);
	}
}
```

Call it like so:

```javascript
Fancy.init({something: 'Luke', somethingElse: 'Wroblewski'});
```

That's one way to do it anyway.