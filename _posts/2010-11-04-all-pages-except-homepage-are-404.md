---
title: All pages except homepage are 404!
author: Miloš Gavrilović
layout: post
permalink: /all-pages-except-homepage-are-404/
---
The situation in which I was last night was really scary. After working 6-7 straight hours on one site(powered by WordPress) all of a sudden a problem poped up: all pages except homepage are giving 404 error!

For those who don't know, [http://en.wikipedia.org/wiki/HTTP_404](404 error) basically means page is missing, it is not there.

So anyway, I still cant figure out why that happened because I was doing anything with .htaccess or permalinks...

But after googling for a bit, I found out some solutions to for this problem.

1. In WordPress admin panel go `Settings -> Permalinks` and just hit `Save`. This solution just *might* work for you. *Alas, it didnt work for me.*
2.  In phpmyadmin(or whatever you might be using) just go and repair and then after that optI'mize all WordPress tables. This usually works for me on some other site when some table locks, but *in this case it didn't work*.
3. Log into your FTP and just go ahead and download your `.htaccess`, so you have backup of it, and after that delete `.htaccess` file from your server. After that go in WordPress admin panel and open `Settings -> Permalinks`, select option you want and hit `Save`. *This also didnt work for me.*
4. Log into your FTP and check what permissions does .htaccess file have. If I'm not mistaken it needs to have `777` permissions, so if it does not have those permissions go ahead and fix that. After that go ahead and try option #1 again. *No, this didnt work for me.*

Basically everything I was seeing was that it is either `.htaccess`(permalinks problem) or it was some database problem. Now, I didn't mention that on other WordPress everything was working fine but on the site in question at the tI'me of this problem, the only "pretty" link I could manage to have is the one with index.php in front of it. If I understand anything, it is that if you have index.php in your url and permalinks *won't* work without `index.php`, i.e. you get 404 errors it is because you don't have `mod_rewrite` enabled in apache settings!

More about permalinks on WordPress codex page for [Using Permalinks](http://codex.WordPress.org/Using_Permalinks).

Like I said everything was working on other site that is using WordPress and I'm 100% sure that mod_rewrite is enabled because bunch of other sites were and still are working ok.

What I thought then was "I'm all out if ideas, I just might clean my WordPress database with WP-Cleanup" and that's just what I did. Needless to say the problem was solved simply by using this simple plugin!

So kudos for maybe [the best WordPress plugin ever][http://WordPress.org/extend/plugins/wp-cleanup/]!

## *UPDATE:*

<http://support.makedesignnotwar.com/discussion/583/ecp-1.2.2-possible-bug-with-permalinks>
