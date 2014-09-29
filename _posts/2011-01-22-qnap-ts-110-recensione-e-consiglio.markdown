---
author: pol@blog
comments: true
date: 2011-01-22 13:43:49+00:00
layout: post
slug: qnap-ts-110-recensione-e-consiglio
title: Qnap TS-110, recensione e consiglio!
wordpress_id: 1114
categories:
- Generale
- NAS Qnap
tags:
- nas
- qnap
- ts-110
---

Ecco arrivato il mio nuovo acquisto! :)

Si tratta del [NAS Qnap TS-110](http://www.qnap.com/pro_detail_feature.asp?p_id=136) equipaggiato con un hard disk della Samsung, nello specifico un [Samsung Spinpoint F3](http://www.samsung.com/global/business/hdd/productmodel.do?type=94&subtype=98&model_cd=507) da 1TB, S-ATA I, 32MB di cache!

Nella confezione oltre al NAS troviamo un cavo ethernet, il cavo AC, delle viti, un CD e un piccolo manuale.

Costruttivamente parlando il NAS è veramente ben fatto, i materiali sono solidi e non scricchiolano ne traballano.

Davanti troviamo i led di stato, il tasto di accensione (in basso) e un ingresso USB con un tasto (in alto): praticamente se inserite li un device USB e poi premete il tasto, il NAS farà la copia di quello che c'è dentro...figo eh :D

[caption id="attachment_1115" align="aligncenter" width="157" caption="Fronte del NAS"][![]({{ site.baseurl }}/images/2011/01/front1-157x300.jpg)]({{ site.baseurl }}/images/2011/01/front1.jpg)[/caption]

Sul retro invece troviamo: due USB, una porta e-SATA, una Gigabit Ethernet e l'ingresso AC.

Il cavo e-SATA **non** è in dotazione ma su eBay ho trovato un cavo e-SATA -> SATA a pochi spiccioli ;)

[caption id="attachment_1116" align="aligncenter" width="158" caption="Retro del NAS"][![]({{ site.baseurl }}/images/2011/01/retro1-158x300.jpg)]({{ site.baseurl }}/images/2011/01/retro1.jpg)[/caption]

L'hard disk che ho scelto è molto  silenzioso, non produce nessun tipo di rumore tranne quando viene formattato che emette un leggero ronzio. Solo una piccola cosa mi ha infastidito: dei 1000 GB solo 931,15 GB erano disponibili che una volta formattato in EXT 4 sono diventati 915!

Per quanto riguarda la WebGUI devo dire che è veramente ben fatta: ha moltissime opzioni, è veloce e intuitiva!

Poi le funzionalità offerte da questo NAS sono una miriade: web server, ftp server, file server, download center (torrent, emule, rapidshare, megaupload, http), print server, itunes server, backup automatico, accensione/spegnimento programmati, iSCSI, sorveglianza, S.M.A.R.T., notifiche via email e SMS ecc ecc...potrei continuare per ore! :D

I file system supportati sono: NTFS, FAT, EXT 3, EXT4 ma con il [firmware 3.4.0](http://www.qnapclub.it/viewtopic.php?f=39&t=3211) in arrivo a breve si aggiungerà HFS+

Una volta montato l'hard disk e acceso il NAS (del quale vi consiglio caldamente la lettura del manuale di 415 pagine xD) dovrete aprire il vostro browser e andare all'indirizzo ip del NAS seguito da _:8080_.

Per vedere qual è l'ip del NAS io sono entrato nel mio router e sotto la sezione LAN l'ho subito individuato!

Al primo accesso oltre alle normali configurazioni inziali come configurare la rete, **cambiare la password di accesso**, **cambiare la porta di accesso**, formattare il disco ecc, **vi consiglio** anche di **attivare SSH** (ovviamente cambiando porta dalla 22 ad un'altra a vostra scelta e abilitando il controllo accesso per impedire a qualcuno di connettersi) e il perchè lo vediamo subito ;)

<!-- more -->

Cos'è successo?

Praticamente volevo crearmi un certificato SSL personale, in modo da utilizzare la connessione _https_ senza avvisi o errori vari!

Da _**furbo**_ dopo aver caricato il mio certificato personale ho attivato l'opzione _"Forzare soltanto la connessione sicura (SSL)"_.

[caption id="attachment_1120" align="aligncenter" width="300" caption="NON spuntate la casellina li sopra :)"][![]({{ site.baseurl }}/images/2011/01/webssl1-300x85.png)]({{ site.baseurl }}/images/2011/01/webssl1.png)[/caption]

Risultato?

Devo aver sbagliato qualcosa nel certificato così non riuscivo più a connettermi al mio NAS!

Ehhh bel casino! Premere il tasto reset no...non avevo voglia di riconfigurare tutto da capo!

Così dopo qualche minuto ho trovato uno che ha avuto il mio stesso problema solo che lui l'ha risolto in modo un po' differente...ma il mio è senz'altro più veloce :)

Praticamente bisogna accedere via SSH al proprio NAS:


`ssh -p PORTA -l admin IP-DEL-NAS`


inserite la password che avete impostato nella configurazione inziale e una volta dentro la shell date:


`cd /mnt/HDA_ROOT/.config`




`vim uLinux.conf`


e poi cercate la riga:


`Force SSL = 1`


e la fate diventare


`Force SSL = 0`




[caption id="attachment_1118" align="aligncenter" width="300" caption="Comandi"][![]({{ site.baseurl }}/images/2011/01/cdnas1-300x58.png)]({{ site.baseurl }}/images/2011/01/cdnas1.png)[/caption]

[caption id="attachment_1119" align="aligncenter" width="194" caption="Modificare come sta scritto qui!"][![]({{ site.baseurl }}/images/2011/01/sslmod1.png)]({{ site.baseurl }}/images/2011/01/sslmod1.png)[/caption]

Se non siete abituati ad usare vim (come il sottoscritto) dovrete cercare i comandi base con il _man _o con _google_.

Usciti da vim date un bel


`reboot`


ed ecco che potrete di nuovo accedere via WebGUI al vostro NAS :)

[caption id="attachment_1117" align="aligncenter" width="300" caption="WebGUI"][![]({{ site.baseurl }}/images/2011/01/gui1-300x174.png)]({{ site.baseurl }}/images/2011/01/gui1.png)[/caption]
