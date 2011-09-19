---
date: 2006-09-21 00:19:32
title: Ternary Operator
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2006/09/ternary-operator/
---
Like this:

    $variable = condition ? if true : if false

Get it?

    if ($cake == "fresh") {
        print "Yum yum! This cake is tasty.";
    } else {
        print "Yuck! This cake tastes awful!";
    }

    // This can be rewritten as the following ternary statement:

    $message = ($cake == "fresh") ? "Yum yum! This cake is tasty." : "Yuck! This cake tastes awful!";

### Sources

- [Wikipedia](http://en.wikipedia.org/wiki/Ternary_operation)
- <a href="http://us3.php.net/language.operators.comparison#language.operators.comparison.ternary">PHP Docs</a>.

If/Then/Else statments are a type of Control Structure: [Wikipedia](http://en.wikipedia.org/wiki/Control_structure), [PHP docs](http://us3.php.net/if).
