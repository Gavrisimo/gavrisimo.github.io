---
title: How to move wordpress site from localhost to web server?
author: Miloš Gavrilović
layout: post
permalink: /how-to-move-wordpress-site-from-localhost-to-web-server/
---
With only 3 SQL queries! :)

Just move every file from your localhost to web server via ftp, then export wordpress database from localhost and import it on your web server.

After that all you have to do is run these 3 SQL queries:

{% highlight sql linenos %}
UPDATE wp_options SET option_value = replace( option_value, 'http://localhost', 'http://web-server' ) WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET guid = replace(guid, 'http://localhost','http://web-server');
UPDATE wp_posts SET post_content = replace(post_content, 'http://localhost','http://web-server');
{% endhighlight %}

Just replace `http://localhost` with whatever you have in your database, it can be any of these:

1. `localhost`
2. `http://localhost`
3. `127.0.0.1`
4. `http://127.0.0.1`
5. etc...

If you are not sure what value you have there, you can run this SQL query to check that out: `SELECT option_value FROM wp_options WHERE option_name = 'siteurl'`
