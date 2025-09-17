---
date: '2025-08-12T19:14:52+02:00'
draft: true
title: 'Nvibrance'
showToc: true
---

My GTX 1060 does something weird with its colors. It increases contrast and
saturation by cutting off the extremes of the color and brightness spectrum. 

What do I mean by that? Very bright grays become white, very dark grays become black.
They're not skewed towards the extremes of the spectrum, they are being
displayed as literally the same color. A few years ago I found out that the
google search bar is a light gray and not the same color as the background. 
This distorts the view of how anything looks or is supposed to look soooo much. 
I feel like I'm browsing the internet partially blind because some things and
distinctions are just invisible to me.

AND APPARENTLY THAT'S AN INTENDED FEATURE. 

An image 'pops' more if it has a lot of saturated colors and a lot of very dark
and very bright areas. Nvidia thinks I like everything I do to look like a
stolen TV show clip uploaded to youtube with so many filters that the copyright
protection system does not recognize it anymore. 

On Xorg you can disable that. It doesn't persist across reboots (of course it
doesn't), but putting `nvidia-settings -l` in your session script will do the
trick. 

On Wayland, adjusting nvidia settings is not possible, at least not through any
official means. 


