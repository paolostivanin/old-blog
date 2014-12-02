---
comments: true
date: 2014-12-02
layout: blog
category: blog
title: 'VPN Unlimited on Arch Linux'
summary: 'How to install and use VPN Unlimited on Arch Linux'
image: /images/header_images/mul_logo.png
tags: [archlinux]
---

I bought for just 19 bucks 3 years of the [VPN Unlimited](https://www.vpnunlimitedapp.com/) service.

After I downloaded and unpacked the GNU/Linux client [from their site](https://www.vpnunlimitedapp.com/downloads) I tried to run it but I only received a *library error*.

The main problem is that the binary is linked with Curl 7.23, so we need to install it from AUR along with some dependencies.
	
	pacman -S gksu lsb-release
	pacaur -d pkcs11-helper libcurl-compat (compile with makepkg)

After you installed the software (you just need to copy the files in their correct location) you have to put the following script on /usr/bin/ and chmod it to 755.

	#!/bin/bash

	PID=""
	
	function get_pid {
		PID=$(pidof vpn-unlimited-daemon)
	}
	
	get_pid
	
	if [ -z $PID ];then
		gksu vpn-unlimited-daemon&
		sleep 2
	fi
	
	LD_PRELOAD=libcurl.so.3 vpn-unlimited

Finally you have to modify the file `/usr/share/applications/vpn-unlimited.desktop` and change the line `Exec=vpn-unlimited` to `Exec=$script_bash.sh`
