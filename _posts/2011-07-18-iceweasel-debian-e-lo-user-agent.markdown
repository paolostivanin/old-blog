---
comments: true
date: 2011-07-18 07:30:43+00:00
layout: post
title: Iceweasel, Debian e lo user agent!
categories:
- Debian &amp; Co
- Ubuntu
- Unix
tags:
- debian
- iceweasel
---

L'altro giorno ho stampato i biglietti della Ryanair dopo aver fatto il check-in online e mi sono accorto che tali biglietti non stavano in 1 pagina ma bensì in 2 (veniva troncata la parte finale).

Un po' dubbioso mi sono informato e ho visto che sulle F.A.Q. della Ryanair c'è esplicitamente scritto che **"i biglietti devono essere stampati uno per pagina in un foglio A4"**

Bene mi son detto...e ora che faccio? Provo con Google Chrome ma niente, stesso risultato!

Comincio quindi a pensare che sia un problema di Ryanair ma faccio un ultimo tentativo e accendo la VM con Windows...e magia funziona O_o

Allora c'è qualcosa che non va su Debian...provo da Arch con **FIREFOX** e...funziona!

Mi metto quindi a cercare qualche informazione in merito alle pagine _.aspx_ (quelle della Ryanair) e vedo su un forum che posso esservi dei problemi se il sito è fatto da schifo perchè la pagina negozia col server uno user-agent non conosciuto scazzando di fatto il tutto -.-''

Ottimo, il problema se pur fastidioso è di semplice risoluzione: cambiamo user-agent di quell'inutilità di Iceweasel!

C'è un ottima estensione che lo fa ma non resta attivo quando spegniamo quella _"bellezza di browser"_. Facciamo da _about:config_ allora ma per qualche strana ragione al riavvio di Iceweasel le configurazioni vengono perse O.o

Allora come extrema ratio non mi resta che spulciarmi i file _.js_ di Iceweasel alla ricerca dello user-agent e modificarlo da li.

Se anche voi avete questo problema dello user-agent potete facilmente risolvere in questo modo:

Modificate con un qualsiasi editor di testo questo file:


`gksu gedit /usr/lib/iceweasel/defaults/syspref/iceweasel.js`


e all'interno scriveteci (tutto su una riga eh!):


`// Override the default user-agent string:
pref("general.useragent.override", "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2) Gecko/20110323 Firefox/5.0");`


Fatto, problema risolto :)

Certo questo problema potrebbe tranquillamente **non esserci se quelli di Debian la finissero con questa cazzata di usare Iceweasel** ma si sa, il bello di GNU/Linux è che puoi fare quello che vuoi e come vuoi ;)
