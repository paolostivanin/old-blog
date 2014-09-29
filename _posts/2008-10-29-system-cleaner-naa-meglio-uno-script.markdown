---
comments: true
date: 2008-10-29 13:53:38+00:00
layout: post
title: System Cleaner? Naa! Meglio uno script!
categories:
- Ubuntu
- Unix
---

Ciao a tutti!

Una novità sicuramente inutile (ora come ora dico eh, _ndr_) è il System Cleaner


<blockquote>system-cleaner finds and removes cruft from a system. Cruft is
(currently) packages that apt marks as automatically removable, or
that Ubuntu no longer supports.</blockquote>


L'ho provato e devo dire che è ben poco utile e poco efficiente.

Per rimuovere tutto ciò che non è necessario, basta utilizzare questo semplicissimo script realizzato da me:


[**SCRIPT PULIRE UBUNTU**](http://www.fileden.com/files/2008/6/10/1953114/1pulire-ubuntu.sh)



**_Lo scaricate --> doppo click --> esegui nel terminale_**

ed è fatta!

Ecco le screen se qualcuno avesse ancora dubbi:

[![](http://www.allfreeportal.com/imghost/thumbs/789417Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=789417Schermata.png)

[![](http://www.allfreeportal.com/imghost/thumbs/45643Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=45643Schermata-1.png)

_**Per chi si chiede cosa fa questo script, presto detto:**_


<blockquote>#!/bin/sh
#Questo programma effettua la pulizia di un sistema basato su Ubuntu
echo “Inizia ora la pulizia del sistema...”
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg –purge `COLUMNS=300 dpkg -l “*” | egrep “^rc” | cut -d -f3`
sudo rm -fr /tmp/*</blockquote>
