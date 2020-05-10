---
layout: post
author: ZweiEuro
title: Apache, again
---

A few notes when trying to re-setup apache.\
After deleting everything I had for the first apache server I setup, I reinstalled everything after deleting the config, then i found 
[ufw](https://wiki.archlinux.org/index.php/Uncomplicated_Firewall) which i straight up completly missed. I knew of iptables, but I didn't know that this, actually rather convenient tool exists.

This time though I will try to follow a guide, I found [this](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-18-04) from digitalOcean. 
Thankfully I could loads of the steps already since I already set up most of the system.

Sidenote: I actually never got around setting pacman to colour ... for anyone who fergot as well, \#Colour in \/etc\/pacman.conf ,simple \\Sidenote

Now ... step 2 says stuff about adding an apache profile to ufw, well first of I run arch, so the ubuntu stuff straight up won't work, secondly this, apparently seems to be quite out of date.
ufw actually has a general setting for web servers of any kind, including the high sec that I am after.

/etc/ufw/applications.d/ufw-webserver or something along those lines, has the setting for secure, yay, no more searching.

And after some trying ... this isn't really my place to look for instructions, but it's perfectly fine for knowing what to google.

I think I need 2 vhosts ? One for 80 and one for 443, although I think ufw will catch the 80 one, I think I need it for certbot to auto-config the cert... so damn need to go back to that.


Wasn't that hard to get certbot to do what I want it to, it is thogh very much a challenge to get the redirect right ... right now you don't get redirected if you just enter the name ... landing on :80 with no response... which is bad.
It redirects everything else though, which is very annoying as it should also redirect here...
