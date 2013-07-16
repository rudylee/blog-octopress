---
author: admin
comments: true
date: 2011-05-24 04:45:58+00:00
layout: post
slug: wordpress-uses-the-latest-jquery
title: Make wordpress using the latest jQuery
wordpress_id: 597
categories:
- Wordpress
tags:
- ajax
- content theme
- jquery
- libs
- snippet
- theme folder
- wp
---

I just copied this from another website, put it here just in case that I forgot.

``` php
if( !is_admin()){
    wp_deregister_script('jquery');
    wp_register_script('jquery', ("http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"), false, '');
    wp_enqueue_script('jquery');
}
```

Put this snippet to functions.php file in your theme folder ( eg : wp-content/theme/whatever/functions.php )
