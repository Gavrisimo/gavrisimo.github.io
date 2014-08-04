---
title: How to enable WordPress auto update with SFTP
author: Miloš Gavrilović
layout: post
permalink: /how-to-enable-wordpress-auto-update-with-sftp/
---
After moving this site over to [Linode.com](http://www.linode.com) on Ubuntu 10.4 powered VPS I started having problems with auto updates and with, what used to be simple task, installing plugins.

The main problem is that I am using SFTP to log in to my VPS in order to browse around or SSH via terminal to administrate it.

After googling for a little bit for a solution on how to fix this, I have found this article:

[http://snowulf.com/2010/06/29/wordpress-enabling-sshsftp-updates](http://snowulf.com/2010/06/29/wordpress-enabling-sshsftp-updates)

{% highlight bash linenos %}
apt-get install libssh2-php
/etc/init.d/apache2 restart
{% endhighlight %}

It's really that simple!

Now, when you go to admin panel and you try to do auto upgrade of WordPress, you will be presented with third option `SSH2`.

### UPDATE 22.02.2014

For some reason this solution didn't work for me on Ubuntu 13.10 so I ended up just using plugin called [SSH SFTP Updater Support](http://wordpress.org/plugins/ssh-sftp-updater-support/)
