---
author: pol@blog
comments: true
date: 2008-11-21 09:30:37+00:00
layout: post
slug: metacity-2253-gtk-engines-guida-alla-compilazione
title: Rinnoviamo la grafica di Gnome da svn!
wordpress_id: 420
categories:
- ArchLinux
- Ubuntu
- Unix
---

Volete avere **l'ultimissima versione di metacity, gtk-engines, gnome-themes & gnome-themes-extra?**

Quelle super nuove e sbarluccicose? (tipo le lucine di natale, _ndr_)

Non v'importa se sono taggate _unstable_?

Non v'importa se possono disintegrare ogni singolo atomo del vostro piccì?

No?

Bene, allora questa guida fa per voi!

**PREMESSA:**



	
  1. Questa guida è valida per **qualsiasi distro**

	
  2. Installare **subversion** prima di procedere**
**


Innazitutto _scarichiamo metacity da svn_, per fare questo apriamo il terminale e scriviamo:


`svn co http://svn.gnome.org/svn/metacity/trunk metacity`



Una volta terminato il download,_ entriamo nella cartella e inziamo a compilare_:


`cd metacity`




`./autogen.sh --prefix=/usr`




`make`




`sudo make install`




`cd`



Installiamo quindi gtk-engines da svn, per fare questo apriamo di nuovo il terminale e scriviamo:


`svn co http://svn.gnome.org/svn/gtk-engines/trunk gtk-engines`



Una volta terminato il download,_ entriamo nella cartella e inziamo a compilare_:


`cd gtk-engines`




`./autogen.sh --prefix=/usr`




`make`




`sudo make install`




`cd`



Installiamo ora gnome-themes da svn, per fare questo apriamo di nuovo il terminale e scriviamo:


`svn co http://svn.gnome.org/svn/gnome-themes/trunk gnome-themes`



Una volta terminato il download,_ entriamo nella cartella e inziamo a compilare_:


`cd gnome-themes`




`./autogen.sh --prefix=/usr`




`make`




`sudo make install`




`cd`



E infine installiamo gnome-themes-extra da svn, per fare questo apriamo di nuovo il terminale e scriviamo:

`svn co http://svn.gnome.org/svn/gnome-themes-extras/trunk gnome-themes-extras`

Una volta terminato il download,_ entriamo nella cartella e inziamo a compilare_:


`cd gnome-themes-extras`




`./autogen.sh --prefix=/usr`




`make`




`sudo make install`




`cd`



Infine terminiamo la nostra sessione e ri-accediamo!

Ecco a voi il nuovissimo e fiammante Gnome :D

Questo è un esempio del tema Darklooks con icone Droopline-Neu:


[![](http://www.allfreeportal.com/imghost/thumbs/144814Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=144814Schermata.png)




[![](http://www.allfreeportal.com/imghost/thumbs/246928Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=246928Schermata-1.png)
