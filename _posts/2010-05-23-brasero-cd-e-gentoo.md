---
comments: true
date: 2010-05-23 13:03:05+00:00
layout: post
title: Brasero, cd e Gentoo!
categories:
- Gentoo
- Unix
---

Aggiungere il **vostro utente** a plugdev e a cdrom e poi controllare che **plugdev** sia aggiunto in haldaemon.

Potete fare ciò con il comando:


`usermod -a -G`


oppure editando da root:


`/etc/group`


Ora brasero vedrà i vostri supporti :)

**PS: ovviamente la premessa è aver abilitato le flag USE appropiate!**
