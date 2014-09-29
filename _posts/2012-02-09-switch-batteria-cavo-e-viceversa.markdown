---
author: pol@blog
comments: true
date: 2012-02-09 10:42:03+00:00
layout: post
slug: switch-batteria-cavo-e-viceversa
title: Switch batteria -> cavo e viceversa!
wordpress_id: 1815
categories:
- ArchLinux
- Debian &amp; Co
- Ubuntu
- Unix
---

Il mio notebook ha dei problemi con UDev/Upower in quanto quando inserisco o tolgo il cavo il gestore alimentazione non mi riconosce questi eventi.

È un problema che ho riscontrato su Ubuntu, Debian, Gentoo ed Archlinux e quindi con svariate versione di UDev/Upower ma sono finalmente riuscito a trovare una soluzione per questo fastidioso bug :)

Se anche voi siete afflitti da questo problema vi basterà creare uno script:

    
    nano -w /home/$USER/SwitchBattery.sh


contenente il seguente codice (se usi **YAD**):

    
    #!/bin/bash
    pass=$(yad --class="GSu" 
    --title="Password" 
    --text="Enter '$USER' password:" 
    --image="dialog-password" 
    --entry --hide-text --separator="")
    if [ $? != 0 ];then
    exit 0
    fi
    echo $pass | sudo -S udevadm trigger --subsystem-match=power_supply &>/dev/null


oppure il seguente (se usi **Zenity**):

    
    #!/bin/bash
    pass=$(zenity 
    --title="Password" 
    --text="Enter '$USER' password:" 
    --entry --hide-text)
    if [ $? != 0 ];then
    exit 0
    fi
    echo $pass | sudo -S udevadm trigger --subsystem-match=power_supply &>/dev/null


oppure questo se non vuoi inutili** "fronzoli"**:

    
    #!/bin/bash
    echo "Inserisci PWD:"
    read -rs pass
    echo $pass | sudo -S udevadm trigger --subsystem-match=power_supply &>/dev/null


Infine rendiamo eseguibile il file con:

    
    chmod +x /home/$USER/SwitchBattery.sh




PS: su Archlinux ho dovuto modificare il file sudoers per permettere all'utente non root di eseguire quel comando. Se vi interessa basta procedere in questo modo:


`su
visudo`


E ho quindi aggiunto questa riga:


`%wheel ALL=(ALL) /usr/bin/udevadm`




Enjoy:D
