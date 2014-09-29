---
author: pol@blog
comments: true
date: 2008-07-27 16:45:37+00:00
layout: post
slug: risoluzione-bug-intrepid
title: Risoluzione bug Intrepid!
wordpress_id: 94
categories:
- Ubuntu
---

Stavo pensando cosa aspettano a correggere questo bug quelli di Ubuntu...Così mentre non avevo niente da fare mi son ricordato dell'esistenza degli scriptini facili, veloci e funzionali che si possono fare con la shell bash, così ho inventato un metodo abbastanza veloce per risolvere il problema di Intrepid che se spegni o riavvii torna alla schermata di login.



	
  * **Per spegnere il pc scriviamo questo piccolo script:**


`sudo gedit /home/UTENTE/Scrivania/spegni.sh`



	
  * scrivete questa riga:


`sudo shutdown -h now`



	
  * Diamo i permessi di scrittura:


`chmod +rwx /home/utene/Scrivania/spegni.sh`



	
  * **Per riavviare invece scriviamo questo:**


`sudo gedit /home/utene/Scrivania/riavvia.sh`



	
  * scrivete questa riga:


`sudo reboot`



	
  * Diamo i permessi di scrittura:


`chmod +rwx /home/utene/Scrivania/riavvia.sh`

Quando cliccheremo sopra premiamo su: **ESEGUI NEL TERMINALE** e inseriamo la nostra password!

Ecco "risolto" questo fastidioso bug!
