---
comments: true
date: 2009-06-05 18:29:00+00:00
layout: post
title: Adobe-air, Widget & Archlinux, DA OGGI SI PUÒ!
categories:
- ArchLinux
- Unix
---

Dopo la mia gaffe riguardo al post precedente, mi son rimboccato le maniche e ho cercato una soluzione per sistemare noi Arcieri e...**L'HO TROVATA** :D

Innazitutto scaricate il file già compilato me da qui:


[ADOBE-AIR](http://www.fileden.com/getfile.php?file_path=http://www.fileden.com/files/2008/6/10/1953114/adobe-air-1.5-1-i686.pkg.tar.gz)



aprite il terminale, diventate root (`su` + password) e installatelo con:


`pacman -U /percorso-al-file/*pkg.tar.gz`



poi tornate **normal user** digitando


`exit`



Ora scaricate il widget vodafone dal post precedente, tornate al terminale e scrivete:


`adobe-air /percorso-al-file-air/*.air`



**ET-VOILÀÀÀÀÀÀÀÀÀÀ **:D

Ora per ottimizzare il tutto create una scorciatoia con _"Crea Lanciatore"_ ed avremo il nostro bel widget anche per Archlinux :D

Di nuovo scusa a tutti gli Arcieri per non aver fatto il controllo per Arch la scorsa volta, non succederà più promesso :D


[![](http://www.allfreeportal.com/imghost/thumbs/368516arch.png)](http://www.allfreeportal.com/imghost/viewer.php?id=368516arch.png)
