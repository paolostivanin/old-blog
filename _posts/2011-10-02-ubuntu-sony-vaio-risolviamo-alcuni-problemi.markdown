---
author: pol@blog
comments: true
date: 2011-10-02 16:05:52+00:00
layout: post
slug: ubuntu-sony-vaio-risolviamo-alcuni-problemi
title: 'Ubuntu + Sony vaio: risolviamo alcuni problemi!'
wordpress_id: 1581
categories:
- Debian &amp; Co
- Ubuntu
- Unix
tags:
- bluetooth
- debian
- linux
- numlock
- touchpad
- ubuntu
- unity
- vaio
---

Ho da poco acquistato un nuovo notebook ([Sony Vaio](http://www.polslinux.it/info/)) in sostituzione dell'ormai vecchio e lento Eeepc.

Ho deciso di installare Ubuntu 11.10 (devo ammettere che Unity mi intriga) con una riserva di 60GB per qualcos'altro (probabilmente Gentoo!).

Ma bando alle ciance, vediamo quali sono i problemi che ho riscontrato una volta installato Ubuntu:



	
  1. Lo scroll del touchpad non funziona

	
  2. Il numlock non parte al boot del sistema

	
  3. Il bluetooth è sempre acceso al boot del sistema


Partiamo dal problema numero **1** che mi ha impegnato **tanto, molto, parecchio** tempo prima di risolverlo!

<!-- more -->


Innanzitutto installiamo _dkms_ aprendo il terminale e digitando:



    
    sudo apt-get install dkms




poi scaricate [QUESTO](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.9/psmouse-alps-dkms_0.9_all.deb) pacchetto e installatelo con:



    
    sudo dpkg -i psmouse-alps-dkms_0.9_all.deb




nel caso vi siano problemi con altre dipendenze non soddisfatte basta dare da terminale:



    
    sudo apt-get install -f




Fortunatamente sono su Ubuntu e quindi non ho dovuto ricompilare niente ma semplicemente installare un comodo deb :)




Se siete su altre distro [QUI](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.9/) trovate le patch da applicare al kernel...ma quella sarà un'altra guida ;)


Veniamo ora al problema numero **2**, ovvero il numlock attivo al boot del sistema.


Qui ho trovato subito la soluzione ma ho dovuto ragionare un attimo per capire come applicarla dato che Ubuntu 11.10 **non ha più GDM** come display manager ma **LightDM**.




Per risolverle l'inconveniente del numlock basta installare _numlockx_ da terminale con:



    
    sudo apt-get install numlockx




e poi editare il file _Xsession_ in_ /etc/X11_:



    
    sudo nano -w /etc/X11/Xsession




aggiungendo **alla fine del file prima di exit 0**:



    
    if [ -x /usr/bin/numlockx ]; then
    /usr/bin/numlockx on
    fi




_N.B.: questo modo permette l'accensione automatica del numlock **dopo** che è stato effettuato il login. Al momento LightDM non permette di accendere automaticamente il numlock come avveniva prima per GDM._


Infine per ultimo ma non meno fastidioso il problema del bluetooth sempre acceso all'avvio del sistema.


Qui la soluzione è semplice e veloce infatti basta editare il file _/etc/rc.local_:



    
    sudo nano -w /etc/rc.local




aggiungendo **alla fine del file prima di exit 0** la seguente riga:



    
    rfkill block bluetooth




Il bluetooth è poi accendibile normalmente tramite applet ;)


Ecco tutto, ora il notebook è <del>perfettamente</del> funzionante <del>in ogni sua parte</del> :)

Enjoy :)

EDIT: il bluetooth **non** funziona e, ad oggi, non v'è modo di farlo funzioanre :(
