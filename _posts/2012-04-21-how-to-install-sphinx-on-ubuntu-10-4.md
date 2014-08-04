---
title: How to install sphinx on Ubuntu 10.4
author: Miloš Gavrilović
layout: post
permalink: /how-to-install-sphinx-on-ubuntu-10-4/
---
Today I had to enable sphinx on [crtaci.info](http://www.crtaci.info/) and this is small list of terminal commands I used to get that done.

Download and extract sphinx source:

{% highlight bash linenos %}
cd /tmp
wget http://sphinxsearch.com/files/sphinx-2.0.4-release.tar.gz
tar xzvf sphinx-2.0.4-release.tar.gz
rm -f sphinx-2.0.4-release.tar.gz
cd sphinx-2.0.4-release
{% endhighlight %}

After that all you have to do is this:

{% highlight bash linenos %}
./configure
make
make install
{% endhighlight %}

The server I was installing this on is Ubuntu 10.4 and my host provider is [linode.com](http://www.linode.com/) which means I have very small set of things installed other then `php/apache/mysql`. That's why I had problems with these commands and this is what helped:

`apt-get install libmysqlclient-dev gcc g++`

After that I managed to run all three commands(configure + make) just fine. :)

More info:

[http://sphinxsearch.com/](http://sphinxsearch.com/)
[http://community.invisionpower.com/resources/documentation/index.html/_/tutorials/large-communities/setting-up-sphinx-r181](http://community.invisionpower.com/resources/documentation/index.html/_/tutorials/large-communities/setting-up-sphinx-r181)
[http://stackoverflow.com/questions/8025128/installing-sphinx-on-ubuntu](http://stackoverflow.com/questions/8025128/installing-sphinx-on-ubuntu)

and of course the amazing Linode library:

[http://library.linode.com/](http://library.linode.com/)
