---
comments: true
date: 2008-08-11 14:15:17+00:00
layout: blog
title: Brasero 0.8.1 su Arch Linux
categories:
- Unix
---

Ho letto della notizia dell'uscita di Brasero 0.8.1 e, avendo visto che non si era ancora aggiornata la mia Arch, ho deciso di installarmelo a mano!

Da AUR non è ancora presente e, il mantainer, deve ancora aggiornarlo, quindi, mano al mio pkgbuild :D



	
  * Innazitutto scarichiamo il mio archivio contenenti i file che ci servono e il pkgbuild aggiornato:


[DOWNLOAD TARBALL BRASERO-0.8.1](http://www.megaupload.com/it/?d=RVKMRTS2)



	
  * Estraiamo ed entriamo nella cartella e iniziamo la compilazione:


`cd PERCORSO-FILE-SCARICATO`

`tar xjvf Brasero.tar.gz`

`cd Brasero`

`makepkg`



	
  * Una volta fatto ciò, dopo che tutto è andato a buon fine, è arrivato il momento di sostituire i file vecchi con i nuovi in questo modo:


`su
PASSWORD`

`cd PERCORSO-CARTELLA
cd NOME-CARTELLA
cd pkg
cd usr
cd bin
cp * /usr/bin
cd ..
cd lib
cp -r * /usr/lib
cd ..
cd share
cp -r * /usr/share`



	
  * Il comando _cp -r_ serve per copiare tutta la directory, compresi file e sottodirectorty. Ecco fatto, ora abbiamo la nostra versione di Brasero pronta e funzionante!


**Consiglio a tutti di aggiornare, perchè porta parecchie novità **:D

[![](http://www.allfreeportal.com/imghost/thumbs/472580Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=472580Schermata.png)
