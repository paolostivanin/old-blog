---
comments: true
date: 2012-05-26 10:54:20+00:00
layout: blog
title: KeePassX 2.0 alpha1
categories:
- ArchLinux
- Debian &amp; Co
- Ubuntu
- Unix
tags:
- archlinux
- debian
- keepassx
- linux
- password-manager
- ubuntu
---

Dopo diverso tempo _(2 anni)_ che [KeePassX](http://www.keepassx.org) non veniva più aggiornato finalmente i dev hanno "preso l'iniziativa" e hanno quindi deciso di [sviluppare una nuova versione](https://gitorious.org/keepassx) (2.0, attualmente in _alpha1_) che sia compatibile con i database di KeePass (.kdbx, _ndr_) e che abbia una nuova veste grafica.

I risultati sono già visibili e, devo dire, sono anche molto interessanti.

[gallery]

Avendo già effettuato delle prove posso dire che i database _.kdbx_ sono importati perfettamente, partendo dai gruppi fino alle varie informazioni (user, pwd, note, ecc).

La stabilità è eccezionale nonostante sia solo la prima versione alpha.

Il mio consiglio quindi è di **backuppare il vostro attuale DB** **prima di usare la versione alpha di KeePassX** e successivamente fare delle prove su il database originale prima di decidere di usarlo in maniera stabile (cosa che **sconsiglio** almeno fino al rilascio della prima beta)

Se volete provare KeePassX ho preparato uno scriptino che si occuperà di fare quasi tutto. Dico quasi perchè non effettua il controllo delle dipendenze che dovrete installare voi manualmente_ (su Debian & Co. sono git-core, cmake, qt4-qmake, libqt4-dev, libgcrypt11-dev, zlib1g-dev)_

    
    #!/bin/bash
    
    CUR=$PWD
    
    echo "--> Downloading source..."
    git clone git://gitorious.org/keepassx/keepassx.git
    echo "--> Done, running make..."
    cd ${PWD}/keepassx
    mkdir ${PWD}/build
    cd ${PWD}/build
    cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local -DCMAKE_VERBOSE_MAKEFILE=ON -DWITH_GUI_TESTS=ON -DCMAKE_BUILD_TYPE=Release
    make -j2
    if [ $? == 0 ];then
    	sudo make install
    	echo "--> All done"
    	cd $CUR
    	rm -rf keepassx
    	exit 0
    fi
    echo "--> Something went wrong..."
    cd $CUR
    rm -rf keepassx
    exit 1


Se è la prima volta che installate KeepassX dovete scaricare [QUESTO]({{ site.baseurl }}/images/2012/05/kee-file-desktop1.tar) file, estrarlo (`tar xf kee-file-desktop.tar`) e dare il comando:

    
    sudo cp path-al-file-keepassx.desktop /usr/share/applications/keepassx.desktop


per poter avere l'icona di KeepassX nel menù delle applicazioni installate.

Enjoy :D 
