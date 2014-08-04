---
title: Photoshop problem with text tool
author: Miloš Gavrilović
layout: post
permalink: /photoshop-problem-with-text-tool/
categories:
  - Random
---
Recently I had some problems with text tool in Photoshop and after 2-3 reinstalls and no luck in googling for solution, I finally managed to find some article that helped me!

So solution is this:

1.  Close all Adobe applications.
2.  Go to Start and in the search field, type: %USERPROFILE%AppDataLocalAdobe
3.  Delete the TypeSupport folder
4.  Open Photoshop, things should be back to normal.

Original article can be found here:

<a href="http://buithanhtung.wordpress.com/2011/02/11/photoshop-could-not-complete-your-request-because-something-prevented-the-text-engine-from-being-initialized-error/" target="_blank">http://buithanhtung.wordpress.com/2011/02/11/photoshop-could-not-complete-your-request-because-something-prevented-the-text-engine-from-being-initialized-error/</a>
