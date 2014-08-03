---
title: How to install Canon LBP printers in Ubuntu
author: Miloš Gavrilović
layout: post
permalink: /how-to-install-canon-lbp-printers-in-ubuntu/
categories:
  - Random
---
Excellent article on how to install drivers fro Cannon LBP printers on ubuntu!

You can find original article here:

<a href="http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/" target="_blank">http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/</a>

The current supported printer models are:

> LBP-1120, LBP-1210, LBP2900, LBP3000, LBP3010, LBP3018, LBP3050, LBP3100, LBP3108, LBP3150, LBP3200, LBP3210, LBP3250, LBP3300, LBP3310, LBP3500, LBP5000, LBP5050, LBP5100, LBP5300, LBP7200C.

All you have to do is <a href="http://codebin.cotescu.com/canon/lbp_driver/CanonCAPTdriver.tar.gz" target="_blank">download the script</a> and extract it somewhere on your hdd. Then in terminal cd to that extracted folder and run this:

<pre class="brush: bash; title: ; notranslate" title="">sudo ./canonLBP_install.sh PRINTER_MODEL</pre>

Just change `PRINTER_MODEL` with one model number from above.

Thats it. :)
