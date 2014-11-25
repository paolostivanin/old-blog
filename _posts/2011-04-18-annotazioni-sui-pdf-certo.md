---
comments: true
date: 2011-04-18 18:11:39+00:00
layout: blog
title: Annotazioni sui PDF? Certo!
categories:
- Debian &amp; Co
- Ubuntu
- Unix
---

Di default **Ubuntu** **10.10 **usa **poppler ****0.14.3** che **non** ha il supporto alla scrittura delle annotazioni sui files pdf.

Per risolvere tale inconveniente ci viene in aiuto il [mio ppa](http://www.polslinux.it/polslinux-repository) **(****solo per Ubuntu 10.10****)**

_Per Lucid **non** mi è possibile creare i suddetti pacchetti perchè richiederebbe un aggiornamento massiccio di molte componenti quali libcairo2, svariate parte di x11, ecc!_

Dopo aver aggiunto il _ppa polmaver_ alla vostra lista sorgenti date in questo ordine:


`sudo apt-get update`




`sudo apt-get dist-upgrade`


Ora per provare questa nuova funzione aprite un pdf e dalla colonna di destra al posto di _thumbnails_ selezionate _annotations_, poi cliccate su _add_ e scegliete dove posizionarla :)

Enjoy! :D

[gallery]
