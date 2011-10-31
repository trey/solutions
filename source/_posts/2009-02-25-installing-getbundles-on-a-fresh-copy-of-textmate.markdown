---
title: Installing GetBundles on a Fresh Copy of TextMate
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/02/installing-getbundles-on-a-fresh-copy-of-textmate/
---

```
mkdir -p ~/Library/Application\ Support/TextMate/Bundles
cd !$
svn co http://svn.textmate.org/trunk/Review/Bundles/GetBundles.tmbundle/
osascript -e 'tell app "TextMate" to reload bundles'
```

### Sources

- [Alex Payne -- How I Use TextMate](http://al3x.net/2008/12/03/how-i-use-textmate.html)
- [TextMate Blog -- Bundles and GitHub](http://blog.macromates.com/2008/bundles-and-github/)

