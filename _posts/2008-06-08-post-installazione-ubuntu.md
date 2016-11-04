---
comments: true
date: 2008-06-08 22:30:12+00:00
layout: post
title: Post-installazione Ubuntu 9.10!
categories:
- Ubuntu
- Unix
---

Ri-ecccomi gente!

Allora sul post di prima vi ho "insegnato" come partizione l'HD per poi installare Ubuntu!

Ora vi dirò cosa fare per avere una Ubuntu-box sempre aggiornata, ma stabile e che vi permetta di fare tutto ciò che vorrette!

Intanto, appena effettuato l'accesso, NON fate gli aggiornamenti, aspettate, portate 5 minuti di pazienza!

Allora:

- Aggiungiamo i repository Medibuntu, che sono quello che ci permetteranno di avere mooolte cose (tra qui codec, acroread, flash, etc). Allora, intanto aggiungiamolo alla nostra sources.list con questo comando:

`sudo wget 
--output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list &&
sudo apt-get --quiet update &&
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get --quiet update`

- Aggiungiamo la chiave GPG e aggiorniamo i repo:

`sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update`

- Aggiungiamo altri repo molto utili in questo semplice modo:

Sistema --> Amministrazione --> Sorgenti Software:  nella sezione _Software per Ubuntu_, selezionate tutto; nella sezione _Software da terze parti_, seleazionate tutto; nella sezione _Aggiornamenti_, selezionate tutto. Il resto lasciate stare.

Ora passiamo alla fase di AGGIORNAMENTO:

- Per aggiornare apriamo il terminale e scriviamo:

`sudo apt-get dist-upgrade`

Attendiamo lo scaricamento e l'installazione di tutto, se necessario riavviamo.

Una volta fatto tutto, puliamo un po' Ubuntu in questo modo:

-Apriamo il terminale e scriviamo:

`sudo apt-get autoclean && sudo apt-get autoremove && sudo dpkg --purge `COLUMNS=300 dpkg -l "*" | egrep "^rc" | cut -d  -f3``

Fatto, ora abbiamo la nostra Ubuntu-box aggiornata e bella pulita!

Se ci sono dubbi o perplessità o correzioni da fare, non esitate a lasciare dei commenti o delle domande eh! =)

Ora installiamo le cose utili:

**Acrobat Reader:**

`sudo apt-get install acroread`

**Per mp3, avi, ecc**:

`sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse`

**Per vedere i DVD:**

`sudo apt-get install libdvdcss2 libdvdnav4 libdvdread4`
