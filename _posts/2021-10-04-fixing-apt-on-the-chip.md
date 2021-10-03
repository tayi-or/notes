---
layout: post
category: linux
tags:
  - linux
  - debian
  - jessie
  - chip
  - pocketchip
  - ntc
  - nextthingco
title: fixing apt on the C.H.I.P.
---

Since NTC thing went bust years ago, there have been no official builds of the C.H.I.P. OS, which runs a modified version of Debian Jessie, and due to time being a thing, this isn't very great.

If you have a fresh C.H.I.P. install, you can do this to get APT working again.

0. Use the USB serial to setup instead of the not great keyboard of the PocketC.H.I.P. 
  * On a Mac (& probably Linux), open Terminal and `screen /dev/tty.usbmodem*`.
  * Unsure about Windows, but PuTTY is probably what you're after.
1. Download the `armhf` versions of the following packages packages: (visit the linked pages, ctrl+f for the package name, and copy the url, and then run `wget [URL]`)
  * [`apt-transport-https`](http://ftp.us.debian.org/debian//pool/main/a/apt/)
  * [`ca-certificates`](http://ftp.us.debian.org/debian/pool/main/c/ca-certificates/)
  * [`debian-archive-keyring`](http://ftp.us.debian.org/debian/pool/main/d/debian-archive-keyring)
2. Install all the listed packages with the following command `sudo dpkg -i *.deb`
3. Edit `/etc/apt/sources.list` to have the following contents.

```
deb http://archive.debian.org/debian/ jessie main contrib non-free
deb-src http://archive.debian.org/debian/ jessie main contrib non-free

deb http://security.debian.org/ jessie/updates main contrib non-free
deb-src http://security.debian.org/ jessie/updates main contrib non-free

deb http://archive.debian.org/debian jessie-backports main contrib non-free 
deb-src http://archive.debian.org/debian jessie-backports main contrib non-free

deb http://chip.jfpossibilities.com/chip/debian/repo jessie main

deb http://chip.jfpossibilities.com/chip/debian/pocketchip jessie main
```
4. Edit `/etc/apt/apt.conf.d/99-no-ssl.conf` to be the following:

```
Acquire {
        https::Verify-Peer false;
        Check-Valid-Until false;
}
APT:Get::AllowUnauthenticated true;
```

:warning: This will disable security measures to validate the integrity of the software installed on the device. If you trust that Debian isn't gonna get hacked, and that you only connect to trusted WiFi, this shouldn't be an issue though.

5. With any luck, `sudo apt update` should now work 🎉
  * Follow the upgrade instructions [here](https://www.reddit.com/r/ChipCommunity/comments/htkasm/chip_flashing_guide_july_2020/) if you want a newer version of Debian.
