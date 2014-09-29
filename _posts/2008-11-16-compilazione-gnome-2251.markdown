---
author: pol@blog
comments: true
date: 2008-11-16 13:15:51+00:00
layout: post
slug: compilazione-gnome-2251
title: Compilazione Gnome 2.25.1
wordpress_id: 403
categories:
- ArchLinux
- Ubuntu
- Unix
---

Con questa breve guida, compileremo (si spera :P ) **Gnome 2.25.1** con** JHBUILD**!

Innanzitutto installiamo **jhbuild:**


`sudo apt-get install jhbuild / yaourt -S jhbuild-svn`



Ora scarichiamo il file _jhbuildrc_ aprendo il terminale e scrivendo:


`wget http://ftp.gnome.org/pub/GNOME/teams/releng/2.25.1/sample-tarball.jhbuildrc`



Rinonimiamo il file da **sample-tarball.jhbuildrc** in **.jhbuildrc**

Benissimo, ora controlliamo che tutto sia a posto con:


`jhbuild sanitycheck`



Se tutto è a posto installiamo i prerequisiti con:


`jhbuild bootstrap`



Ricontrolliamo che tutto sia a posto con:


`jhbuild sanitycheck`



E ora inzia il divertimento, inziamo a compilare tutto:


`jhbuild build`



Ecco fatto, ora non ci resta che aspettare :D

Io proverò stasera con calma perchè oggi pomeriggio sono di studio, se qualcuno prova prima di me, mi faccia sapere com'è l'esito finale :D
