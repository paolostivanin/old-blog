---
author: pol@blog
comments: true
date: 2008-06-22 16:29:43+00:00
layout: post
slug: kerneler-compiliamo-il-kernel
title: Kerneler! Compiliamo il kernel!
wordpress_id: 16
categories:
- Unix
---

Sito ufficiale: [www.kerneler.org](http://www.kerneler.org)

Kerneler è un utile programmino che ci aiuta alla compilazione del kernel!

Vediamo come usarlo!

Innanzitutto vediamo di installare delle dipendenze fondamentali:



	
  * _ bash_

	
  * _ build-essential_

	
  * _ libncurses5_

	
  * _ libncurses5-dev_

	
  * _dialog_

	
  * _kernel-package_

	
  * _fakeroot_

	
  * _module-assistant_

	
  * _patch
_


Benissimo, scarichiamo kerneler da qui:

[http://downloads.sourceforge.net/kerneler/kerneler_0.19a_alpha.tar.gz](http://downloads.sourceforge.net/kerneler/kerneler_0.19a_alpha.tar.gz)

Fatto ciò apriamo scompattiamo l'archivio ed entriamo dentro la cartella kerneler.

Una volta dentro digitiamo: ` ./kerneler ` per far partire il programma!

Ora ci comparirà una finestra come questa:

![](http://www.tuxjournal.net/wp-content/uploads/2007/11/k3.jpg)

Come vedete le cose da fare sono semplici, basta cliccare in cima ad ogni cosa ed è fatta :-)

Per vedere cosa scegliere nel kernel dovete affidarvi a guide come questa:

[http://www.slacky.eu/wikislack/index.php?title=Kernel_Menuconfig#Local_version_-_append_to_kernel_release](http://www.slacky.eu/wikislack/index.php?title=Kernel_Menuconfig#Local_version_-_append_to_kernel_release)

Ok raga, avete compilato il vostro kernel!

Guida scarsa lo so, ma il programma è così semplice che non penso abbia bisogno di tante spiegazioni :-)
