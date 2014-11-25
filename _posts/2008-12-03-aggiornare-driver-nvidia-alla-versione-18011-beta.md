---
comments: true
date: 2008-12-03 20:32:19+00:00
layout: blog
title: Aggiornare driver Nvidia alla versione 180.22!
categories:
- ArchLinux
- Ubuntu
- Unix
---

Questa nuova release, la **180.22**, apporta dei** miglioramenti davvero notevoli**.


<blockquote>

> 
> 
	
>   * Improved VDPAU error detection and reporting.
> 
	
>   * Improved VDPAU support for some video bitstreams.
> 

Exactly what bitsreams they are talking about is unknown.

Additional changes:

	
>   * Added support for the following new GPUs:

	
>     * GeForce 9400M
> 


> 
	
>   * Fixed font corruption on GeForce 6 and 7 series GPUs when the GlyphCache setting is enabled.
> 
	
>   * Fixed a memory leak problem when the GlyphCache setting is enabled.
> 
	
>   * Added support for GVO full-range color.
> 
	
>   * Fixed a problem parsing the monitor sync range X config file options.
> 

</blockquote>


La prova è stata fatta su Ubuntu Hardy 32 bit, Ubuntu Intrepid 32 bit e ArchLinux i686, con Gnome, rispettivamente 2.22.3 e 2.24.1 e 2.24.2

È funzionato tutto alla perfezione e, IMHO, i miglioramenti sono ben visibili!

Consiglio l'upgrade anche a voi, tanto mal che vada li rimuovete e reinstallate i vecchi!

L'installazione è semplice, _**(valida per UBUNTU E DERIVATE. Per altre distro cambia solo la parola "init.d") **_scarichiamo i driver da qui:


[DRIVER UNIX 32 BIT](http://it.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run)



Ora per installarli dobbiamo fermare X, quindi:


`CTRL+ALT+F2`




`sudo /etc/init.d/gdm stop`




`cd /PERCORSO-FILE-SCARICATO`




`chmod +x *.run`




`sudo ./*.run` (**DEVE** essere dato con _sudo_ altrimenti da errore lo script)



Per _**ArchLinux**_ invece basta aprire il terminale e digitare:


`yaourt -S nvidia-beta`



_**Enjoy it **_:-D


[![](http://www.allfreeportal.com/imghost/thumbs/536264Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=536264Schermata.png)
