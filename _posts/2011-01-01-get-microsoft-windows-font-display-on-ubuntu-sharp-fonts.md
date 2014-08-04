---
title: Get Microsoft Windows Font Display on Ubuntu (Sharp Fonts)
author: Miloš Gavrilović
layout: post
permalink: /get-microsoft-windows-font-display-on-ubuntu-sharp-fonts/
---
If you hate how your sites look after you made a switch from windows to linux, then this article is for you!

Check it out: [http://www.amitash.com/microsoft-windows-font-display-ubuntu-sharp-fonts.html](http://www.amitash.com/microsoft-windows-font-display-ubuntu-sharp-fonts.html)

You just install microsoft fonts via `synaptic`, download some `.conf` files and move those file into `/etc/fonts` and your sites are beautiful again! :)

One thing thought, I was having some permission issues when I tried to move those new files into `/etc/files` so I had to use terminal: `sudo mv -i /home/gavra/Downloads/conf/* /etc/fonts`

So once you move those files just log out/log in or restart your pc and thats it.
