---
author: pol@blog
comments: true
date: 2009-03-15 13:18:35+00:00
layout: post
slug: nuova-major-release-per-i-driver-nvidia-18513-beta
title: 'Nuova major release per i driver Nvidia: 185.13 beta!'
wordpress_id: 640
categories:
- ArchLinux
- Ubuntu
- Unix
---

A poco tempo dalla release **180.37**, ecco spuntare le prime indiscrezioni (e non solo) sui nuovi, nuovissimi, luccianti driver Nvidia: i **185.13 beta.**

**Si tratta della prima release appartenente a questa nuova serie per Linux** e, detta terra terra, si conosce poco e nulla riguardo a questa versione in quanto** il team non ha pubblicato nessun changelog.**

Di certo sembra solo che sia migliorato il supporto a VDPAU ma, essendo un major release, qualcos'altro di buono dovrà pure averlo no?? ;-)

Quindi bando alle chiacchiere e scarichiamo questi nuovi drive (**LEGGERE PRIMA TUTTA LA GUIDA** **E POI FARE I PROCEDIMENTI**):

Apriamo il terminale e, se abbiamo **X86 (32bit)**, scriviamo


`wget ftp://download.nvidia.com/XFree86/Linux-x86/185.13/NVIDIA-Linux-x86-185.13-pkg1.run`



Se invece abbiamo **X86-64 (64bit)**, scriviamo:


`wget ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/NVIDIA-Linux-x86_64-185.13-pkg2.run`



Ora entriamo nella shell **(lo schermo diventa nero quindi stampatevi i passaggi)** con **Ctrl+Alt+F2 **e scriviamo:


`sudo /etc/init.d/gdm stop`




`chmod +x NVIDIA-Linux-_**AAA**_-185.13-pkg2.run` (al posto di _**AAA **_scrivere o **X86** o **X86_64**)




`sudo ./*.run`



Al termine scriviamo


`sudo /etc/init.d/gdm start`



Ed eccoci pronti a goderci questi nuovissimi e misteriosissimi driver che ricordo essere in **VERSIONE BETA!**
