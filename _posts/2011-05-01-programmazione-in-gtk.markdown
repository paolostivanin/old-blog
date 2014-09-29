---
comments: true
date: 2011-05-01 10:21:06+00:00
layout: post
title: Programmazione in GTK+!
categories:
- Unix
tags:
- bash
- glade
- gtk+
- programmazione
---

In questi giorni mi sto dedicando allo scripting in BASH e per dotare i miei script di interfaccia uso Zenity, una comoda (comodissima) alternativa alla creazione di una GUI da zero tramite [GTK+](http://www.gtk.org/)!

Ma l'altro giorno mi son detto: _"ma dai vuoi che sia così difficile creare un'interfaccia in GTK+? Studiamo un po' questo linguaggio va..."_

Detto fatto, ho letto qualche tutorial e ho cominciato a sviluppare la mia prima interfaccia :)

Certo niente di che, una semplice finestra con una menubar e menù a discesa ma il codice da scrivere in GTK+ non è esattamente corto...volete vedere? Eccolo...

<!-- more -->

[caption id="attachment_1306" align="aligncenter" width="244" caption="Finestra con menubar, il codice!"][![]({{ site.baseurl }}/images/2011/05/screenshot32-244x300.png)]({{ site.baseurl }}/images/2011/05/screenshot32.png)[/caption]

E il risultato...

[caption id="attachment_1313" align="aligncenter" width="295" caption="Finestra con menubar, il risultato!"][![]({{ site.baseurl }}/images/2011/05/screenshot13.png)]({{ site.baseurl }}/images/2011/05/screenshot13.png)[/caption]

Come potete vedere bastano "solo" 46 righe di codice per creare la sopracitata finestra! :?

Anche se a prima vista può sembrare chissà cosa, devo dire che il linguaggio GTK+ in sè non è "complicato" da capire e da scrivere, è soltanto **estremamente lungo e noioso**!

Ma esiste un'alternativa nel caso non volessimo scrivere a mano tutta sta roba??

Eh si, hanno pensato a tutto gli sviluppatori di Gnome :)

Ecco quindi che ci viene in aiuto [GLADE](http://glade.gnome.org/), un disegnatore di interfaccia che personalmente non trovo proprio comodo 8O

[caption id="attachment_1316" align="aligncenter" width="300" caption="Glade, il disegnatore di interfaccia"][![]({{ site.baseurl }}/images/2011/05/screenshot51-300x227.png)]({{ site.baseurl }}/images/2011/05/screenshot51.png)[/caption]

Preferisco decisamente di più impararmi il codice e scrivere un po' invece che star lì a capire cosa vuol dire ogni icona, dove sono le varie opzioni, come si sistemano le varie cose, ecc ecc. (Comunque sia, _"De gustibus non disputandum est"_) :D

Ma alla fine cosa ho concluso? Ho concluso che per ora non ritengo prioritario imparare a programmare in GTK+, le mie priorità al momento sono BASH, C e Python!

Resta comunque un capitolo aperto e su cui di certo ritornerò [a maggior ragione dopo che avrò imparato il Python (vedi [PyGTK](http://www.pygtk.org/))] :)

Enjoy!
