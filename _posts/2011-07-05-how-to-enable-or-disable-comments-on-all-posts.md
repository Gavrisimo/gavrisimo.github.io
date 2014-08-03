---
title: How to enable or disable comments on all posts?
author: Miloš Gavrilović
layout: post
permalink: /how-to-enable-or-disable-comments-on-all-posts/
categories:
  - Tips
  - Wordpress
---
Again, like everything else when it comes to WordPress &#8211; this is really easy! <img src="http://milos.gavrilovic.rs/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> All you need to do is run this one small SQL query.

<pre class="brush: sql; title: ; notranslate" title="">UPDATE wp_posts p SET comment_status = 'open', ping_status = 'open' WHERE comment_status = 'closed';</pre>

That sql query will enable comments on all your posts where comments are closed.

If you want to close comments on all posts where you have comments enabled, you just need to tweak this query a little bit.

<pre class="brush: sql; title: ; notranslate" title="">UPDATE wp_posts p SET comment_status = 'closed', ping_status = 'closed' WHERE comment_status = 'open';</pre>
