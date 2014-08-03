---
title: How to force cache to clear without using admin panel?
author: Miloš Gavrilović
layout: post
permalink: /how-to-force-cache-to-clear-without-using-admin-panel/
categories:
  - PHP
  - Tips
---
All you need is FTP access to your server.

Just go to your Magento folder on your FTP and delete everything in these two folders:

<pre class="brush: plain; title: ; notranslate" title="">/var/cache
/var/session
</pre>
