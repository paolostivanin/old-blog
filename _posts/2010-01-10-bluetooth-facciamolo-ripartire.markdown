---
author: pol@blog
comments: true
date: 2010-01-10 21:45:22+00:00
layout: post
slug: bluetooth-facciamolo-ripartire
title: Bluetooth, facciamolo ripartire!
wordpress_id: 799
categories:
- ArchLinux
- Ubuntu
- Unix
---

Installato il sistema operativo nuovo di zecca e ti accorgi che l'applet bluetooth è in esecuzione ma non c'è niente nella tray?

Allora decidi di **killiarla** da terminale e farla **ripartire** (sempre da terminale) ma ti accorgi che viene fuori scritto una cosa simile a questa:


`could not open RFKILL, check your installation device`


Bene, il problema è facilmente risolvibile :)

Dopo diversi giorni di ricerche, smanettamenti e prove varie, ho finalmente trovato la soluzione!

Aprite il terminale e date** (da superuser)**


`chmod 666 /dev/rfkill`


Poi, sempre da terminale, **killate l'applet bluetooth e fatela ripartire**!

Ora rendiamo permanente la modifica con un mio trucchetto:


`gedit /home/UTENTE/gnome-bluetooth.sh`


dentro scriviamoci:


`echo TUAPASSWORD | sudo -S chmod 666 /dev/rfkill`


rendiamolo eseguibile con:


`chmod a+x gnome-bluetooth.sh`


ora andate in Sistema --> Preferenze --> Applicazioni Avvio e premete Aggiungi.


`Nome: 1RFKILL`
`Comando: /home/UTENTE/gnome-bluetooth.sh`


Enjoy :D
