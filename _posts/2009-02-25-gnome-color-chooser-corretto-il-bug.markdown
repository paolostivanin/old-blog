---
author: pol@blog
comments: true
date: 2009-02-25 20:06:15+00:00
layout: post
slug: gnome-color-chooser-corretto-il-bug
title: Gnome-color-chooser, corretto il bug!
wordpress_id: 608
categories:
- ArchLinux
- Unix
---

Su Archlinux avevo un fastidioso problema: non potevo usare **Gnome Color Chooser!**

Così, all'inizio, mi sono arrangiato modificando a mano il file _gtk2-rc_, solo che ogni tanto c'era qualche problemino grafico sicchè ho girato e rigirato finchè non ho scoperto cosa mi impediva di usare **GCC** su Archlinux: _**UN BUG**_ (ma dai!?!) ;-)

Se anche voi avete questo problema, seguite questa breve guida per avere finalmente **GCC** funzionante sulla nostra Archlinux:


[DOWNLOAD GGC-0.2.4](http://downloads.sourceforge.net/gnomecc/gnome-color-chooser-0.2.4.tar.gz)



Estraiamo la cartella ed entriamo **con nautilus **in _gnome-color-chooser-.0.2.4/src _e cerchiamo il file **main.cc**

Apriamolo quindi con **gedit **ed andiamo alla **riga 190** dove troviamo scritto:


`string customgtkrcfile = gtkrcfile.append("-gnome-color-chooser-");`



bene, quella riga **deve **diventare:


`string customgtkrcfile = gtkrcfile + "-gnome-color-chooser-";`



Bene, salviamo, usciamo, apriamo da **terminale** la cartella gnome-color-chooser-0.2.4 e diamo un bel


`./configure --prefix=/usr`




`make && sudo make install`



Fatto, ora avremo il nostro Gnome Color Chooser installato e funzionante al 100% :D
