---
date: 2010-06-09 20:36:25
title: Passing a JavaScript Function as a Parameter to Another Function
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2010/06/passing-a-javascript-function-as-a-parameter-to-another-function/
---
	function makeItRain (effect) {
		$('#something')[effect]();
	}

	makeItRain('slideToggle');

Note the lack of a '`.`' and the '`[]`'s.

### Source

- [Hernán](http://twitter.com/hciudad)