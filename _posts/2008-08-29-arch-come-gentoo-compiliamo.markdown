---
author: pol@blog
comments: true
date: 2008-08-29 09:08:22+00:00
layout: post
slug: arch-come-gentoo-compiliamo
title: Arch come Gentoo, compiliamo!
wordpress_id: 217
categories:
- ArchLinux
- Unix
---

Ebbene si, per coloro a cui piace compilare ed installare solo SW compilato, ecco a voi la novità di oggi:

**PACBUILDER!**

Cos'è Pacbuilder?

Pacbuilder è un SW sviluppato da [Andrea Cimitan](http://www.cimitan.com/blog/) e continuato da [Bash](http://www.deelab.org/bash/) che permette di compilare da sorgenti i pacchetti di ArchLinux, siano essi di Core, Extra, Community, AUR, Testing.

Questo SW permette di:



	
  * ricompilare l'intero sistema

	
  * compilare solo i pacchetti DEVEL

	
  * compilare e installare nuovi SW

	
  * compilare/ricompilare a scelta i SW dei repo Core-Extra-Community-AUR-Testing

	
  * riprendere una compilazione interrotta grazie al _Resume_


Ecco cosa si può fare (per ora) con PACBUILDER:


A tool to massively recompile packages from sources
It currently fetches both ABS and AUR



USAGE:
pacbuilder [options] package



OPTIONS:
General:
--help                print this help
--clean               remove previous log
--edit                be verbose and edit PKGBUILD
--gccinfo             print current compilation flags
--nocolor             do not use any color
--notitle             do not print the title
--noresume            do not resume
Install:
(-S),    --install      build specified packages
(-S) -b, --builddeps    build and install the dependencies
(-S) -e, --edit         be verbose and edit PKGBUILD
(-S) -f, --force        force install, overwrite conflicting files
(-S) -k, --keepdeps     keep makedepends after install
(-S) -u, --sysupgrade   build the updated packages
(-S) -v, --verbose      print makepkg output
Additional parameters:
-p, --pretend         only print the final list of packages to be installed
-a, --confirm         ask again after printing the list of packages to be installed
-m, --match <regex>   only install packages matching <regex>
-d, --deplist         recursively list all dependencies first
Type:
--world               recompile both deps and explicit
--explicit            recompile explicitely installed packages
--devel               recompile only installated devel packages
Target repository:
--core                recompile packages in core
--extra               recompile packages in extra
--testing             recompile packages in testing
--community           recompile packages in community
--aur                 recompile packages in aur

Usarlo è molto semplice, basta diventare _root_ e successivamente digitare:

`pacbuilder [options] [package]`

Per esempio, se vogliamo ricompilare tutti i SW del repo Core, dobbiamo fare **(ci sono 2 trattini prima di world, core, force)**:

`pacbuilder --world --core --force`

Ricordo che l'opzione _force_ è consigliato metterla SEMPRE, onde evitare pacchetti non ricompilati (com'è successo a me) per delle cavolate!

In questo screen si può notare Pacbuilder che cerca i SW installati dal repo Core:

[![](http://www.allfreeportal.com/imghost/thumbs/626754Schermata11.png)](http://www.allfreeportal.com/imghost/viewer.php?id=626754Schermata11.png)

Pacbuilder inizia a compilare:

[![](http://www.allfreeportal.com/imghost/thumbs/128230Schermata-2.png)](http://www.allfreeportal.com/imghost/viewer.php?id=128230Schermata-2.png)


Per chi ha un dual core, **per sfruttare i 2 core durante la compilazione deve fare così:**



`su`

`PASSWORD`

`nano /etc/pacbuilder.conf`


E andiamo nella parte finale del testo e troviamo questo:



# Use alternative CFLAGS for build package
#CFLAGS=""
#CXXFLAGS=""
#MAKEFLAGS="-j3"


Decommentiamo MAKEFLAGS:



# Use alternative CFLAGS for build package
#CFLAGS=""
#CXXFLAGS=""
MAKEFLAGS="-j3"

E così sfrutteremo i 2 core per compilare e fare molto prima :D

**Aggiornamento:**

r117 è stata rimossa l’opzione --confirm e aggiunta l’opzione --noconfirm

r119 ora è disponibile in italiano
