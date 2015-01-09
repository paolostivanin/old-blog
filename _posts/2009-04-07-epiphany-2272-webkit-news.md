---
comments: true
date: 2009-04-07 17:01:30+00:00
layout: post
title: Epiphany 2.27.2, webkit & news!
categories:
- ArchLinux
- Unix
---

Ero curioso di provare epiphany con webkit e, avendo letto che da Gnome 2.28 esso l'avrebbe avuto, mi sono compilato da svn il browser web di Gnome :D
Vi scrivo questa semplice, anzi semplicissima,  guida, così potrete avere anche voi l'ultima release webkit di Epiphany.
Bando alle ciance, aprite il terminale e scrivete:

`svn co http://svn.gnome.org/svn/epiphany/trunk epiphany`

Entriamo nella cartella e compiliamo:

`cd epiphany`

`./autogen.sh --prefix=/usr`

`make` (se avete un dual o più core date un bel make -j 3)

`sudo make install`

Perfetto!
Ora clicchiamo su Epiphany ed ecco a voi la nuovissima e fiammante incarnazione webkit di Epiphany!
Volete sapere cosa mi ha subito colpito?



	
  * il 100% sull'acid test 3 (ovviamente webkit powa)

	
  * i 14MB di ram usati con 1 scheda aperta :D


Un paio di screeeeeeeeeeeeeeenshot** (notare la barra degli indirizzi/caricamento nella seconda foto)**:


[![](http://www.allfreeportal.com/imghost/thumbs/565590epiweb.png)](http://www.allfreeportal.com/imghost/viewer.php?id=565590epiweb.png)




[![](http://www.allfreeportal.com/imghost/thumbs/679361caricamento.png)](http://www.allfreeportal.com/imghost/viewer.php?id=679361caricamento.png)
