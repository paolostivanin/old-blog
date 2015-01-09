---
comments: true
date: 2011-05-18 16:00:19+00:00
layout: post
title: Distro GNU/Linux, piccoli difetti grandi incazzature!
categories:
- Debian &amp; Co
- Generale
- Ubuntu
- Unix
---

Chi di noi non è mai stato soggetto ad un bug nella propria vita informatica?

Ma come per ogni cosa "_ci sono modi e modi"_ e il modo in cui questo bug mi ha perseguitato **per mesi** è stato snervate!

Quella minuscola cazzata che pensavo fosse chissà cosa era in realtà una banalità atroce, ma una _"banalità così banale"_ che ancora adesso non riesco a capacitarmi di come sia possibile non solo che ci sia un bug del genere, ma che sia pure stato Windows XP a farmi capire il perchè di tutto questo casino!

Ma andiamo con ordine, vediamo di capire cos'è successo e come si è risolto.

<!-- more -->**Il bug:** non potevo uppare più files in un colpo con Wordpress (uploader flash) ma dovevo usare l'uploader del browser (uno alla volta -.-'')

**Cosa succedeva:** praticamente quando caricavo più files mi compariva la scritta _"HTTP Error"_, _"I/O Error"_ e il caricamento stava fermo su _Crunching..._

**È un bug noto?** Eccome! provate a scrivere su google _"wordpress i/o error"_ oppure _"wordpress flash uploader"_ oppure _"wordpress upload http error"_

**Workaround?** Ehh...le ho provate tutte! Tutto quello che ho trovato ho provato! Modifica php.ini, modifica .htaccess, ripristino alle condizioni originali, ecc

**E...?** E oggi dopo aver installato Wordpress 3.1.2 e 3.2-beta1 in localhost ho notato che il bug non c'era 8O

**Quindi...**quindi ho pensato: _"cavolo devo avere dei plugin che rompono le pelotas..."_ perciò prendi i plugin e installali su entrambi i blog in localhost...

**Risultato:** il bug ancora non c'era :?

**Ahia...**eh già proprio ahia perchè non sapevo più cosa cavolo fare, avevo già programmato la nottata _"bug hunting"_ oggi ma, grazie al pc della mia ragazza che ha ancora Windows XP _**(si WINDOWS XP, quel catorico si software fatto nel 2001, proprio WINDOWS XP),**_ sono finalmente riuscito a capire il problema!

**Premessa: **io avevo impostato da plesk che "wp-admin" fosse protetta da password.

**Spiegazione: **Quando con WinXP ho provato ad uppare dei files mi è comparso un pop-up che mi chiedeva la password _(che mi ha permesso di notare che il file php che si occupa del multiupload è in wp-admin)_ per poter utilizzare l'uploader flash! Ora vorrei capire perchè Ubuntu, Debian, Archlinux, Linux Mint e Fedora non siano dotate di questa avanzatissima funzionalità.

**Soluzione:** ho disabilitato la password dalla directory ma ho aggiunto altre difese. Resto però sconcertato del fatto che in tutti questi mesi non mi sia mai apparsa l'ombra di un pop-up per l'inserimento della password. :(
