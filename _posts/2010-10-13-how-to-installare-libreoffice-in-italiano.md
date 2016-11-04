---
comments: true
date: 2010-10-13 13:12:20+00:00
layout: post
title: '[How-to] Installare Libreoffice in italiano!'
categories:
- Debian &amp; Co
- Ubuntu
- Unix
tags:
- libreoffice
- ubuntu office
---

È da poco uscita la **beta 2 di Libreoffice** e, [tra le altre cose](http://cgit.freedesktop.org/libreoffice/build/tree/NEWS), porta anche la localizzazione in italiano!

D'ora in poi su questa pagina ci sarà lo script per installare Libreoffice nella sua ultima versione **stabile** :)

Certo, non sono scripts scritti da un programmatore professionista ma il loro lavoro lo fanno bene :)

**Attenzione:** **installare libnotify-bin con:** `sudo apt-get install libnotify-bin`

Dopo aver scaricato ed estratto **nella vostra HOME** l'archivio contente entrambi gli scripts, bisogna renderli eseguibili con:


`chmod +x rimozione-oo.sh installazione-libreoffice-it.sh`


Fatto ciò potete eseguirli da terminale **NON ROOT** con il comando:


`./rimozione-oo.sh`


e, una volta rimosso OpenOffice.org:


`./installazione-libreoffice-it.sh`


Ecco fatto! Ora avete Libreoffice installato nella vostra Ubuntu/Debian/deb-derivate-box :)

N.B. nel caso non abbiate più OpenOffice.org non serve eseguire lo script di _rimozione-oo _

**Changelog:**

**v0.1:** script base

**v0.2:** aggiunte notifiche (richiesto **libnotify-bin**)

**v0.3:** pulizia codice e L.O. aggiornato alla beta3

**v3.3.1:** aggiornato libreoffice alla versione 3.3.1, allineato il numero di versione dello script alla versione di L.O.


## [DOWNLOAD SCRIPTS-x86 (v3.3.1)](http://www.polslinux.it/wp-content/uploads/2010/10/scripts-libreoffice-x86-v3.3.1.tar.gz)




## [DOWNLOAD SCRIPTS X86-64 (v3.3.1)](http://www.polslinux.it/wp-content/uploads/2010/10/scripts-libreoffice64-v3.3.1.tar.gz)

D'ora in poi su questa pagina ci sarà lo script per installare Libreoffice nella sua ultima versione disponibile :)

**Attenzione:** **installare libnotify-bin con:** `sudo apt-get install libnotify-bin`

Dopo aver scaricato ed estratto **nella vostra HOME** l'archivio contente lo script bisogna renderlo eseguibile con **_(sostituire $ARCH con x86 oppure x64)_**:


`chmod +x libreoffice-$ARCH-it`


Fatto ciò procedete all'installazione con:


`./libreoffice-$ARCH-it`


Ecco fatto! Ora avete Libreoffice installato nella vostra Ubuntu/Debian/deb-derivate-box :)

**Changelog:**

**v0.1:** script base

**v0.2:** aggiunte notifiche (richiesto **libnotify-bin**)

**v0.3:** pulizia codice e L.O. aggiornato alla beta3

**v3.3.1:** aggiornato libreoffice alla versione 3.3.1 + allineato il numero di versione dello script alla versione di L.O.

**v3.4.0_rc2:** aggiornato libreoffice alla versione 3.4.0_rc2 + rimosso script disinstallazione OpenOffice


## []({{ site.baseurl }}/images/2010/10/libreoffice-x64-it.tar1.gz)




### [Libreoffice 3.4.0_rc2 - x86]({{ site.baseurl }}/images/2010/10/libreoffice-x86-it.tar1.gz)




### []({{ site.baseurl }}/images/2010/10/libreoffice-x64-it.tar1.gz)[Libreoffice 3.4.0_rc2 - x64]({{ site.baseurl }}/images/2010/10/libreoffice-x64-it.tar1.gz)
