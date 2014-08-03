---
title: How to install sphinx on Ubuntu 10.4
author: Miloš Gavrilović
layout: post
permalink: /how-to-install-sphinx-on-ubuntu-10-4/
categories:
  - Random
---
Today I had to enable sphinx on <a href="http://www.crtaci.info/" target="_blank">crtaci.info</a> and this is small list of terminal commands I used to get that done.

Download and extract sphinx source:

<pre class="brush: bash; title: ; notranslate" title="">cd /tmp
wget http://sphinxsearch.com/files/sphinx-2.0.4-release.tar.gz
tar xzvf sphinx-2.0.4-release.tar.gz
rm -f sphinx-2.0.4-release.tar.gz
cd sphinx-2.0.4-release
</pre>

After that all you have to do is this:

<pre class="brush: bash; title: ; notranslate" title="">./configure
make
make install
</pre>

The server I was installing this on is Ubuntu 10.4 and my host provider is <a href="http://www.linode.com/" target="_blank">linode.com</a> which means I have very small set of things installed other then php/apache/mysql. That&#8217;s why I had problems with these commands and this is what helped:

<pre class="brush: bash; title: ; notranslate" title="">apt-get install libmysqlclient-dev gcc g++
</pre>

After that i managed to run all three commands(configure + make) just fine. :)

More info:
<a href="http://sphinxsearch.com/" target="_blank"> http://sphinxsearch.com/</a>
<a href="http://community.invisionpower.com/resources/documentation/index.html/_/tutorials/large-communities/setting-up-sphinx-r181" target="_blank"> http://community.invisionpower.com/resources/documentation/index.html/_/tutorials/large-communities/setting-up-sphinx-r181</a>
<a href="http://stackoverflow.com/questions/8025128/installing-sphinx-on-ubuntu" target="_blank"> http://stackoverflow.com/questions/8025128/installing-sphinx-on-ubuntu</a>

and of course the amazing Linode library:

<a href="http://library.linode.com/" target="_blank">http://library.linode.com/</a>
