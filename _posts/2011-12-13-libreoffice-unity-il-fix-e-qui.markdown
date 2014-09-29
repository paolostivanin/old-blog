---
author: pol@blog
comments: true
date: 2011-12-13 17:24:51+00:00
layout: post
slug: libreoffice-unity-il-fix-e-qui
title: 'Libreoffice + Unity: il fix è qui!'
wordpress_id: 1742
categories:
- Ubuntu
- Unix
tags:
- libreoffice
- ubuntu
- ubuntu office
- unity
---

Capita anche a voi che Libreoffice (writer, calc, ecc) non compaia in Unity quando è aperto? Si?

Bene _(anzi male xD)_ ma ora grazie a **Marco Trevisan** _(aka 3vi1n0)_ il problema è definitivamente risolto :)

Se anche voi siete affetti da questo bug allora avete 3 possibilità:

<!-- more -->

**1)** Se avete Ubuntu versione amd64 (64bit) allora dovete semplice scaricare [QUESTO]({{ site.baseurl }}/images/2011/12/bamfdaemon.tar1.gz) file e copiarlo in /usr/lib/bamf/

    
    tar xzvf bamfdaemon.tar.gz && killall bamfdaemon && sudo cp bamfdaemon /usr/lib/bamf/


e quindi riavviare Unity con

    
    unity --replace


Se ciò non dovesse bastare riavviate il PC/No(e)tbook :D

**2)** Se non avete Ubuntu amd64 allora dovete compilarvi il demone in questo semplice modo:

    
    sudo apt-get install bzr
    bzr branch lp:~3v1n0/ubuntu/oneiric/bamf/libreoffice-fixes bamf-fixes
    cd bamf-fixes
    sudo apt-get build-dep bamf
    ./autogen.sh --prefix=/usr
    make
    cd src && killall bamfdaemon && sudo cp bamfdaemon /usr/lib/bamf/


**3)** Aspettare qualche giorno _(o settimana?)_ in attesa che il fix venga uppato sui repository di Ubuntu!

Enjoy :)
