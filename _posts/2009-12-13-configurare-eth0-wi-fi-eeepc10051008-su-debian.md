---
comments: true
date: 2009-12-13 11:07:53+00:00
layout: blog
title: Configurare Eth0 + Wi-fi Eeepc1005/1008 su Debian!
categories:
- Ubuntu
- Unix
---

L'altro giorno stavo cercando di installare Debian sul mio Eeepc 1008ha...allora scarico la iso testing, masterizzo nella usb, booto, arrivo alla rete e....**0! 0 assoluto**!

Le periferiche vengono trovate ma non si riescono a configurare! (a causa del kernel 2.6.30 che ha problemi con le suddette periferiche del suddetto Eeepc).

Dopo vari scervellamenti sono riuscito a trovare (con enorme soddisfazione) una soluzione, vediamola insieme :)



	
  * Se abbiamo il wifi, andiamo nella pagine di configurazione del router e mettiamo la chiave **da WPA a WEP**;

	
  * Scarichiamo i files [boot.img.gz](http://people.debian.org/~joeyh/d-i/images/daily/hd-media/boot.img.gz) e [debian-testing-netinst](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-netinst.iso) ;

	
  * Inseriamo la penna usb **SMONTIAMOLA**, apriamo il terminale e scriviamo questo comando (dove la X sta per _b_ o _c_ di solito):




`zcat boot.img.gz > /dev/sdX`






	
  * Ora montiamo la penna usb e copiamo manualmente (copia-incolla) il file _.iso _nella penna usb;

	
  * Bootiamo in_** expert mode **_(**NON** via grafica perchè a volte da problemi) e installiamo Debian normalmente, **lasciando perdere** la configurazione rete. Fatta l'installazione base riavviamo;

	
  * Scarichiamo: [kernel-2.6.32](http://packages.debian.org/unstable/linux-image-2.6.32-trunk-686) , [wireless-tools](http://packages.debian.org/unstable/wirelesstools) , [libiw](http://packages.debian.org/sid/libiw30)

	
  * Ora rimonitamo la chiavetta usb in un pc funzionante, formattiamola in **ext2** e** copiamoci dentro i 3 file appena scaricati**. (nel caso avessimo problemi e non ci lasciasse copiare i files, date questi comandi: `chmod -R +rwx /media/NOMEUSB` , `chown -R NOMEUTENTE /media/NOMEUSB`);

	
  * Ora rimuoviamo la chiavetta, inseriamola nel netbook e diamo (dove X sta per _b _o _c_)**_ _**:




`sudo su`




`fdisk -l`




`mkdir /mnt/pusb`




`mount /dev/sdX1 /mnt/pusb`




`cd /mnt/pusb`




`cp *.deb /home/NOMEUTENTE`




`cd /home/NOMEUTENTE`




`dpkg -i *.deb`






	
  * Riavviamo, bootiamo col nuovo kernel;

	
  * Ora configuriamo la nostra **wlan0** in questo modo:




`sudo nano /etc/network/interfaces`




Copiamo dentro questi comandi:




auto wlan0
iface wlan0 inet dhcp
address _VOSTRO-IP-FISSO (192.168.ecc.ecc)_
netmask 255.255.255.0
gateway _INDIRIZZO-ACCESSO-AL-ROUTER (192.168.ecc.ecc)_






	
  * Salviamo il file e chiudiamo, ora facciamo partire il nostro wifi con questo comando:




`iwconfig wlan0 essid NOME-RETE key CHIAVE-ESADECIMALE mode managed`




**_(la chiave in esadecimale è composta da soli numeri e si trova nella pagina di configurazione del router)_**




`ifconfig wlan0 up`




`dhclient wlan0`




`ping google.com`


_**N.B.: se il comando ping ci ridà "unknow hosts" vuol dire che avete sbagliato qualcosa!**_

Ecco fatto, ora abbiamo il nostro wifi funzionante! Ora possiamo procedere all'installazione di Xorg, Gnome/Kde/Xfce/E-17 ecc, ma prima bisogna aggiungere manualmente al file _/etc/apt/sources.list _i repo che desideriamo, _testing o sid_ :)
