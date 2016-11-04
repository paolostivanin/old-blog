---
comments: true
date: 2009-05-14 18:30:47+00:00
layout: post
title: Cairo dock, OpenGL e driver Intel!
categories:
- ArchLinux
- Ubuntu
- Unix
---

Per chi di voi avesse deciso di installare o provare Cairo-dock 2.0.0 avrà notato che, avviando la dock in modalità OpenGL, essa fa i capricci (su schede Intel di sicuro)!

Bene, vediamo di risolvere velocemente questo problema :D :



	
  1. Andate sul menù di Gnome e cliccate col destro, scegliete quindi _Modifica Menù_;

	
  2. Cercate quindi il lanciatore di cairo-dock (with openGL) e cliccate su _Proprietà_;

	
  3. Nella riga del comando c'è scritto _cairo-dock -o _. Bene, esso dovrà diventare _cairo-dock -i_

	
  4. Ora modificate xorg.conf _(gksu gedit /etc/X11/xorg.conf)_ e aggiungete _Option "AccelMethod"   "UXA"_ nella sezione device della scheda video (controllare che ci sia anche la riga _Driver  "intel"_);

	
  5. Fatto, riavviamo Ubuntu e facciamo partire la nostra cairo-dock con il supporto OpenGL :D


Personalmente, anche se non uso queste dock, posso dire che è veramente ben fatta e molto gradevole anche se. a dirla tutta, qualche piccolo buggetto è presente ;-)
