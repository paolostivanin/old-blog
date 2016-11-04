---
comments: true
date: 2011-09-30 21:58:48+00:00
layout: post
title: 'Debian + Nvidia + Xorg 1.11.1: bug e soluzione.'
---

Oggi dopo 2 settimane di assenza ho controllato gli aggiornamenti disponibili per la mia Debian testing e ne trovati **237**!

Scorro un po' per vedere cosa mi aspetta e noto che ci sarà un aggiornamento di Xorg e un downgrade dei driver Nvidia...

Vabbè dico, intanto aggiorniamo poi vediamo!

Detto fatto, aggiorno, riavvio e...computer impallatissimo, impossibile muovere il mouse, decine di minuti per aprire nautilus (anzi per riuscire ad andare sull'icona di Nautilus), insomma un rallentamento assurdo del sistema.

Leggo un po' in giro e noto che Xorg 1.11.1 e Nvidia non vanno molto d'accordo così ho pensato di effettuare un downgrade!

Ed è stata **un'ottima scelta** che **consiglio** a tutti quelli che riscontrano/hanno riscontrato problemi :)

<!-- more -->Ecco come fare:


`su`




`nano /etc/apt/sources.list`


Aggiungiamo questo repository:


<blockquote>#Xorg downgrade
deb http://backports.debian.org/debian-backports squeeze-backports main contrib non-free</blockquote>


Downgradiamo i pacchetti che ci servono e le loro dipendenze:


`sudo aptitude install xserver-common=2:1.10.4-1~bpo60+1 xserver-xephyr=2:1.10.4-1~bpo60+1 xserver-xorg-core=2:1.10.4-1~bpo60+1 xserver-xorg-input-evdev=1:2.6.0-2~bpo60+1 xserver-xorg-input-synaptics=1.4.1-1~bpo60+1 xserver-xorg-video-vesa=1:2.3.0-7~bpo60+1`


E infine **blocchiamo gli aggiornamenti **di tali pacchetti in questo modo:


`echo "xserver-common hold"|dpkg --set-selections`




`echo "xserver-xephyr hold"|dpkg --set-selections`




`echo "xserver-xorg-core hold"|dpkg --set-selections`




`echo "xserver-xorg-input-evdev hold"|dpkg --set-selections`




`echo "xserver-xorg-input-synaptics hold"|dpkg --set-selections`




`echo "xserver-xorg-video.vesa hold"|dpkg --set-selections`


Riavviate e godetevi il vostro sistema di nuovo funzionante :)

Enjoy!
