---
author: pol@blog
comments: true
date: 2008-07-07 17:23:10+00:00
layout: post
slug: compilazione-kernel-manuale
title: Compilazione kernel manuale
wordpress_id: 42
categories:
- Unix
---

Allora, ho deciso di fare questa guida perchè a noi linuxiani non piacciono le cose automatiche che lavorano al posto nostro anche perchè, che gusto c'è a fare e non capire??

Allora vediamo di capire quali sono i procedimenti:



	
  * Innanzitutto installiamo le dipendenze necessarie:


`sudo apt-get install build-essential kernel-package  libncurses5-dev [linux-kernel-headers errata corrige]
`



	
  * Poi procuriamoci il kernel da questo inidirizzo:


[http://www.eu.kernel.org/pub/linux/kernel/v2.6/](http://www.eu.kernel.org/pub/linux/kernel/v2.6/)



	
  * Spostiamo il kernel in /usr/src;


`sudo cp PERCORSO-DOVE-SI-TROVA-KERNEL-SCARICATO  /usr/src`



	
  * Scompattiamo il kernel:


`sudo tar jxvf linux-VERSIONE-KERNEL.tar.bz2`



	
  * Creiamo un link simbolico di lavoro:


`sudo ln -s linux-VERSIONE linux`



	
  * Apriamo la cartella appena creata e copiamo il vecchio file di configurazione:


`cd linux && sudo cp /boot/config-VERSIONE-DEL-KERNEL-INSTALLATA  .config `



	
  * Usiamo la vecchia configurazione e rispondiamo alle domande a seconda del nostro hardware:


`sudo make oldconfig`



	
  * Ora iniziamo a compilare dando:


`sudo make menuconfig`

(per me il meglio se si ha almeno un'idea di cosa si sta facendo e penso di si  sennò non stareste leggendo qui, LOL)

oppure

`sudo make gconfig`

(non consigliato in quanto non ti lascia fare alcune cose. Bisogna installare delle librerie necessarie che verranno richieste)

oppure

`sudo make xconfig`

(tutti dicono il meglio, ma io mi trovo da dio con menuconfig. Bisogna installare delle librerie necessarie che verranno richieste)

Ora facciamo le modifiche consone al nostro hardware seguendo la [guida di slacky.eu](http://www.slacky.eu/wikislack/index.php?title=Kernel_Menuconfig#Local_version_-_append_to_kernel_release)

Dopo aver fatto ciò, salviamo premendo EXIT e poi YES.

Ora arriva il momento di compilare!

Ora diamo i comandi per compilare, ocio che **se abbiamo un DUAL-CORE dobbiamo scrivere:**

`sudo -s`
`CONCURRENCY_LEVEL=3 make-kpkg –revision X.XX –append-to-version -XX –initrd kernel_image kernel_headers modules_image`
`exit`

Mentre **se NON abbiamo un dual core scriviamo:**
`sudo -s`
`make-kpkg –revision X.XX –append-to-version -XX –initrd kernel_image kernel_headers modules_image`
`exit`


### **CI SONO 2 TRATTINI (che a volte wordpress non fa visualizzare) DAVANTI A REVISION, APPEND E INITRD!**


Dove:

**CONCURRENCY_LEVEL=3:** sfrutta i 2 core per compilare e si farà moooolto prima (sarebbe n° core + 1)

**--revision X.XX**: la revisione del vostro kernel, potete mettere i numeri che volete sulle X.

**--appendo-to-version -XX**: il nome del kernel, ovvero se mettiamo -ciao allora sarà: 2.6.25-ciao. Quindi alle X mettete ciò che volete

**--initrd: sempre metterlo!** Esso dice a make-kpkg di creare per il kernel compilato anche una immagine _initial ram disk_. Questa è fondamentale per chi, come me, dimentica di settare qualcosa come statico invece che come modulare. Senza initrd possono capitare due cose: avete settato quello che c’era da settare come statico, e va tutto liscio, con anche due secondi in meno al boot, o vi viene restituito un Panic grosso come una casa. Ciò è dovuto al fatto della mancata impostazione come statici dei moduli che provvedono al controllo del disco fisso. Se siete guru della compilazione kernel, omettete l’initrd… ma io non posso farne a meno: senza initrd il mio PC non parte.

**kernel_image:** mi sembra ovvio, l'immagine del kernel!

**kernel_headers:** mi sembra ovvio pure questo, gli headers del kernel!

**modules_image:** comparirà il .deb SOLO se avete la cartella modules in /usr/src, se non c'è, non mettetelo!

Ora che abbiamo fatto ciò, premiamo INVIO e aspettiamo!

Una volta compilato scrivere:

`cd ..`

sudo dpkg -i *.deb
