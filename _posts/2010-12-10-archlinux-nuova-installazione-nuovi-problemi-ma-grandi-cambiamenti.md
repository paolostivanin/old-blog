---
comments: true
date: 2010-12-10 15:30:34+00:00
layout: post
title: 'Archlinux: nuova installazione, nuovi problemi ma grandi cambiamenti!'
---

Oggi ho approfittato del mio tempo libero per dare una bella pulita all'hard disk del fisso di casa...

Partendo da 232 GB divisi in:


150 GB --> Win 7




82 GB --> Ubuntu 10.04


Ho modifcato la situazione in:


80 GB --> Win 7




100 GB --> Dati




52 GB --> ArchLinux


Il motivo principale del cambio da Ubuntu ad ArchLinux è causato dal fatto che non ne posso più di dover:



	
  1. Ricorrere a _millemila _repository esterni per avere il software un minimo aggiornato

	
  2. formattare ogni 6 mesi per avere sempre le "ultime" versioni


Così dopo aver installato Windows 7 ho proceduto ad installare Arch come al solito: partiziono, sistemo rc.conf, aggiorno, installo X, fonts, gnome, cups, ecc...
<!-- more -->
Un **primo** grande cambiamento (fin'ora mai preso in considerazione) è stato il fatto che, al posto di usare i soliti driver closed Nvidia, ho usato i [Nouveau](http://nouveau.freedesktop.org/wiki/) con - ovviamente - il supporto 3D (dri)

Vedremo nei prossimi giorni se questo cambiamento è stato furbo o meno :)

Una **seconda** cosa che ho _"killato"_ dai software normalmente installati è stato Compiz. Infatti ho pensato, dato che l'ho usato solo nella configurazione di default di Ubuntu, _"che che me ne faccio??"_ Eh appunto niente. Sicchè ho deciso di _switchare_ a Metacity che, seppur non offrendo molto, almeno mi permette di non avere le righe nere quando sposto le finestre e - a me - tanto basta :)

Procedendo con l'installazione sono arrivato al punto di configuare il _login display manager_ (nel mio caso GDM) e ho optato per la solita scelta: _[/etc/inittab](https://wiki.archlinux.org/index.php/Inittab)_

Bene, al riavvio GDM mi dava una vastità di errori killandomi X e riducendomi alla shell. Siccome questo problema mi era già capitato, ho deciso di risolverlo come la scorsa volta: cambio metodo, al posto di inittab metto il demone in rc.conf **senza** **_@_**.

Effettuo quindi il riavvio e niente. Ennesimo errore! Magico dico...e ora?

E ora provo col metodo startx automatico da inittab, per capirci questo:


`x:5:once:/bin/su PREFERED_USER -l -c '/usr/bin/startx >/dev/null 2>&1'`


Ma sta cosa mi ha devastato tutto...temporanemente per fortuna! (il locale non era più settato su utf ma su POSIX, il comando localegen non esisteva, pacman non funzionava e via dicendo)

Tolgo quindi quella linea e ricorro ad un altro LDM...scelgo [Slim](http://slim.berlios.de/index.php)!

Semplice e veloce, installo, demonizzo, riavvio, metto le crendiziali e..._Utente non riconosciuto_

_ _

[caption id="attachment_1010" align="aligncenter" width="300" caption="Panico! Che succede? :O"]_[![]({{ site.baseurl }}/images/2010/12/Fry-urlo1-300x273.gif)]({{ site.baseurl }}/images/2010/12/Fry-urlo1.gif)_[/caption]

Ah già...c'è un file _/etc/slim.conf_ da configurare...ora lo so ;)

Dopo aver effettuato l'accesso alla sessione noto che la tastiera è in inglese. All'inizio ho pensato che come sempre sia HAL con i suoi _.fdi_ che si mette in mezzo e quindi, dopo aver modificato il file keymap e dopo averlo messo in /etc/hal/fdi/policy, ho riavviato il sistema e...il layout era ancora in inglese.

[caption id="attachment_1013" align="aligncenter" width="274" caption="Che c'è ancoraaaaaa!"][![]({{ site.baseurl }}/images/2010/12/aaah1-274x300.gif)]({{ site.baseurl }}/images/2010/12/aaah1.gif)[/caption]

Ok, calma e sangue freddo, informiamoci su cosa possa essere.

Dopo qualche minuto scopro che:



	
  1. Slim ignora HAL e le sue regole

	
  2. Slim ignora xorg.conf

	
  3. Slim legge, vuole e pretende che le info siano lette dal file di file di configurazione di evdev estensione dello xorg.conf di evdev


Quindi procedo con un


`nano -w /etc/X11/xorg.conf.d/10-evdev.conf`


e aggiungo


`Option "XkbLayout" "it"`


dove c'è scritto_ Identifier "evdev keyboard catchall"_

Riavvio per l'ennesima volta...ohhhhhhh finalmente tutto funziona come deve!

Così dopo aver installato un tema, degli sfondi, nfs, denyhosts, ssh, codec, libreoffice, ecc finalmente ho la mia bella ArchLinux funzionante e ottimizzata al 100%!

Adesso mi resta da collaudare i driver nouveau, ricompilarmi il kernel e fare uno script che mi backuppi i files di configurazione...
