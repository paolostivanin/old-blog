---
comments: true
date: 2009-01-08 09:30:03+00:00
layout: blog
title: Driver intel per Archlinux!
categories:
- ArchLinux
- Unix
---

Mentre commentavo il mio precedente post, mi sono accorto di una cosa _muy _triste ( :( )!

**Arch** ha i driver intel alla versione **2.4.3** mentre i driver intel attuali sono alla versione **2.6.0**!

Non mi sono certo perso d'animo e ho guardato su _AUR_ cosa c'era disponibile...e in effetti i driver c'erano!
Ma...ma...ma il PKGBUILD era fatto in modo non corretto e mancavano delle parti, sicchè l'ho scaricato, l'ho corretto e l'ho ri-uppato!
Ergo, per chi avesse una scheda video intel che usa i driver _xf86-video-intel _se vuole aggiornarli basta che dia questo comando:


`yaourt -S libdrm-newest`
`
yaourt -S xf86-video-intel-newest`

Ed ecco i nostri bei driver aggiornati installati :D


[![](http://www.allfreeportal.com/imghost/thumbs/350193Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=350193Schermata.png)



Enjoy :D

__
