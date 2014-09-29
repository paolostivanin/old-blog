---
author: pol@blog
comments: true
date: 2010-09-08 08:53:55+00:00
layout: post
slug: backup-files-con-tar
title: Backup files con tar!
wordpress_id: 927
categories:
- ArchLinux
- Gentoo
- Ubuntu
- Unix
---

Avete dei file importanti da backuppare tipo file di configurazione, documenti, foto, ecc??

Bene, senza ricorre a softwares vari ed eventuali vi scrivo un piccolo trucco per salvare i vostri files:

Anzitutto creiamo un file, per esempio, in /home/$user/$nomebackup.conf


`touch /home/$user/$nomeback.conf`


Poi scriviamo dentro questo file i files che vogliamo salvare, per esempio:


`ls /etc/rc.conf >> /etc/$nomebackup.conf`




`ls /home/$user/foto.jpg >> /etc/$nomebackup.conf`




`ls /etc/ddclient.conf >> /etc/$nomebackup.conf`


Finito di scrivere i nostri files è arrivato il momento di fare il backup vero e proprio**:**


`tar -cjvpf backup-`date +%d-%m-%Y`.tar.bz2 -T /etc/backup.conf
`


(**N.B.: p****rima di _date_ NON c'è una virgoletta normale come questa ' ma c'è un accento grave `)**:

Con quel comando ho detto a tar di:

**c**: crea un nuovo archivio

**j**: crealo in bz2

**f**: files

**v**: verbose, ovvero fammi vedere quello che fai

**p**: conserva i permessi dei files

**T**: leggi files da backuppare da file di input

inoltre usando la dicitura _backup-_`_date +%d-%m-%Y` _all'archivio di nome _backup_ sarà aggiunta la data di oggi in formato giono-mese-anno.

Per **ripristinare** il backup dobbiamo invece dare questo comando:


`tar -xvpjf $nome-$data.tar.bz2 -C /$percorso-estrazione`


dove il comando _x_ estrae i file nell'archivio, il comando _-C _serve per spostarsi nella directory in cui ci interessa sia estratto l'archivio e gli altri comandi sono riportati li sopra :)
