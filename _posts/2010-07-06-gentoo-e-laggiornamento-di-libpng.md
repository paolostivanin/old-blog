---
comments: true
date: 2010-07-06 21:08:20+00:00
layout: post
title: Gentoo e l'aggiornamento di libpng!
categories:
- Gentoo
- Unix
---

Qualche giorno fa è stata aggiornata libpng dalla versione 1.2.44 alla versione 1.4.3...bene, update andato a buon fine!

Spengo e vado a nanna.

Un paio di giorni dopo, mentre aggiornavo i codec gstreamer, un errore mi ha insospettito: _gst-plugins-pango_ non compilava a causa di un problema con _libpng12_.

Vabbè dico, diamo un bel _revdep-rebuild _e tutto si sistema...sè...credeteci voi (pure io ci speravo ;) )...

Devono essere _riemersi _**60 pacchetti**...un'infinità per il mio _eeepiccolo_ ma io non dispero, tanto non dovevo usarlo e poteva macinare tranquillamente..............

Così dopo circa 2 ore e 15 minuti, al pacchetto 53/60, _compiz-plugins-extra _decide di darmi errore, sempre a causa di libpng12...ARGH! :(

Cerco un po' in giro...e trovo [QUESTA](http://blog.flameeyes.eu/2010/06/29/stable-users-libpng-update) soluzione che mi ha illuminato la via :)

**Premessa 1:** installare lafilefixer con emerge, ovvero: _emerge lafilefixer_

**Premessa 2: **bisogna editare un file, precisamente _/etc/portage/bashrc_


`post_src_install() {
lafilefixer "${D}"
}`


Poi bisogna compiere questi passaggi:


`emerge -C =libpng-1.2*`




` `




`rm -f /usr/lib/libpng12.so*`




`emerge -1 =libpng-1.4*`


` `


`revdep-rebuild -- --keep-going`


Se il tutto (dopo aver fatto i passaggi sopra scritti) non dovesse funzionare provare con:


`lafilefixer --justfixit`


E tutto sarà tornato alla normalità! _**Revdeppare**_ per credere :D

Morale della favola? Oh ve ne sono parecchi:



	
  1. **MAI aggiornare Gentoo la sera o quando si è stanchi perchè, se chiudete il terminale senza rendervi conto che c'è scritto qualcosa, poi fate questa fine xD**

	
  2. **prima di dare revdep-rebuild controllate di avere installato _lafilefixer_ o dovrete rifare tutto per la terza** volta!

	
  3. ricordarsi che libpng12 serve per chromium-bin (solo se usate il BIN) quindi dovrete reinstallare libpng-1.2.44 in un nuovo slot ;)


