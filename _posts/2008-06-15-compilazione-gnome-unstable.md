---
comments: true
date: 2008-06-15 16:16:18+00:00
layout: post
title: Compilazione Gnome Unstable
categories:
- Ubuntu
---

Beh, vi avevo detto che avrei scritto una guida su come compilare Gnome unstable...ma ho avuto dei problemi!

Dopo **8**** ore** (mi sono dimenticato di usare il comando per compilare con 2 core invece che con 1) di compilazione, prendo lo script di installazione della sezione di Garnome e...**NON VA!**

Ah beh, ne sono volete giù di tutti i colori...ho cercato di fare qualcosa a mano ma ho ottenuto come risultato il fatto di dover formattare tutto XD

Però, se qualcuno è più agile di me con gli script, mi faccia sapere!

Intanto vi dico come compilare Gnome senza errori (e già questa è una grande cosa ;-) )

Intanto scarichiamo l'ultima versione di Garnome da qui:

[http://ftp.gnome.org/pub/GNOME/sources/garnome/2.23/](http://ftp.gnome.org/pub/GNOME/sources/garnome/2.23/)

Una volta scaricato estraiamo tutto e procediamo ad installare le dipendenze che sono queste:

[http://www.fileden.com/files/2008/6/10/1953114/DEPS-LIST.txt](http://www.fileden.com/files/2008/6/10/1953114/DEPS-LIST.txt)

_**N.B.: INSTALLATE LE DIPENDENZE UNA A UNA DA SYNAPTIC PERCHÈ POTREBBERO ESSERE VECCHIE QUELLE SCRITTE LI.**_

Fatto ciò, apriamo il terminale e entriamo nella cartella di Garnome; una volta dentro la cartella diamo il comando:

`make deep-install`

Se abbiamo un dual-core PRIMA di dare quel comando diamo questo comando:

`export CONCURRENCY_LEVEL=2`

così sfrutteremo tutti e due i core per compilare e faremo _**MOOOLTO **_prima!

Bene, aspettiamo e una volta fatto tutto entrate nella cartella di Garnome e cercate di capire come usare lo script, se ci riuscite, fate un fischio :-)
