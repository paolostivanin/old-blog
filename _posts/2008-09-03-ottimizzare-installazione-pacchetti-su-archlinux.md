---
comments: true
date: 2008-09-03 14:39:26+00:00
layout: blog
title: Ottimizzare installazione pacchetti su Archlinux!
categories:
- ArchLinux
- Unix
---

Ciao gente!

Qualche giorno fa, quando ho parlato di pacbuilder, vi ho detto che si possono usare entrambi i core per compilare.

Bene, questa ottimizzazione la possiamo ottenere anche per **PACMAN!**

Vediamo come fare per ottimizzare al meglio la compilazione di quello che installiamo dai PKGBUILD (prevalentemente AUR)! :D

Allora, prima di tutto diventiamo_ root_:


`su`




`PASSWORD`



poi editiamo il nostro _/etc/makepkg.conf_:


`gedit /etc/makepkg.conf`



e ci troviamo di fronte ad un file pieno di roba scritta.

Bene, cerchiamo questa parte qui:


#########################################################################
# ARCHITECTURE, COMPILE FLAGS
#########################################################################
#
CARCH="i686"
CHOST="i686-pc-linux-gnu"



#-- Exclusive: will only run on -march=i686
# -march (or -mcpu) builds exclusively for an architecture
# -mtune optimizes for an architecture, but builds for whole processor family
CFLAGS=""
CXXFLAGS=""
#-- Make Flags: change this for DistCC/SMP systems
MAKEFLAGS=""

Una volta trovata, dovremo occuparci solo di 3 punti, ovvero:


CFLAGS=""
CXXFLAGS=""
MAKEFLAGS=""

Allora, nel campo _CFLAGS_ dobbiamo mettere quello che più si addice al [nostro processore.](http://wiki.archlinux.org/index.php/Safe_Cflags) **<-- CLICCA LI.**

Nel campo _CXXFLAGS_ scriviamo semplicemente: _${CFLAGS} _ovviamente fra le virgolette!

Infine nel MAKEFLAGS, se abbiamo un dual core scriviamo:


-j3



altrimenti


-j2



Per esempio, io ho un core 2 duo, quindi quei 3 punti per me saranno così:


CFLAGS="-march=prescott -O2 -pipe -fomit-frame-pointer"
CXXFLAGS="${CFLAGS}"
MAKEFLAGS="-j3"

Ecco fatto, con questa semplice guida ottimizzeremo i futuri PKGBUILD che installeremo :D

Semplice no?

**IMPORTANTE: la stessa configurazione si può copiarla all'interno di _/etc/pacbuilder.conf_ (alla fine del file) così da poter compilare per il nostro sistema i pacchetti che installiamo dai repositoy core, extra, community, testing!:**




Dubbi, errori, incomprensioni, richieste d'aiuto, ecc, sono ben accette :D
