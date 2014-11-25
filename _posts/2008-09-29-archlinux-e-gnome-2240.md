---
comments: true
date: 2008-09-29 08:30:16+00:00
layout: blog
title: ArchLinux e Gnome 2.24.0
categories:
- ArchLinux
- Unix
---

Ciao a tutti e buona settimana!

L'altro giorno ho ri-abilitato **i repo testing su Arch**, perchè sono troppo curioso di provare **Gnome 2.24**!

Ma, dopo le ultime 2 formattazioni, ho deciso che sto giro dovevo disabilitare l'aggiornamento di xorg, synaptics, intel, vesa.

Ma come?

Semplice, aprite il terminale da root e scrivete:


`nano /etc/pacman.conf`



e scorrendo le righe troverete questo:


# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup
#IgnorePkg   =
#IgnoreGroup =

Bene, decommentiamo IgnorePkg (togliamo #) e scriviamo cosa NON vogliamo venga aggiornato, nel mio caso così:


# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup
IgnorePkg   = xorg-server xf86-video-vesa xf86-video-intel xf86-input-synaptics
#IgnoreGroup =

Ecco fatto, ora siamo pronti ad aggiornare :D

Accediamo al terminale da root e scriviamo:


`pacman -Sfyu` **(l'opzione _f_ (_force)_, si usa perchè bisogna sostituire pacchetti già esistenti)**



e attendiamo!

Alla fine avremo il nostro Gnome 2.24 castrato, questo perchè stanno ancora pacchettizzando i nostri amici DEV :D

Speriamo facciano in fretta perchè sono proprio curioso :D

Ovviamente, essendo in testing, alcuni problemi (non gravi, il computer funziona alla perfezione) si riscontrano, come ad esempio: il monitor sistema non va (ma è ancora la versione 2.22.3), gconf-editor ha dei problemi, è tutto dovuto al fatto che il sistema è a metà XD

Bene bene, attenderò impaziente che vegna pacchettizzato tutto così vedrò tutti i miei problemi sparire :D

[![](http://www.allfreeportal.com/imghost/thumbs/529183Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=529183Schermata.png)

[![](http://www.allfreeportal.com/imghost/thumbs/460311Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=460311Schermata-1.png)

[![](http://www.allfreeportal.com/imghost/thumbs/15170Schermata-2.png)](http://www.allfreeportal.com/imghost/viewer.php?id=15170Schermata-2.png)

