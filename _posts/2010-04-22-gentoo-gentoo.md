---
comments: true
date: 2010-04-22 13:48:52+00:00
layout: blog
title: Gentoo? Gentoo!
categories:
- Generale
- Gentoo
- Unix
---

`sudo mount -t ext4 /dev/sda3 /media/gentoo`




`sudo mount -t proc none /media/gentoo/proc`




`sudo mount -o bind /dev /media/gentoo/dev`




`sudo chroot /media/gentoo /bin/bash`


_Tutto tranquillo, compilazione manuale del kernel pure...poi do:_


emerge xorg-server


_E iniziano i problemi.................risolti con:_


`echo dev-libs/cyrus-sasl -ldap >> /etc/portage/package.use`


_Maggiori info nel corso dei prossimi giorni _:)
