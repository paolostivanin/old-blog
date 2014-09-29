---
author: pol@blog
comments: true
date: 2008-07-31 12:17:05+00:00
layout: post
slug: backerupper-faccimo-backup-dei-nostri-dati
title: BackerUpper, faccimo backup dei nostri dati!
wordpress_id: 121
categories:
- Unix
---

Girovagando per la rete cosa non si trova eh???

Ecco a voi **BACKERUPPER**, l'ennesimo prodotto di [SOURCEFORGE](http://sourceforge.net) (ui lov iu sourceforge :D ) che sforna software open-source e free a manetta :D

**BackerUpper**, è un tool che ci permette di effettuare un backup di una determinata cartella - oppure dell’intero disco - in maniera automatica o manuale, per avere sempre pronto un backup sicuramente funzionante del nostro pc.

Innanzitutto scarichiamo il tool da qui:

[SCARICA BACKERUPPER](http://sourceforge.net/project/showfiles.php?group_id=186109)

E vediamo che sono disponibili:

BackerUpper-0.24.32.tar.gz      ** <-- per architetture 32 bit**

BackerUpper-0.24-64.tar.gz       **<-- per architetture 64 bit**



	
  * Dopo averlo scaricato, scompattiamo **(AL POSTO DI XX METTERE 32 O 64)** e entriamo nella directory:


`tar -zxvf backerupper-0.24-XX.tar.gz && cd backerupper-0.24-XX`



	
  * Installiamo BackerUpper:


`sudo ./install.sh`



	
  * Ecco fatto, installato, veloce e indolore :D



	
  * Per eseguirlo, apriamo il terminale e scriviamo:


`backer`



	
  * Una volta eseguito questo è quello che ci appare:


[![](http://www.allfreeportal.com/imghost/thumbs/899333backer.png)](http://www.allfreeportal.com/imghost/viewer.php?id=899333backer.png)



	
  * 


Possiamo compilare il form e cliccare su backup now, oppure automatizzare la cosa creando un profilo:





[![](http://www.allfreeportal.com/imghost/thumbs/776001Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=776001Schermata.png)



	
  * Ora vi spiego come usarlo:



	
  1. **Per creare il backup,** cliccate su _NEW _e vi apparirà la finestra in basso;

	
  2. Compiliamo i campi: _Name _= nome che vogliamo; _DirToBakcup_ = directory di cui vogliamo fare il backup; _Destionation Dir_ = dove va a finire il backup; il resto è ogni quanto fare il backup!

	
  3. Clicchiamo su _OK_ e poi su _BACKUP NOW_ ed ecco a voi, basta aspettare (**mi ha stupito la velocità, 320MB in 2 minuti** :D )

	
  4. **Per ripristinare il nostro backup,** clicchiamo su _RESTORE_ e selezioniamo il nostro profilo e automaticamente sceglierà l'archivio da ripristinare; clicchiamo su _RESTORE_ ed ecco fatto, ripristinato il nostro backup :D


[![](http://www.allfreeportal.com/imghost/thumbs/361737Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=361737Schermata-1.png)

Ecco raga, spero sia tutto chiaro :D

**Dubbi, commenti, impressioni?** Prego postate pure che mi fa solo che piacere :D
