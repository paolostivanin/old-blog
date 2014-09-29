---
author: pol@blog
comments: true
date: 2012-10-04 20:05:08+00:00
layout: post
slug: gentoo-e-il-non-boot
title: Gentoo e il non boot
wordpress_id: 2027
categories:
- Gentoo
- Unix
tags:
- /dev/console
- /dev/null
- boot
- gentoo
---

Dopo aver effettuato il chroot, preparato il sistema base, compilato il kernel, riavviato il PC e selezionato Gentoo dal menù di GRUB, ottengo uno strano messaggio relativo al device file `/dev/console` e il boot si blocca...

Un po' stranito da questo fatto cerco delle notizie al riguardo e trovo un'informazione molto interessante nella [wiki di Gentoo](http://www.gentoo.org/doc/en/udev-guide.xml) dove si afferma che questo problema deriva dalla mancanza della disponibilità di alcuni "device files" (in particolare `/dev/null` e `/dev/console`) prima che `/dev` sia montato e gestito da udev _(tra l'altro c'è scritto che può capitare se si usano dei media vecchi ma io ho usato lo stage3 del 17/09/2012 xD)___.

Comunque _(e per fortuna)_ la soluzione in questo caso è molto semplice:

<!-- more -->



	
  1. tramite live cd o un'altra distro GNU/Linux (o BSD) effettuiamo il chroot

	
  2. una volta effettuato il chroot controlliamo di essere root con il comando `id -u` (deve restituire il numero 0)

	
  3. creiamo quindi una cartella temporanea con: `mkdir /temp-dir`

	
  4. montiamo il fs root nella cartella appena creata con: `mount -o bind / /temp-dir`

	
  5. entriamo nella cartella dev con: `cd /temp-dir/dev`

	
  6. controlliamo se sono presenti `/dev/null` e `/dev/console` con il comando `ls`

	
  7. se **non** è presente `null` allora diamo` mknod -m 660 null c 3 1`

	
  8. se **non** è presente `console` allora diamo `mknod -m 660 console c 5 1`

	
  9. usciamo dalla cartella con `cd ../..`

	
  10. smontiamo il fs con `umount /temp-dir`

	
  11. e quindi rimuoviamo la cartella con `rmdir /temp-dir`


Alla fine di tutto usciamo dal chroot, riavviamo il PC, selezioniamo Gentoo dal menù di GRUB e...voilà :) tutto funzionante ;)
