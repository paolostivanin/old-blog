---
comments: true
date: 2011-08-26 11:45:44+00:00
layout: post
title: Archlinux e hostname command not found, la soluzione!
---

Per chi come me ha il repository testing abilitato avrà notato che il comando `hostname` è automagicamente sparito_ (errore nell'esecuzione di startx alla linea 127)_!

Tempo fa la_ "colpa"_ era da attribuirsi alla deprecazione di _net-tools_ in favore di _coreutils_ ma, installando manualmente _net-tools_, il problema si "raggirava" perchè net-tools forniva ancora il suddetto comando.

Qualche giorno fa però nel repository testing c'è stato un aggiornamento a net-tools che ha reso effettiva l'inutilità di quest'ultimo a causa della rimozione del comando `hostname`.

Chiedendo info sul forum internazionale ho scoperto che il comando in questione ora è fornito da questo pacchetto: **inetutils**.

Perciò con:


`pacman -R net-tools`




`pacman -S inetutils`


risolveremo finalmente ogni problema :)

Enjoy!
