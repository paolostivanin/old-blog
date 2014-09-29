---
author: pol@blog
comments: true
date: 2012-01-25 15:10:17+00:00
layout: post
slug: bash-pwd-manager-v2-un-assaggio
title: Bash PWD Manager v2, un assaggio!
wordpress_id: 1777
categories:
- Projects
- Unix
tags:
- bash-pwd-manager
---

Come si può notare dal [changelog su Github](https://github.com/polslinux/BashPWDManager/blob/master/docs/changelog), la versione 2.0 di_** Bash PWD Manager**_ porterà un bel po' di novità.

Si va da una maggiore sicurezza ad una grafica completamente rivista e rinnovata rispetto la versione 1.X :)

Questo è il changelog completo (molto probabilmente anche il definitivo):


<blockquote>

> 
> 
	
>   * NEW: nuova UI
> 
	
>   * NEW: yad sostituisce zenity (yad è MOLTO più potente di zenity)
> 
	
>   * ADDED: db sqlite. Ora le password saranno salvate cifrate in un database cifrato.
> 
	
>   * ADDED: gruppi
> 
	
>   * ADDED: note
> 
	
>   * ADDED: scadenza password
> 
	
>   * ADDED: quando il db viene decifrato sarà presentata una lista dei titoli per poter scegliere quale pwd visualizzare
> 
	
>   * ADDED: controllo integrità db tramite md5sum
> 
	
>   * ADDED: possibile blocco del db tramite chattr
> 
	
>   * ADDED: opzioni per backuppare e ripristinare il db
> 
	
>   * ADDED: scelta se usare 1 metodo di cifratura (GPG + OpenSSL) oppure 2 (GPG+OpenSSL). Se viene selezionato di scegliere 2 metodi di cifratura si è **obbligati** a scegliere 2 pwds diverse!
> 
	
>   * ADDED: interfaccia CLI
> 
	
>   * ADDED: log file (pwd sbagliata, errore md5, backup info, etc)
> 
	
>   * IMPROVED: codice core viene rivisitato
> 
	
>   * IMPROVED: installer aggiornato per supportare le nuove caratteristiche
> 
	
>   * IMPROVED: uninstaller aggiornato per supportare le nuove caratteristiche
> 
	
>   * UPDATED: file README aggiornato con le nuove informazioni
> 

</blockquote>


Ed ecco a voi uno screenshot di come sarà la UI relativa all'inserimento dettagli...

[caption id="attachment_1778" align="aligncenter" width="249" caption="Bash PWD Manager - Add details"][![]({{ site.baseurl }}/images/2012/01/bashpwdm1.png)]({{ site.baseurl }}/images/2012/01/bashpwdm1.png)[/caption]

Enjoy :)
