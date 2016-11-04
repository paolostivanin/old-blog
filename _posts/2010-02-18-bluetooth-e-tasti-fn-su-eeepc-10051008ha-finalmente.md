---
comments: true
date: 2010-02-18 14:08:12+00:00
layout: post
title: Bluetooth e tasti FN su Eeepc 1005/1008HA...finalmente!
categories:
- ArchLinux
- Ubuntu
- Unix
---

Dopo giorni di ricerca sfrenata e di iscrizioni a millemila forum sono riuscito a far ripartire:



	
  * il bluetooth

	
  * i tasti FN


YUPPIIIIIIIIIIIIIIIIIIII :D :D :D

Se si ha **GRUB2** Per risolvere questi 2 problemi basta editare il file _/etc/default/grub _in questo modo:


`sudo gedit /etc/default/grub`


Ora fra le prime righe c'è questa:


`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`


che deve diventare:


`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"`


Perfetto, salviamo e aggiorniamo Grub:


`sudo update-grub`


Olè problema (finalmenteeeeeeeeeee) risolto :)

Se invece si ha Grub-0.97 basta editare il file menu.lst


`sudo gedit /boot/grub/menu.lst`



e aggiungere la riga acpi_osi=Linux di fianco a ro quiet in questo modo:


`kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/f9460e30-8018-4dfe-8fba-a32c7ee53a7c rootfstype=ext4 ro quiet acpi_osi=Linux`


**PS: notare che Linux va con la L e non con la l** ;)
