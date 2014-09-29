---
comments: true
date: 2008-07-11 09:46:16+00:00
layout: post
title: 'Distro provata: Arch Linux 2008.06 per i686!'
categories:
- Unix
---

## **F-A-N-T-A-S-T-I-C-A!**


Ecco cosa posso dire di questa distro, FANTASTICA!

Penso che esistano poche se non nessuna distro così aggiornata e così funzionale!

Qualche esempio?

Beh, con un comando si installano java, flash, codec senza nessun smanettamento (e java su ubuntu fa dannare).

Poi gli aggiornamenti sono impressionanti, mentre su Ubuntu Gnome 2.22.3 è uscito ieri e neanche tutto, su Arch lo ho da una settimana e mezza!

E **non** sto usando i **repo testing e unstable** altrimenti avrei una distro che neanche debian sid sa cosa vuol dire "essere aggiornati" ;)

Ma veniamo a qualche particolare tecnico:

**Kernel:** sempre l'ultimo uscito, in questo caso il 2.6.25.10 (il kernel si aggiorna ogni volta che esce un kernel nuovo, senza bisogno di smanettamenti o altro)

**Desktop Enviorment:** sempre l'ultimo uscito, in questo caso Gnome 2.22.3, ma potreste avere l'ultima versione di KDE, FluxBox, OpenBox, E-17, Wim, ecc

**Riconoscimento hardware:** ECCELLENTE. Con quest'ultima release hanno eliminato dei piccolo ma fastidiosi bug al wifi, ora tutto funziona alla perfezione :D

**Tempo boot e shutdown:** estremamente corti, ora che si accende/spegne Ubuntu accendo/spegno 2 volte Arch e non sto scherzando.

**Possibilità di personalizzazione (installazione compresa):** TOTALE. Dal DE ai programmi, a tutto.

**Pacchetti:** tantissimi. Fra i repo ufficilai e AUR non temente nulla.

**Pregi:**



	
  * ** **rolling distro, ovvero si aggiorna continuamente senza dover aspettare Major Release (come Ubuntu, Fedora, Mandriva, ecc)

	
  * ottimo sistema di gestioni pacchetti e dipendenze (pacman)

	
  * super personalizzabile

	
  * veloce, scattante, non consuma niente in ram e cpu. (poi dipende dai servizi che metti)

	
  * installazione di codecs estremamente facile e veloce


**Difetti **(se così si possono chiamare, personalmente non li ritengo difetti)**:**



	
  * Installazione lunga. Ci vuole tempo per personalizzare tutto, almeno un paio d'ore.

	
  * Flash non è supportato bene per X86_64 quindi bisogna smanettare un pochino (ma nel forum sono tutti gentili, quindi DON'T UARRI! ;-))


Dopo aver installato Arch Linux, la cui guida super completa è questa:

[GUIDA D'INIZIO PER ARCH LINUX](http://www.archlinux.it/wiki/index.php?title=Beginners_Guide_(Italiano)#DON.27T_PANIC.21)

Installiamo il necessario per avere la nostra Arch-Box funzionante :D



	
  * Partiamo con installare Flash:


`pacman -S flashplugin`



	
  * Poi installiamo Java:


`pacman  -S jre ` (al termine ci dirà di installare una libreria per farlo andare su firefox, installiamo mi raccomando! Inoltre dovrete leggere la LICENSE di java con `nano /opt/java/jre/LICENSE`)



	
  * Installiamo i codecs vari:


`pacman -S codecs`



	
  * Installiamo Openoffice


`pacman -S openoffice-it`



	
  * Installiamo il necessario per i dvd:


`pacman -S totem-xine libdvdread libdvdcss libdvdnav`

Ecco fatto, ora abbiamo la nostra Arch box completa del minimo necessario per vivere!

A voi il resto ora :D

I comandi li ho specificati nella guida di Arch 64 bit, quindi guardateli la :D

**Una cosa, per installare pacchetti da AUR, bisogna installare YAOURT e ci sono due modi:**

**1)**

`su ` (e poi password)

`nano /etc/pacman.conf`



	
  * aggiungiamo questa riga alla fine:


[archlinuxfr]
Server = [http://repo.archlinux.fr/i686](http://repo.archlinux.fr/i686)



	
  * Sincronizziamo e installiamo:


`pacman -Sy yaourt`

Ora se volete potete disabilitare questo server mettendoci degli # davanti alle 2 righe.

**2)**

`wget [http://aur.archlinux.org/packages/yaourt/yaourt/PKGBUILD](http://aur.archlinux.org/packages/yaourt/yaourt/PKGBUILD)`` wget [http://aur.archlinux.org/packages/yaourt/yaourt/yaourt.install](http://aur.archlinux.org/packages/yaourt/yaourt/yaourt.install)`

`[](http://aur.archlinux.org/packages/yaourt/yaourt/yaourt.install)makepkg`



	
  * Rinonimare l'archivio in:


yaourt.tar.gz

	
  * E poi fare:


`pacman -U yaourt-*-pkg.tar.gz`



	
  * Infine, per usare yaourt basta fare: `yaourt -S` nomepacchetto


Un po' di screen per voi raga:

**Desktop vuoto:**

[![](http://www.allfreeportal.com/imghost/thumbs/963392Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=963392Schermata.png)

**Monitor Sistema:
**
[![](http://www.allfreeportal.com/imghost/thumbs/901060Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=901060Schermata-1.png)

**Pacman:**

[![](http://www.allfreeportal.com/imghost/thumbs/7488Schermata-2.png)](http://www.allfreeportal.com/imghost/viewer.php?id=7488Schermata-2.png)

**
Fonts:**

[![](http://www.allfreeportal.com/imghost/thumbs/224188Schermata-3.png)](http://www.allfreeportal.com/imghost/viewer.php?id=224188Schermata-3.png)

**
Altri wallpapers predefiniti:**

[![](http://www.allfreeportal.com/imghost/thumbs/770914Schermata-4.png)](http://www.allfreeportal.com/imghost/viewer.php?id=770914Schermata-4.png)
