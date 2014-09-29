---
author: pol@blog
comments: true
date: 2009-09-11 14:08:26+00:00
layout: post
slug: da-jaunty-a-karmic-veloce-e-indolore
title: Da Jaunty a Karmic, veloce e indolore!
wordpress_id: 762
categories:
- Ubuntu
- Unix
---

In questi giorni - avendo visto sul mio notebook che Karmic si sta stabilizzando - ho deciso che era ora anche per il fisso di fare un bel +1 (da 9.04 a 9.10, _ndr_)

Per fare questo aggiornamento abbiamo 3 diverse strade:

1) quella utile per tutta la vita

2) quella utile solo adesso

3) quella per quelli che non hanno niente da fare

Procediamo con la spiegazione delle 3 strade:

1) Questa prima strada (da me intrapresa), si rivela molto comoda da qui all'eternità perchè una volta creato questo lanciatore basterà premerlo e - senza dover cambiare niente a mano - avremo sempre l'ultima _**unstable release **_di Ubuntu! Per fare ciò cliccalte col destro sul menù di gnome, abilitate _Strumenti di sistema_ e cliccate su _Nuova voce_._ _Questo campo sarà così impostato:


**Tipo:** Applicazione




**Nome:** Ubuntu+1




**Comando: **update-manager -d




**Commento:** Per aggiornare ogni release di Ubuntu all'ultima disponibile (unstable)




**Icona:** /usr/share/icons/Human/scalable/apps/update-manager.svg


2) Questa strada è un po' più lenta perchè bisogna dare questo comando per ogni release di Ubuntu cambiando, ovviamente, i nomi dentro le parentesi graffe. Se scegliete questa strada dovrete cambiare manualmente il file _sources.list _e aggiornare l'intero sistema con questi comandi:


`sudo sed -i {s/jaunty/karmic/g} /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade`


3) Questa è la strada preferita per chi non sa come passare i pomeriggi, causa fratture, malattie, noia, ecc ecc. Il tutto è molto semplice, basta fare così:


Editare il file _sources.list_:




`sudo gedit /etc/apt/sources.list`




cambiare **a mano** ogni singolo jaunty in karmic; fatto ciò aggiornate gli indici con:




`sudo apt-get update`




ora aprite Synaptic e aggiornate i pacchetti 1 a 1 :D


Ora che vi ho indicato le possibili vie di aggiornamento, passiamo alla mia esperienza **_aggiornamentativa_** LoL :D

Premesso che ho usato **la strada 1**, io avevo una **Ubuntu Jaunty 32bit **con svariati **PPA** (driver Nvidia, Virtualbox, ecc) i quali sono stati **TUTTI **disabilitati durante l'aggiornamento.

Una volta cliccato sull'icona della _**strada 1**, _comparirà la finestra che vi chiederà di passare a Ubuntu 9.10, voi cliccate e compare un'altra finestra che vi accompagnerà per tutto il viaggio verso lidi più aggiornati xD


**L'inzio...**




[![](http://imgur.com/3RalDl.jpg)](http://imgur.com/3RalDl.jpg)


[](http://imgur.com/3RalDl.jpg)

[](http://imgur.com/3RalDl.jpg)

[](http://imgur.com/3RalDl.jpg)

[](http://imgur.com/3RalDl.jpg)

[





**Riepilogo di quello che succederà al nostro amato sistema prima dell'oblio...**



](http://imgur.com/3RalDl.jpg)


[![](http://imgur.com/YCgEEl.jpg)](http://imgur.com/YCgEEl.jpg)







**Si parteeee...**




[![](http://www.allfreeportal.com/imghost/thumbs/334468karmic+3.jpg)](http://www.allfreeportal.com/imghost/viewer.php?id=334468karmic+3.jpg)




**Kernel e moduli installati alla perfezione :)**




[![](http://www.allfreeportal.com/imghost/thumbs/442184karmic+4.jpg)](http://www.allfreeportal.com/imghost/viewer.php?id=442184karmic+4.jpg)







**E dopo un bel riavvio.....................OOOOOOOOOOOOOOOOOOOHHHH.... (suspence...)**




[![](http://www.allfreeportal.com/imghost/thumbs/386540karmic+5.jpg)](http://www.allfreeportal.com/imghost/viewer.php?id=386540karmic+5.jpg)


Ed ecco qui, conclusa la nostra avventura :D

Tutto è filato liscio, nessun intoppo ;)

Rispetto ad una nuova installazione avremo queste differenze:



	
  * avremo installati sia pidgin sia empathy

	
  * avremo grub-0.97 e **NON** grub2

	
  * possibili doppioni nelle stampanti causa cups aggiornato (1.3.11 --> 1.4.0) e quindi impossibilità di stampare. Per ovviare a ciò basta rimuovere la vecchia stampante **PRIMA di accendere la stampante
**

	
  * avremo sia F-spot che Solang installati


E basta, mi pare sia tutto :D

Che dire, Karmic sarà un release fantastica a partire dall'ottimo kernel che essa include, fino alle migliore di Gnome e di Intel ;-)

Consiglio di aspettare ad aggiornare almeno fino alla **beta-release** del 01/10/2009, così per essere sicuri di non incorrere in intoppi :D

Alla prossima gente, statemi bene :D
