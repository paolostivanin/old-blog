---
comments: true
date: 2008-09-06 15:37:57+00:00
layout: post
title: Exaile 0.3-dev! Completamente riscritto!
categories:
- Ubuntu
- Unix
---

Oggi stavo usando (con soddisfazione) Exaile 0.2.13, quando mi son chiesto "chissà se c'è una dev-branch"?

Così ho cercato un po' in giro e ho trovato che** [EXAILE 0.3](http://www.exaile.org/)** **_è sotto pesante sviluppo._**

Ma quanto pesante?

Beh, TANTO pesante!

Infatti il dev di Exaile ha deciso di **RISCRIVERE TOTALEMENTE EXAILE** perchè, secondo lui, il codice potrebbe essere migliore e inoltre, usando codice migliore, in futuro sarà più facile aggiungere delle cose!

Detto ciò, se siete curiosi di provarlo, seguite questi semplici passaggi:


`sudo apt-get install bzr`




`bzr checkout lp:exaile`




`cd exaile`




`cd mmkeys`




`cd build`




`mkdir lib`




`cd lib`



**Cliccate col destro e premete su "crea file" e lo chiamatae: mmkeys.so**


`cd`




`cd exaile`




`make`




`sudo make install`



Ed ecco fatto che installerà Exaile**. Per aggiornare:**


`cd exaile`




`bzr update`
