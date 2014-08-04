---
title: All pages except homepage are 404!
author: Miloš Gavrilović
layout: post
permalink: /all-pages-except-homepage-are-404/
categories:
  - Wordpress
---
The situation in which I was last night was really scary. After working 6-7 straight hours on one site(powered by wordpress) all of a sudden a problem poped up: all pages except homepage are giving 404 error!

For those who dont know, [http://en.wikipedia.org/wiki/HTTP_404](404 error) basically means page is missing, it is not there.

So anyway, I still cant figure out why that happened because I was doing anything with .htaccess or permalinks...

But after googling for a bit, I found out some solutions to for this problem.

1.  **In wordpress admin panel go &#8220;Settings -> Permalinks&#8221; and just hit &#8220;Save&#8221;.**
    This solution just *might* work for you. Alas, it didnt work for me.
2.  **In phpmyadmin(or whatever you might be using) just go and repair and then after that optimize all wordpress tables.**
    This usually works for me on some other site when some table locks, but in this case it didnt work.
3.  **Log into your FTP and just go ahead and download your .htaccess, so you have backup of it, and after that delete .htaccess file from your server. After that go in wordpress admin panel and open &#8220;Settings -> Permalinks&#8221;, select option you want and hit &#8220;Save&#8221;.
    **This also didnt work for me.
4.  **Log into your FTP and check what permissions does .htaccess file have. If im not mistaken it needs to have 777 permissions, so if it does not have those permissions go ahead and fix that. After that go ahead and try option #1 again.
    **No, this didnt work for me.

Basically everything I was seeing was that its either .htaccess(permalinks problem) or it was some database problem. Now, I didnt mention that on other wordpress everything was working fine but on the site in question at the time of this problem, the only &#8220;pretty&#8221; link I could manage to have is the one with index.php in front of it. If I understand anything than its that if you have index.php in your url and permalinks **wont** work without index.php aka you get 404 errors its because you dont have mod_rewrite enabled in apache settings!

More about permalinks on wordpress codex page for &#8220;<a title="Using Permalinks" href="http://codex.wordpress.org/Using_Permalinks" target="_blank">Using Permalinks</a>&#8221;

Like I said everything was working on other site that is using wordpress and im 100% sure that mod_rewrite is enabled because bunch of other sites were and still are working ok.

What I thought then was &#8220;im all out if ideas, I just might clean my wordpress database with WP-Cleanup&#8221; and thats just what I did. Needless to say the problem was solved simply by using this simple plugin!

So kudos for maybe [the best wordpress plugin ever][1]!

## **UPDATE:**

<http://support.makedesignnotwar.com/discussion/583/ecp-1.2.2-possible-bug-with-permalinks>

 [1]: http://wordpress.org/extend/plugins/wp-cleanup/
