---
author: pol@blog
comments: true
date: 2010-12-11 11:13:13+00:00
layout: post
slug: minitest-driver-nouveau-vs-driver-proprietari
title: 'Minitest: driver Nouveau VS driver proprietari'
wordpress_id: 1028
categories:
- ArchLinux
- Unix
tags:
- archlinux
- driver
- glxgears
- nouveau
- nvidia
---

Certo Glxgears non sarà un test ed elaborato e preciso ma almeno un'indicazione di massima la fornisce.

Con Ubuntu 10.04 + **driver proprietari 260.19** + Xorg 1.7.6 = **3100 FPS**

Con ArchLinux + driver Nouveau 0.0.16_git20100819-1 + Xorg 1.9.2 = **950 FPS**

[caption id="attachment_1029" align="aligncenter" width="300" caption="Glxgears con Nouveau!"][![]({{ site.baseurl }}/images/2010/12/glxarch1-300x143.jpg)]({{ site.baseurl }}/images/2010/12/glxarch1.jpg)[/caption]

Ovviamente sapevo che non potevo aspettarmi un valore alla pari dei driver proprietari che sono sviluppati da anni.

Comunque ciò non influisce sulle prestazioni quotidiane **anzi** la differenza **non** si nota (almeno per il mio uso).

Navigo su internet, guardo film in flash, guardo mkv 1080p e tutto funziona normalmente!

Inoltre ho fatto un altro test: ho **abilitato** su Chromium le **flags** _WebGL_ e _GPU Accelerated Compositing_, ho fatto un paio di prove di quelle riportati <del>QUI</del> _(sito cancellato causa vulnerabilità RFI)_ e tutto ha funzionato a dovere! No crash, renderizzazione ottima!

Sono davvero soddisfatto di questi driver non mi aspettavo un risultato così ottimo!

Di certo questi sono e resteranno i miei driver di default :)


