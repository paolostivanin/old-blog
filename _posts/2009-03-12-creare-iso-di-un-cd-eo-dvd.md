---
comments: true
date: 2009-03-12 19:59:49+00:00
layout: blog
title: Creare ISO di un CD e/o DVD!
categories:
- ArchLinux
- Ubuntu
- Unix
---

Trick & Trip della serata:

è possibile** creare l’immagine ISO di un CD o un DVD** da utilizzare come ci pare e piace: dal backup di un sistema operativo già presente nel CD, alla creazione di una ISO per virtualbox, ecc ecc ecc!


Su Linux generalmente la prima unità ottica sarà _/dev/sr0_, la seconda _/dev/sr1_ e così via, la creazione dell’immagine è semplicissima!




Apriamo il terminale e digitiamo _(dopo aver - ovviamente - inserito il CD/DVD, LoL_ ;-) _)_:




`sudo dd if=/dev/sr0 of=immagine.iso`



Cosa fa questo comando?

Semplicemente crea una ISO dal nome _immagine _del contenuto del CD/DVD nella directory in cui siamo (generalmente la _Home _se abbiamo appena aperto il terminale)

Enjoy :D
