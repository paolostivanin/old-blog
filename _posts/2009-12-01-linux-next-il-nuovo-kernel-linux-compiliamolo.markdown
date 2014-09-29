---
author: pol@blog
comments: true
date: 2009-12-01 20:09:48+00:00
layout: post
slug: linux-next-il-nuovo-kernel-linux-compiliamolo
title: Linux-next, il nuovo kernel Linux, compiliamolo!
wordpress_id: 777
categories:
- ArchLinux
- Ubuntu
- Unix
---


	
  1. Creiamo una cartella nella home che si chiama mykernel

	
  2. Scarichiamo i source del kernel _$versione-$rc_ da qui: [KERNEL-2.6.34-rc2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.34-rc2.tar.bz2)

	
  3. Scarichiamo la patch linux-next-_$data_ da qui: [LINUX-NEXT-20100325](http://www.kernel.org/pub/linux/kernel/v2.6/next/patch-v2.6.34-rc2-next-20100325.bz2) e posizioniamola all'interno della cartella kernel appena creata, quindi scompattiano l'archivio

	
  4. Scompattiamo pure l'archivio kernel-_$versione-$rc_ nella cartella mykernel appena creata

	
  5. Entriamo nella main directory del kernel-_$versione-$rc_, apriamo il terminale e diamo:
`patch -p1 <../patch-v2.6.34-rc2-next-20100325`

	
  6. Ora seguiamo una qualsiasi guida per compilare il kernel (guardate la wiki della vostra distro, di solito c'è sempre)


Vi ricordo che linux-next è il branch UNSTABLE del futuro nuovo e innovativo kernel Linux (per i newbie: non è la serie 2.6.X, ndr), a buon intenditor poche parole :)
