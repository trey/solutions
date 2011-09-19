---
date: 2008-05-19 21:22:04
title: Starting a Magento Theme
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/05/starting-a-magento-theme/
---
<!-- I'm a bit riled about the way this system is setup.  I don't understand who ecommerce systems are designed for, but it sure as hell isn't a designer or someone with a normal since of intuition with computers or web development.  Magento promised to be a better open source shopping cart package, which it seem to be, but it's still far from a pleasure to use.

The theme system is based on XML; which is a terse, unfriendly beast on it's best day.  Locking it in the room with a designer who needs to build something is just cruel.  I think it's time we stop letting programmers build things that are meant to be used by designers.  They need supervision by normal people.

Enough ranting, on with the how-to.
-->
Duplicate these folders:

    app/design/frontend/default/default
    skin/frontend/default/default

(Don't get me started about how awkward the folder structure is.)

Rename the duplicated folders to whatever you want (make them both the same).

FYI, the theme files under the `app/` folder are for generated templates (things the system has to build when the site is viewed) and the theme files under the `skin/` folder are for publicly viewable files (images, CSS, JavaScript).

Now go to your the admin area of your site and then `System > Configuration`.  Then click `Design` in the sidebar and under `Themes` type the name of your theme folders (the ones you duplicated).  Just once.  One name.

Now the fun really begins.  Time to dig into a bluemillion `.phtml` and `.xml` files.  I'm still not too far along here, but I have determined that to change the media that you load in most pages, you need to edit:

    app/design/frontend/default/your_theme_name/layout/page.xml

There you'll se a bunch of crap like this:

    <action method="addCss"><stylesheet>css/reset.css</stylesheet></action>

Have fun.