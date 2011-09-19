---
date: 2008-12-01 20:42:14
title: Optimizing a Website for iPhone
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/12/optimizing-a-website-for-iphone/
---
This is primarily for making iPhone-only versions of an existing site/application.

## Set your Viewport

	<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0" />

## Use Media Queries for linking CSS files

	<!-- For iPhone: -->
	<link media="only screen and (max-device-width: 480px)" href="small-device.css" type= "text/css" rel="stylesheet">

	<!-- For everything else: -->
	<link media="screen and (min-device-width: 481px)" href="not-small-device.css" type="text/css" rel="stylesheet">

## Override text size adjustments (in your CSS)

	html { -webkit-text-size-adjust: none; }

## Run in Full-Screen mode

If you want your site/application to run in full screen mode (and separated from the normal mobile Safari) when running from a home screen shortcut, add this meta tag:

	<meta name="apple-mobile-web-app-capable" content="yes">

## Don't forget the Touch Icon

Don't forget to add a nice icon for people who bookmark your site on their home screens.

	<link rel="apple-touch-icon" href="/img/touch_icon.png">

### Sources

- [Related Gist](http://gist.github.com/30333)
- [Daring Fireball: Meta Tag Allows Full-Screen iPhone Web Apps](http://daringfireball.net/linked/2008/10/03/fullscreen-iphone-web-apps)
- [ADC: Using the Viewport Meta Tag](https://developer.apple.com/webapps/docs/documentation/AppleApplications/Reference/SafariWebContent/UsingtheViewport/chapter_4_section_5.html)
- [ADC: Using Conditional CSS](http://developer.apple.com/webapps/docs/documentation/AppleApplications/Reference/SafariWebContent/OptimizingforSafarioniPhone/chapter_3_section_2.html)
- [Safari Reference Library](http://developer.apple.com/safari/library/codinghowtos/mobile/userExperience/index.html)
