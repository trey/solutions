---
layout: post
title: "Sorting JavaScript Arrays in Numerical Order"
date: 2011-10-14 14:21
comments: true
categories: [JavaScript]
---

I do not understand why this is was so difficult to figure out.

You'll need [Underscore.js](http://documentcloud.github.com/underscore/) to play along at home.

Start with an array like

``` javascript
var sizes = [4, 1, 10, 8];
```

If you just use JavaScript's built in `.sort()` method, you'll end up with

``` javascript
sizes.sort();
// results in [1, 10, 4, 8]
```

This is because it sorts lexicographically by default. Why? Because it (doesn't) love you.

Here's how to do it using Underscore's `sortBy` method:

``` javascript
sizes = _.sortBy( sizes, function( val ){ return val; } );
// results in [1, 4, 8, 10]
```

Why does this work? I'm not sure. Ask your dad.

### Source

- [Stack Overflow](http://stackoverflow.com/questions/4929924/how-to-sort-a-javascript-object-or-convert-it-to-an-array/4929935#4929935)
