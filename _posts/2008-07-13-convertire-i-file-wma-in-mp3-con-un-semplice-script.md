---
comments: true
date: 2008-07-13 13:00:36+00:00
layout: blog
title: Convertire i file WMA in MP3 con un semplice script
categories:
- Generale
---

Quante volte vi è capitato di dover convertire un file wma in mp3 e non sapete come fare?

Beh, Nautilus ci viene in aiuto e, con dei piccoli e semplice passi, avremo uno scriptino pronto pronto per fare ciò :D

**PREMESSA: QUESTO SISTEMA FUNZIONA CON DEBIAN, UBUNTU, FEDORA, ARCH, GENTOO, INSOMMA TUTTE LE DISTRO CHE HANNO GNOME** :D



	
  * Intanto installiamo le basi per far andare tutto l'amabaradan:


`sudo apt-get install mplayer lame ubuntu-restricted-extras`



	
  * Scarichiamo questo file testo:


[convert-wma-to-mp3](http://polslinux.wordpress.com/2008/07/13/convertire-i-file-wma-in-mp3-con-un-semplice-script/convert-wma-to-mp3/)



	
  * Rinonimiamo il file TOGLIENDO IL .doc


quindi **DA** convert wma to mp3.doc** DIVENTA **convert wma to mp3



	
  * Spostiamo il file nella cartella scritps di nautilus:


`cp convert wma to mp3 ~/.gnome2/nautilus-scripts`



	
  * Rendiamolo eseguibile con il comando:


`chmod +x ~/.gnome2/nautilus-scripts/convert wma to mp3`

Ecco fatto raga!

Ora per far funzionare questo script basta cliccare col tasto destro su un file .wma e scegliere la voce _“script”_ e _“convert wma to mp3“_.
