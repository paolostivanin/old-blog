---
comments: true
date: 2011-02-19 11:36:48+00:00
layout: blog
title: Megaupload su NAS Qnap!
categories:
- NAS Qnap
tags:
- megaupload
- nas
- pyload
- qnap
---

Per chi utilizza i NAS Qnap saprà che l'unico sito hosting ad oggi disponibile tramite download station è Rapidshare.

E se volessimo scaricare da Megaupload, Fileserve, Depositfile, Hotfile, ecc?

Per questo ci viene in aiuto [PyLoad](http://pyload.org/), un download manager gratuito scritto in Python.

Riporto dal sito le caratteristiche salienti:



	
  * Scritto in Python

	
  * Bassi requisti hardware

	
  * Supporta molto siti di hosting one-click

	
  * Comprende supporto ad account premium, riconoscimento captcha, riconnessione

	
  * Supporto a DLC, CCF, RSDF

	
  * Accesso remoto via interfaccia web

	
  * Supporto gratuito su irc o forum

	
  * licenza GPL


Prerequisti per procedere all'installazione:

	
  * installare il plugin Optware

	
  * avere abilitato l'accesso SSH al NAS


Fatte le premesse veniamo subito al sodo e vediamo come installare questo comodo software :)
<!-- more -->

Per prima cosa dobbiamo accedere via SSH al nostro NAS:

`ssh -l $USER $IP-NAS`

Poi dobbiamo installare tutte le dipendenze necessarie in questo modo:

`ipkg install screen
ipkg install nano
ipkg install wget
ipkg install unzip
ipkg install python
ipkg install py25-crypto
ipkg install py25-curl
ipkg install libcurl
ipkg install py25-openssl
ipkg install py25-django
ipkg install py25-pil
ipkg install tesseract-ocr
ipkg install tesseract-ocr-lang-eng
ipkg install ossp-js
`
Successivamente passiamo allo scaricamento e all'installazione di Pyload:

`cd /opt
wget https://bitbucket.org/spoob/pyload/get/tip.zip --no-check-certificate
unzip-unzip tip.zip`
--------------------------------------------------------------
_**`Se e solo se usate la versione tip.zip dovete dare questo comando aggiuntivo:`**_
`mv spoob-pyload* pyload`
--------------------------------------------------------------
`rm tip.zip
cd pyload/
cd module/config/
echo "/usr/share/pyload" >> configdir
chmod +x /opt/pyload/pyLoadCore.py`


Fatto ciò dobbiamo passare alla configurazione vera e proprio tramite questo comando:


`python /opt/pyload/pyLoadCore.py -s`

Terminata la procedura se avete fatto tutto correttamente andate all'indirizzo _$IP-NAS:8000_ e dovreste vedere l'interfaccia web di PyLoad :)


Ricordo che PyLoad deve essere attivato ad **ogni **avvio del NAS (nel caso voi lo accendiate e lo spegniate).




Un consiglio per evitare di tenere aperta la shell SSH è di dare questo comando:


`screen -dmS python /opt/pyload/pyLoadCore.py`


così potete tranquillamente sloggarvi da SSH ma PyLoad continuerà a funzionare ;)




Nota: la versione di PyLoad che vi consiglio di scaricare con questo post è la "tip" ovvero quella presa dal ramo in sviluppo. La consiglio in quanto l'autore fixa bugs in tempo reale e ciò è molto comodo. (Per esempio dopo che io ho riportato un bug relativo a megaupload lui in 10 ore l'ha corretto)






[gallery]


