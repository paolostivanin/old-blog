---
comments: true
date: 2008-07-15 10:17:25+00:00
layout: blog
title: '[How-to] Installare Network-Manager 0.7!'
categories:
- Ubuntu
---

Hola raga!

Nell'attesa che arrivi giovedì che ho un po' di tempo libero così posso provare e recensire Debian Testing (un utente del blog me lo ha chiesto e son ben felice di accontentare la sua richiesta), oggi mi dedico al software "unstable".

Oddio, unstable è a dirla grossa, Fedora 9 lo ha di predefinito e sembra funzionare bene quindi, perchè non provarlo?

------------------------------------------------------------

**Disclaimer:**

Ogni possibile causa di distruzione, annientamento del computer, sistema operativo o qualsiasi altra cosa non sarà ritorcibile su di me.

Chiunque segua questa guida si dichiara consapevole delle conseguenze.

------------------------------------------------------------

Non prendete paura, è solo per evitare casini inutili che qualche persona potrebbe crearmi ^_^

Ma veniamo a noi!



	
  * Editiamo il nostro sources.list in questo modo:


`sudo gedit /etc/apt/sources.list`



	
  * Incolliamo queste righe a fine documento


`deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main`



	
  * Salviamo e aggiorniamo:


`sudo apt-get update && sudo apt-get dist-upgrade`



	
  * **Se non dovesse esserci, aggiungiamo l'applet:**


`Alt+F2` e poi scriviamo `nm-applet`

Perfetto, ora avremo il nostro network-manager 0.7 installato!

Ricordo che è un software UD (under-development) quindi ocio raga! :D
