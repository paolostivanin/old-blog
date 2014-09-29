---
author: pol@blog
comments: true
date: 2010-05-28 18:00:05+00:00
layout: post
slug: mantenere-sincronizzate-due-cartelle-con-rsync
title: Mantenere sincronizzate due cartelle con Rsync!
wordpress_id: 892
categories:
- ArchLinux
- Ubuntu
- Unix
---

Avete necessità di mantenere sincronizzate due cartelle, due hard disk, un HD con una USB, etc?

Bene, [Rsync](http://samba.anu.edu.au/rsync/) è quello che fa per voi!

Gli usi di questo potentissimo tool sono molti, io ve ne insegnerò un che mi è tornato utile ultimamente:


`﻿rsync -auv --stats  /PERCORSO-SORGENTE/  /PERCORSO-DESTINAZIONE/`


Con questo comando praticamente avrete i medesimi file in entrambe le cartelle e, se vi sono già file uguali, li salta. Praticamente è un backup incrementale :)

Mi raccomando di **mettere sempre la / alla fine **altrimenti succederà questo:

Se **metto la / alla fine** allora avrò questa situazione:


SORGENTE:
Cartella A 
File1
File2
File3
DESTINAZIONE:
Cartella A 
File1
File2
File3


---------------------------------------------
Altrimenti se **NON metto la / alla fine **avrò quest'altra situazione:


SORGENTE:
Cartella A 
File1
File2
File3
DESTINAZIONE:
Cartella A 
Cartella A 
File1
File2
File3
