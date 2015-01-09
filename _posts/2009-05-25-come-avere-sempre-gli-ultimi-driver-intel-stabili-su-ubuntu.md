---
comments: true
date: 2009-05-25 18:46:29+00:00
layout: post
title: Come avere SEMPRE gli ultimi driver Intel stabili su Ubuntu!
categories:
- Ubuntu
- Unix
---

Con questo piccolo how-to voglio dirvi come avere _**SEMPRE**_ i driver Intel aggiornati all'ultima versione **stabile****!**

Innazitutto apriamo con Gedit il file sources.list:


`sudo gedit /etc/apt/sources.list`



poi copiamo in fondo al file il repository x-swat:


`# Xorg update`




`deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main`



aggiungiamo quindi la chiave GPG copiandola su un nuovo file di testo e aggiungendola da "Sorgenti Software"


[Chiave GPG](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9)



Aggiorniamo il nostro sistema:


`sudo apt-get update && sudo apt-get dist-upgrade`



Et voilà, avremo sempre gli ultimi driver intel (e relativi annessi e connessi) sempre all'ultima versione **stabile!**

** **
