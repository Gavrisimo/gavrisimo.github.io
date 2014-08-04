---
title: Updating WordPress
author: Miloš Gavrilović
layout: post
permalink: /updating-wordpress/
categories:
  - Wordpress
---
Ever since moving to VPS hosting I had some issues with updating WordPress that I just didn't spend enough time looking into, maybe because I was lazy... Today I finally fixed that!

The issue I was having is that whenever I was trying to update something in `wp-admin`, be it WP core or some plugin or theme, it always asked me for FTP credentials. Since I was lazy, I just gave it my `root:password` combo and continued with my life.

Of course FTP didn't really work on my VPS, i.e. I didn't want to use it, so I had to find a way for WP to use ssh/sftp, which I explained here: [http://milos.gavrilovic.rs/how-to-enable-wordpress-auto-update-with-sftp/]

The solution now looks so simple that I just can't believe I didn't find out about it earlier...

All you need to do is add this line to your `wp-config.php` file:

`define('FS_METHOD','direct');`

If you have correct file/folder permissions and ownership that should do it!

For me though, that didn't work...

I had to change ownership of the files, since they were owned by `root`. So this is what I did:

`chown -R www-data:www-data /var/www/site/public_html`

Now WordPress installation is completely owned by `apache` and update is working flawlessly.

*Side note: I have no idea at the moment how or does this affect security of the server, so that's the next thing I will investigate! :)*
