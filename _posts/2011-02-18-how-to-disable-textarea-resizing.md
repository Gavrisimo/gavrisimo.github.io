---
title: How to disable textarea resizing?
author: Miloš Gavrilović
layout: post
permalink: /how-to-disable-textarea-resizing/
categories:
  - Tips
---
Its really simple:

<pre class="brush: css; title: ; notranslate" title="">resize: none;</pre>

But in my opinion this is not really a good thing to do.

I also think that letting visitors re-size textarea both on x and y axis is bad idea. So what seems the best thing to do?

<pre class="brush: css; title: ; notranslate" title="">resize: vertical;</pre>

This way you are letting visitors to re-size textarea only on y axis it works much better then previous two options, again only in my opinion.

### Making it even better!

If you want to limit how much a user can make your textarea big or small you can use this:

<pre class="brush: css; title: ; notranslate" title="">min-height: 100xp;
min-height: 300xp;</pre>
