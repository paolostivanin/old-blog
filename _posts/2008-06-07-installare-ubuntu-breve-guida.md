---
comments: true
date: 2008-06-07
layout: blog
title: Installare Ubuntu, breve guida!
categories:
- Ubuntu
---

Ciao a tutti, sul post di oggi vi insegnerò come installare Ubuntu, o meglio, vi insegnerò come PARTIZIONARE l'HD per installare Ubuntu!

Non sto qui a spiegarvi passo-passo come installarlo perchè è una cosa semplicissima, sono 7 passaggi di cui solo 1 (partizionamento) può rompere le scatole a chi non è almeno un po' conoscente di Ubuntu (anche se altre distro hanno un sistema di installazione pressochè uguale quindi questo metodo va bene per gran parte delle distro della famiglia LINUX).

_**PREMESSA: SE AVETE UN DUAL/QUAD-CORE USATE LA 64 BIT**__** (la cui tag è AMD64 o X86_64),**__** VI CONVIENE!**_

Allora, mettiamo il nostro cd di Ubuntu nel lettore cd, cambiamo le perifiche di boot dal bios (di solito premendo CANC alla primissia schermata quando accendete il piccì) e selezioniamo (genericamente parlando) "DVD-ROM".

Ora ci appare un menù con tutte le lingue disponibile, scegliamo quella che più ci garba e premiamo invio.

Dopodichè dovremo scegliere fra le prime 2 opzioni:



	
  1. Far partire Ubuntu da live

	
  2. Installare Ubuntu direttamente


Di solito, se uno è la prima volta che usa Ubuntu, sceglie la "1", questo perchè facendo partire la live, si può vedere se Ubuntu riconosce tutto il nostro Hardware!

Dopo che avremo girato un po' premiamo sull'icona "Installa" e da qui parte il Wizard di 7 passaggi.

Arrivati al partizionamento ci sono 4 opzioni:

![Schermata partizionamento](http://sodilinux.itd.cnr.it/zoomlinux/installaz/5.1.png)

Scegliamo quello che preferiamo con alcuni accorgimenti:



	
  1. Per dimensionare "graficamente" una partizione

	
  2. Per usare TUTTO l'HD cancellando TUTTO quello che c'è dentro

	
  3. Se è già installato un 		      sistema operativo ma è rimasto dello spazio libero non partizionato

	
  4. Manualmente, il mio preferito (e vedrete anche il vostro)




Per installare Ubuntu oltre al sistema operativo residente, 		    occorre creare 2 partizioni:






	
  1. una partizione detta **area di swap**

	
  2. una partizione con** file system 		    ext3 (o ext4 per Ubuntu 9.04 e successive)
**



	
  * **l'area di swap** deve essere compresa tra il valore 		    della RAM del proprio computer e il suo doppio (ES: se si ha 256 mb 		    di RAM, è possibile 		    impostare 512 mb per l'area di swap, **ma se si ha 1 o più GB di ram, NON serve raddoppiare, ma basta mettere il valore reale della ram**),

	
  * **l'ext3 (o ext4) **conterrà il 		    sistema operativo vero e proprio.




Per creare una partizione vuota (tipo free), è possibile 		    procedere secondo questa modalità:




- ridimensionare (cioè diminuire) la partizione 		    di Windows o Mac. In questo caso bisogna cliccare sulla partizione di Windows 		    (quella di **Tipo: 		    ntfs**) e poi su _Edit partition_




Dopo aver scelto quanti GB prendere (prendete una bella porzione, considerando che Ubuntu installato occupa 3.8GB + Area Swap) su _"use as"_ lasciamo quello che c'è e su _"mount point"_ lo stesso.




Ecco fatto, ora abbiamo 2 partizioni.




Ora clicchiamo su quella appena creata a premiamo _"DELETE PARTITION"_, la partizione sarà quindi chiamata "free space".




Clicchiamo nuovamente su questa a premiamo _"NEW PARTITION" _e creiamo l**'area di swap **in questo modo:






	
  * _Type for the new partition_: PRIMARY (_**DEVE**_ essere di tipo _**PRIMARIO**_ sia la SWAP che la EXT3)

	
  * _New partition size in Megabytes_: (vedere cosa scritto sopra per scegliere la grandezza della swap)

	
  * _Location for the new partition_: come preferite, è lo stesso ;)

	
  * _Use as_: SWAP

	
  * _Mount Point_: non potete fare niente


Ri-clicchiamo nuovamente sulla partizione 		  libera (free space) e su **New partition** e ora creiamo la partizione dove va installato il nostro sistema in questo modo:



	
  * _Type for the new partition_: PRIMARY

	
  * _New partition size in Megabytes_: quello segnato di default (ovvero il rimanente dopo aver creato la swap)

	
  * _Location for the new partition_: come preferite, è lo stesso ;)

	
  * _Use as_: EXT3 o EXT4

	
  * _Mount Point_:  /  (il mount point "/" starebbe per "root". Selezionate quello li dall'elenco, è il primo)


Ora fate ok!

Molto bene, ora abbiamo le nostre 2 partizioni pronte per essere usate!

Seguite il tutorial fino alla fine e aspettate l'installazione!

Riavviate e accedete, nel prossimo post vi dirò cosa fare dopo aver eseguito l'installazione e aver fatto il primo login!

Spero vi sia state tutto o abbastanza chiaro, nel caso ci fossero dubbi o imprecisioni, non esistate a scrivermi!
