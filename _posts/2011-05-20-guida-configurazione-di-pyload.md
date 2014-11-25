---
comments: true
date: 2011-05-20 12:04:09+00:00
layout: blog
title: Guida configurazione di PyLoad!
categories:
- Debian &amp; Co
- Ubuntu
- Unix
---

[caption id="attachment_1467" align="aligncenter" width="412" caption="Pyload Logo!"][![]({{ site.baseurl }}/images/2011/05/pyload_logo1.png)]({{ site.baseurl }}/images/2011/05/pyload_logo1.png)[/caption]

Per chi avesse riscontrato problemi o difficoltà nell'installare PyLoad ho deciso di scrivere un breve (e spero chiara) guida sul come configurarlo!



	
  1. Scaricare [PyLoad](http://get.pyload.org/get/build/ubuntu/pyload-v0.4.5-noarch.deb/)

	
  2. Installarlo tramite `sudo dpkg -i pyload-v0.4.5-noarch.deb`

	
  3. Risolvere eventuali problemi con `sudo apt-get install -f`

	
  4. Forwardare sul proprio router la _**porta 8000**_ (se intendete controllare PyLoad da remoto, altrimenti non è necessario)

	
  5. Andare su _Applicazioni --> Internet --> PyLoad Download Manager_

	
  6. Si aprirà il terminale, ora inizia la configurazione vera e propria.


Configurazione PyLoad:

	
  1. _Choose your Language:_**it** (e premi invio)

	
  2. Premi di nuovo Invio

	
  3. Premi di nuovo Invio

	
  4. _Continua con il setup? _**y**

	
  5. _Cambiare il percorso della configurazione? _**n
**

	
  6. _Fai la configurazione di base? _**y
**

	
  7. _Nome utente [user]:_ scrivi un nome per l'utente che avrà accesso a PyLoad

	
  8. _Password:_ inserisci la password per l'utente sopra scelto

	
  9. _Lingua ([en], de, it, pl, es, cs, fr): _**it**

	
  10. _Cartella di download [Downloads]:_ premete invio**
**

	
  11. Su _Max Download,__Usa Riconnessione _e _Configura SSL_ premete semplicemente invio

	
  12. _Configurare l'interfaccia web? _**y**

	
  13. _Attivare l'interfaccia web? ([y]/n):_** y
**

	
  14. _Indirizzo [0.0.0.0]:_ se intendiamo usarlo **solo in locale** allora scriviamo **127.0.0.1** se invece pensiamo di **usarlo anche da remoto** scriviamo l'indirizzo ip lan del nostro pc (esempio **192.xxx.yyy.zzz**)

	
  15. _Porta [8000]:_ premete invio

	
  16. Premete Invio altre 2 volte a avete finito :)


Ora per avviare PyLoad andiamo su _Applicazioni --> Internet --> PyLoad Download Manager_ e si aprirà il terminale!

Da notare che ogni volta che PyLoad viene avviato esso controllerà se sono disponibili aggiornamenti per i plugin e, nel caso fossero disponibili aggiormenti, PyLoad farà tutto automaticamente.

Se alla fine compare questa scritta:

_*** Plugins have been updated, please restart pyLoad ***_

Allora dovete chiudere il terminale e avviare di nuovo PyLoad :)

Adesso aprite il vostro browser e digitate:


**127.0.0.1:8000** _se avete configurato PyLoad solo in locale_


oppure


**192.xxx.yyy.zzz:8000** _se avete configurato PyLoad per essere controllato anche da remoto!_


Enjoy :)
