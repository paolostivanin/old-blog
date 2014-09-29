---
comments: true
date: 2010-12-11 13:33:05+00:00
layout: post
title: Dropbox non parte? Ritardiamolo!
categories:
- ArchLinux
- Unix
tags:
- archlinux
- dropbox
- script
---

Ho installato [Dropbox-experimental](https://aur.archlinux.org/packages.php?ID=29432) ma presenta un problemino: se Wicd non fa presto a connettersi Dropbox _"muore" _e non riparte più.

Conosco e vi propongo 2 metodi per ovviare a ciò.
<!-- more -->

In entrambi i metodi bisogna killare dropbox perchè ogni volta che esso parte crea la voce in _Applicazioni d'avvio_ quindi se non viene killato il processo entrambi gli script non funzionano!

1. Aggiungere uno script (esempio nella Home):


nano -w ~/.dropstart




#!/bin/bash




`killall dropbox`




`sleep 40`




`/opt/dropbox/dropboxd`


e renderlo eseguibile con:


`chmod +x ~/.dropstart`


Per concludere andare di nuovo in:


Sistema --> Preferenze --> Applicazioni d'Avvio


E aggiungere una voce d'avvio con questi parametri:


**Nome:** _$quello-che-volete_




**Comando:** sh /home/$USER/.dropstart




**Commento:** _$quello-che-volete_


******************************************************************************

2. **Spuntiamo** come nel punto 1 la voce Dropbox nelle Applicazioni d'Avvio;

Poi modifichiamo lo script _rc.local_ in questo modo:


`nano -w /etc/rc.local`




`killall dropbox`




`sleep 40 && /opt/dropbox/dropboxd`


Ecco fatto! Ora a voi tocca la _l'ardua_ scelta del metodo da usare :)

[caption id="attachment_1038" align="aligncenter" width="300" caption="Userai il metodo 1 o 2?"][![]({{ site.baseurl }}/images/2010/12/pillola_rossa-blu1-300x155.jpg)]({{ site.baseurl }}/images/2010/12/pillola_rossa-blu1.jpg)[/caption]
