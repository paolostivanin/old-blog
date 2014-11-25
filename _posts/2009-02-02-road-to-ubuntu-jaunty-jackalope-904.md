---
comments: true
date: 2009-02-02 19:46:10+00:00
layout: blog
title: 'Road to: Ubuntu Jaunty Jackalope 9.04'
categories:
- Ubuntu
- Unix
---

Eccomi qui a scrivere la mia attuale esperienza su **Ubuntu Jaunty** (futura Ubuntu 9.04, _ndr_).

Ho scaricato la daily-live (1 settimana son andato avanti nell'aspettare quella che funzionasse) e ho bootato il sistema!

Perfetto, non vedo crash, tutto funziona mi son detto "_bon, installo!"_

Ho trovato 2 news nell'installer, rispettivamente questa:


[![](http://www.allfreeportal.com/imghost/thumbs/458264Screenshot-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=458264Screenshot-1.png)



e questa:


[![](http://www.allfreeportal.com/imghost/thumbs/701114Screenshot.png)](http://www.allfreeportal.com/imghost/viewer.php?id=701114Screenshot.png)



La prima _"installer-news"_ consiste nel fatto che possiamo scegliere **EXT4** come file system e la seconda consiste nel fatto che possiamo scegliere una password per criptare/decriptare la nostra home!

Io, ovviamente, ho scelto  **EXT4**, ho inserito le mie info e son partito! Bene anzi, _**MALE!**_

A metà installazione mi viene fuori "ubiquity errore ecc ecc"...a posto! Riavvio, riprovo, medesimo errore!

Allora per sfizio provo a mettere **EXT3 **e indovinate un po'? Funziona!

_NdR: per chi installa con EXT4, siccome grub non lo supporta (grub2 si), deve inserire nel file /boot/grub/menu.lst, al termine della riga kernel=..... **rootfstype=ext4**
_

Vabbè, accedo al mio nuovo sistema, faccio gli aggiornamenti e tutto va felice e sereno!

In più di 4 ore di smodato utilizzo non ho avuto nemmeno un crash, sono contento :D

L'unico neo, l'unico **GRANDE**, **GROSSO** neo della faccenda, sono le** schede video Intel**.

Io infatti monto una _Intel X3100 GMA965_ e facendo il test (che potete fare anche voi, basta aprire il terminale e scrivere _glxgears_) sia su Intrepid che su Jaunty e, su quest'ultima, ho avuto dei_** risultati sconvolgenti**_, a voi i commenti:

**UBUNTU INTREPIX 8.10 (driver intel 2.4.1,  libdrm 2.3.1, mesa 7.2):**


[![](http://www.allfreeportal.com/imghost/thumbs/662249intrepid.png)](http://www.allfreeportal.com/imghost/viewer.php?id=662249intrepid.png)



**UBUNTU JAUNTY 9.04 (driver intel 2.6.1, libdrm 2.4.4, mesa 7.3):**


[![](http://www.allfreeportal.com/imghost/thumbs/988819jaunty.png)](http://www.allfreeportal.com/imghost/viewer.php?id=988819jaunty.png)



I test, ovviamente, sono stati eseguiti a parità di condizioni, ovvero senza programmi attivi o processi _"strani"_ e compiz, naturalmente, attivo.

Che dite si nota qualche differenza di prestazioni?

Sono rimasto veramente sconcertato dal calo così brusco delle prestazioni...per _"fortuna" _ho letto che con il **kernel 2.6.29** si sistemeranno le cose...ora provo a ricompilarlo e vi faccio sapere!

In sintesi, queste sono le info tecniche salienti su Jaunty ad oggi:

**Kernel:** 2.6.28-6-generic

**Gnome:** 2.25.5

**KDE:** 4.2.0

**Alsa: **1.0.18

**Xorg: **1.6 rc2

**Mesa:** 7.3

Ho provato anche **Kubuntu 9.04** ma alcune cose di KDE 4.2 crashavano inesorabilmente e non potevo usare il sistema e, a causa del poco tempo, non potevo star li a sistemare. Mi spiace per i KDEisti ma vi prometto che appena ho tempo farò la recensione di Kubuntu (sperando nel frattempo i bug vengo risolti) :D
