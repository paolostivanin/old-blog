---
comments: true
date: 2012-03-28 20:21:48+00:00
layout: post
title: Eseguire script al plug/unplug del cavo AC
categories:
- ArchLinux
- Unix
---

A causa di un bug sono costretto a ricorrere ad un mio script per fare in modo che il sistema riconosca il cavo "unplugged" quando è disinserito o "plugged" quando è inserito.

Per un po' ho vissuto con il metodo di cliccare sullo script quando inserivo o rimuovevo il cavo ma poi mi sono stufato e ho preferito cercare una soluzione che rendesse automatico il tutto.

Per fare ciò per prima cosa editiamo il file _lm_batter.sh_:

    
    sudo nano /etc/acpi/lm_battery.sh


quindi inseriamo il percorso allo script BASH preceduto da uno _sleep 3_ (questo per evitare che "succeda tutto troppo in fretta e il sistema non si accorga del cambiamento"):

    
    sleep 3
    /home/$USER/myscript.sh


Enjoy :)


