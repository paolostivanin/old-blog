---
author: pol@blog
comments: true
date: 2010-10-05 17:38:39+00:00
layout: post
slug: da-ext2-a-ext3-senza-formattare
title: Da ext2 a ext3 senza formattare!
wordpress_id: 976
categories:
- Debian &amp; Co
- Ubuntu
- Unix
tags:
- ext2
- ext3
- formattare
---

Circa 5 anni fa ho comprato un hard disk esterno da 250Gb che uso principalmente per **archiviazione** e **basta** (quindi quasi sempre spento).

Ieri, dopo tutto questo tempo, ho deciso di analizzare il disco_ (controllo errori + defrag)_ per vedere _come stava _dato che da qualche mese a questa parte era diventato piuttosto lento.

Risultato?

**Frammentazione al 67%**

In questi casi c'è poco da fare così ho optato per una soluzione drastica, divisa in 2 punti:



	
  * repulist dei files che non uso più

	
  * `mkfs.ext2 /dev/sdb`


Dopo aver fatto ciò ho risalvato i dati e tutto è tornato - ovviamente - al posto giusto...ma...

...Ma non ero completamente soddisfatto di aver formattato in ext2 (si, ci ho pensato dopo xD) così ho deciso di _"convertirlo"_ in ext3 (aggiungendoci quindi il **_journaling_) in modo da stare più tranquillo :)**

**Per fare questa conversione ext2 --> ext3** i passaggi sono pochi e semplici:



	
  1. Smontiamo il drive in questione con: `sudo umount /dev/sdXY` dove _X_ è una lettera (a,b,c,d,ecc) e _Y_ un numero (1,2,3,ecc)

	
  2. Aggiungiamo il journaling al file system con: `sudo tune2fs -j /dev/sdXY`

	
  3. Controlliamo che sia tutto ok con: `sudo fsck.ext3 /dev/sdXY`


Ora abbiamo 2 possibilità:

	
  1. Se il file system convertito è in un HD esterno o una pen drive o un drive qualsiasi che **non è sempre attaccatto al pc allora siamo a posto, la guida finisce qui :)**

	
  2. **Se il file system convertito fa parte in modo perenne del pc allora dobbiamo dire a fstab che questo FS è diventato ext3: `sudo nano -w /etc/fstab` e cerchiamo il drive in questione cambiando ext2 in ext3.**


_**Opzionale:** se vogliamo cambiare il "numero di mount ogniqualvolta deve controllare il disco" basta dare: _`sudo sudo tune2fs -c $NM /dev/sdXY` dove $NM è il numero di mount (10,20,30,ecc)
