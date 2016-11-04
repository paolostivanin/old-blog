---
comments: true
date: 2012-10-26 09:43:21+00:00
layout: post
title: '[how-to] Get the bluetooth adapter 0489:E027 working on GNU/Linux'
---

Dear readers,

today **is a happy and joyous day** because i finally managed to get my laptop's bluetooth adapter to work (_Sony Vaio VPCEH1S0E_)!!

**The problem:**

the bluetooth adapter _(which is an Atheros AR3011 [0489:e027 foxconn hon/hai])_ is not recognized (i've reported a bug to the Ubuntu Kernel Team, you can see it [HERE](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826)).

There is no way _(until today)_  to get it to work. If you try with `hciconfig hci0 up `you'll get an error similar to `error timeout 110` and the `BD Address` will always be `00:00:00:00:00:00`

**The solution:**

<!-- more -->After **months** of research, today I managed to write the patch that fixed the bug so i've sent it to the [Ubuntu](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826) and [Gentoo](https://bugs.gentoo.org/show_bug.cgi?id=439620) mainline kernel team and, of course, to the[ upstream Linux kernel team](https://bugzilla.kernel.org/show_bug.cgi?id=49521)

I have tested my patch on Gentoo amd64 _(gentoo-sources-3.6.*, bluez-4.101, linux-firmware-20120917)_ and on Ubuntu 12.10 amd64 _(kernel 3.5.0-18-generic, bluez-4.101, linux-firmware-1.95)_ but, while on Gentoo** i was able to get it to work**, on Ubuntu there are still some problems (_maybe due to the older kernel_ _you cannot pair the pc<->phone)_.

If you are on **Gentoo** you can follow these simple steps:



	
  1. check if yours gentoo-sources is >= 3.6

	
  2. `emerge gnome-user-share` (you **must** emerge it if you want be able to receive files)

	
  3. `emerge linux-firmware`

	
  4. download [THIS]({{ site.baseurl }}/images/2012/10/fix-bluetooth1.tar) file and extract it to /usr/src/linux/drivers/bluetooth

	
  5. `cd /usr/src/linux/drivers/bluetooth`

	
  6. `cp ath3k.c ath3k.c.orig`

	
  7. `cp btusb.c btusb.c.orig`

	
  8. `patch < 0489e027-ath3k.patch`

	
  9. `patch < 0489e027-btusb.patch`

	
  10. `cd ../../`

	
  11. `make drivers/bluetooth/ath3k.ko`

	
  12. `make drivers/bluetooth/btusb.ko`

	
  13. `cp drivers/bluetooth/ath3k.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/`

	
  14. `cp drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/`

	
  15. `depmod -a`

	
  16. add ath3k and btusb to /etc/conf.d/modules

	
  17. reboot. Now with `lsusb` you should see A`theros Communications, Inc. AR3011 Bluetooth` instead of `0489:e027 foxconn hon/hai`


If you are on U/K/Xu/buntu the steps to follow are:

	
  1. `sudo apt-get install linux-source`

	
  2. `cd /usr/src/linux-source-3.5.0/`

	
  3. `sudo tar xvjf linux-source-3.5.0.tar.bz2`

	
  4. `sudo make oldconfig`

	
  5. `sudo cp linux-source-3.5.0/drivers/bluetooth/ath3k.c linux-source-3.5.0/drivers/bluetooth/ath3k.c.orig`

	
  6. `sudo cp linux-source-3.5.0/drivers/bluetooth/btusb.c linux-source-3.5.0/drivers/bluetooth/btusb.c.orig`

	
  7. download [THIS]({{ site.baseurl }}/images/2012/10/fix-bluetooth1.tar) file and extract it to /usr/src/linux-source-3.5.0/linux-source-3.5.0/drivers/bluetooth/

	
  8. `cd linux-source-3.5.0/drivers/bluetooth/`

	
  9. `sudo patch < 0489e027-ath3k.patch`

	
  10. `sudo patch < 0489e027-btusb.patch`

	
  11. `cd ../../`

	
  12. `sudo make -C /lib/modules/$(uname -r)/build  M=`pwd` drivers/bluetooth/btusb.ko`

	
  13. `sudo make -C /lib/modules/$(uname -r)/build  M=`pwd` drivers/bluetooth/ath3k.ko`

	
  14. `sudo cp drivers/bluetooth/ath3k.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/`

	
  15. `sudo cp drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/`

	
  16. `sudo depmod -a`

	
  17. add ath3k and btusb to /etc/modules

	
  18. reboot. Now with `lsusb` you should see A`theros Communications, Inc. AR3011 Bluetooth` instead of `0489:e027 foxconn hon/hai`


I hope that this tutorial will be helpful to a lot of other people :-)

PS: if you have a similar device _(like **0489**: xxxx)_ and it doesn't work then you can [contact me](http://www.polslinux.it/contattami/). I will try to write a patch also for yours adapter ;-)

Enjoy :-)
