title: Quick Tip - Razor Megalodon on Linux
date: 2013-09-24 01:17:51
tags:
- linux
---
I've been using a headset on my gaming computer for the longest time. The Razor Megalodon. It's a USB Headset from Razor which works pretty well on Windows but unfortunately it does not seem to work out of the box on Linux. For me anyway it's always gave me crackling sound when I try to play any audio.

Today I finally discovered the fix for this is actually quite simple. The module snd-usb-audio settings need to be tweaked when using the Megalodon. I created a new file in **/etc/modprobe.d/megalodon.conf** and added a line:

    options snd-usb-audio nrpacks=16

With this setting I no longer hear crackling sound and the headset appears to work perfectly.
