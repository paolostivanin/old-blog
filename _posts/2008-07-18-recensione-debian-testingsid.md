---
comments: true
date: 2008-07-18 13:52:13+00:00
layout: post
title: '[Recensione] Debian testing/Sid'
categories:
- Unix
---

Ciao a tutti raga!

Come promesso sono qui a recensire Debian testing!

Allora, dopo aver scaricato il cd da noi preferito (NETINST il mio):

[DOWNLOAD DEBIAN](http://www.debian.org/devel/debian-installer/)

Bootiamo e installiamo Debian (il cui procedimento è quasi identico a Ubuntu).



	
  * Una volta installata, prima di fare qualcosa aggiustiamo i repo COPIANDO E INCOLLANDO QUESTI:


`deb http://security.debian.org/ testing/updates main
deb-src http://security.debian.org/ testing/updates main`

`deb http://www.debian-multimedia.org testing main`
`
deb http://ftp.it.debian.org/debian/ testing main contrib non-free
deb-src http://ftp.it.debian.org/debian/ testing main contrib non-free`



	
  * **PRIMA DI AGGIORNARE INSTALLIAMO LA CHIAVE GPG:**


[DOWNLOAD CHIAVE GPG](http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb)

`cd PERCORSO-AL-FILE`

`dpkg -i *.deb`



	
  * Ora aggiorniamo:


`apt-get update && apt-get dist-upgrade`

Ecco fatto, ora abbiamo la nostra Debian Testing completa sul nostro pc :D

**Per chi volesse usare SID basta che cambi la parola TESTING in SID su tutti i repo!**

A mio parere Debian è una bella distro, leggera e funzionale, perfetta per PC, ma su notebook a me ha creato dei problemi che non ho voglia di star qui a risolvere perchè li trovo dei problemi banali che una distro come Debian non mi aspettavo creasse e sono:



	
  1. non riconoscimento del touchpad

	
  2. riconoscimento scheda wireless ma incapacità di trovare le reti nonostante i driver iwl3945 fossero installati e caricati.


Sinceramente è una distro da consigliare a qualche purista dell'opensource perchè se usi/hai usato Ubuntu non ha senso provare Debian  perchè non ha niente in più (e qualcosa in meno) della derivata Ubuntu. (sembra strano ma è così LOL).

**Qualche screenshot:**

[![](http://www.allfreeportal.com/imghost/thumbs/314719Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=314719Schermata.png)

[![](http://www.allfreeportal.com/imghost/thumbs/511125Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=511125Schermata-1.png)

[![](http://www.allfreeportal.com/imghost/thumbs/139927Schermata-2.png)](http://www.allfreeportal.com/imghost/viewer.php?id=139927Schermata-2.png)

[![](http://www.allfreeportal.com/imghost/thumbs/536452Schermata-3.png)](http://www.allfreeportal.com/imghost/viewer.php?id=536452Schermata-3.png)

[![](http://www.allfreeportal.com/imghost/thumbs/478906Schermata-4.png)](http://www.allfreeportal.com/imghost/viewer.php?id=478906Schermata-4.png)

[![](http://www.allfreeportal.com/imghost/thumbs/972671Schermata-5.png)](http://www.allfreeportal.com/imghost/viewer.php?id=972671Schermata-5.png)

[![](http://www.allfreeportal.com/imghost/thumbs/832683Schermata-6.png)](http://www.allfreeportal.com/imghost/viewer.php?id=832683Schermata-6.png)

[![](http://www.allfreeportal.com/imghost/thumbs/82929Schermata-7.png)](http://www.allfreeportal.com/imghost/viewer.php?id=82929Schermata-7.png)
