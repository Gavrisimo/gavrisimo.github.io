---
title: How to force cache to clear without using admin panel?
author: Miloš Gavrilović
layout: post
permalink: /how-to-force-cache-to-clear-without-using-admin-panel/
---
All you need is FTP access to your server.

Just go to your Magento folder on your FTP and delete everything in these two folders:

{% highlight bash linenos %}
/var/cache
/var/session
{% endhighlight %}
