---
comments: true
date: 2008-12-04 10:30:15+00:00
layout: post
title: ArchLinux, guida per avere tastiera IT e touchpad funzionanti!
categories:
- ArchLinux
- Unix
---

Dopo 3 giorni di smanettamenti e di odio verso Xorg 1.5.3, sono finalmente riuscito ad avere la mia tastiera in **ITALIANO** e avere finalmente il **TOUCHPAD** **PERFETTAMENTE FUNZIONANTE** :D

Vorreste sapere come ehhhhh???? ;)

Intanto faccio il bakcup dei file con (da terminale root):


`mkdir /home/UTENTE/backup`




`cp /etc/X11/xorg.conf /home/UTENTE/bakcup`




`cp /usr/share/hal/fdi/policy/10osvendor/*keymap* /home/UTENTE/backup`




`cp /usr/share/hal/fdi/policy/10osvendor/*synaptics* /home/UTENTE/backup`



Allora, **se avete queste 3 righe in xorg.conf**


_Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection_

**RIMUOVETELE!**

Ora copiamo i files di hal da /usr a /etc in questo modo


`su`




`PASSWORD`




`cp /usr/share/hal/fdi/policy/10osvendor/*.* /etc/hal/fdi/policy`



Ora **scaricate** i 2 file (li trovate li sotto) relativi la tastiera e il touchpad e copiateli in /etc in questo modo:


`cp /PERCORSO-FILE-SCARICATI/*.* /etc/hal/fdi/policy`



Ora riavviate HAL


`/etc/rc.d/hal restart`



**ed ecco fatto, touchpad funzionante e tastiera in italiano **:D

_**In teoria dovrebbero funzionare anche da voi**_, quelli che ho usato io NON sono file miei adattati per me, ma file generali che ho trovato. Da me funzionano stupendamente bene!

**QUESTA GUIDA NON FUNZIONA SU: **



	
  * **acer aspire one**

	
  * **HP pavilion dv6822el**


---------------------------------

_**FILE DA SCARICARE**_

[keymap](http://www.fileden.com/files/2008/6/10/1953114/10-keymap.fdi)

[touchpad](http://www.fileden.com/files/2008/6/10/1953114/11-x11-synaptics.fdi)

--------------------------------
