---
comments: true
date: 2010-05-12 20:32:37+00:00
layout: post
title: Modificare ebuild Gentoo...
categories:
- Gentoo
- Unix
---

Durante la mia prima installazione di Gentoo ho  installato _gnome-base/gnome_ che si è portato dietro softwares che non mi interessano.

Il problema è che se io disinstallo tali softwares e poi do:


`emerge -uDavN world`


i programmi appena disinstallati verranno (_ovviamente_) reinstallati dato che sono dipendenze di gnome-base/gnome.

Come risolvere sto problema senza troppi casini?

Semplice, basta modificare l'ebuild di Gnome :)

Intanto creiamo una cartella portage per lavorare in locale:


`mkdir /usr/local/portage`


Ora editiamo make.conf e aggiungiamo tale riga:


`PORTDIR_OVERLAY="/usr/local/portage"`


Chiudiamo l'editor e cerchiamo la categoria e il nomepacchetto del pacchetto che ci interessa con:


`emerge -s _$nomepacchetto_`


Creiamo la cartella _$categoria/$nomepacchetto_ (in questo caso gnome-base/gnome):


`mkdir -p /usr/local/portage/gnome-base/gnome`


Copiamo l'ebuild ufficiale nella cartella appena creata:


`cp /usr/portage/gnome-base/gnome/gnome-2.26.3.ebuild /usr/local/portage/gnome-base/gnome/gnome-2.26.3.ebuild`


Entriamo nella cartella:


`cd /usr/local/portage/gnome-base/gnome/`


Editiamo il nostro ebuild in tranquillità togliendo i softwares che non ci interessano:


`nano -w gnome-2.26.3.ebuild`


Chiudiamo l'editor e generiamo il file manifest (**da fare ogni volta che si edita l'ebuild!**)


`ebuild gnome-2.26.3.ebuild manifest`


Disinstalliamo ora i pacchetti che non ci interessano con:


`emerge -C _$nomepacchetti_`


Ora potete dare:


`emerge -uDavN world`


senza problemi :)
