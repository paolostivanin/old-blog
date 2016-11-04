---
comments: true
date: 2011-05-05 21:00:35+00:00
layout: post
title: Nerdate in BASH!
---

Il modo migliore per ricordarsi quando sono gli esami?

A mio parere è scriverselo sul calendario :)

Ma se non avete la possibilità di farlo allora uno script in BASH può risolvere ogni vostro problema!

[gallery]

Certo ci vorrà qualche minuto in più rispetto al primo metodo ma il risultato è più comodo e stiloso anche se questo sta a voi constatarlo :)

Se lo volete usare anche voi ricordatevi di sostituire le varie variabili ;)

    
    #!/bin/bash
    
    fisica="scrivi-giorno"
    fisica1="scrivi-giorno"
    fisica2="scrivi-giorno"
    
    continuo="scrivi-giorno"
    continuo1="scrivi-giorno"
    continuo2="scrivi-giorno"
    continuop2="scrivi-giorno"
    continuop2_1="scrivi-giorno"
    continuop2_2="scrivi-giorno"
    
    stat="scrivi-giorno"
    stat_1="scrivi-giorno"
    stat_2="scrivi-giorno"
    
    disc="scrivi-giorno"
    disc_1="scrivi-giorno"
    disc_2="scrivi-giorno"
    
    scelta_1=$(zenity  --width=80 --height=160 --list --title "Info" --text "Scegli se vuoi visualizzare la date per esame o per mese" --radiolist  --column "Scelta" --column "Tipo" TRUE Esame FALSE Mese)
    
    if [ "$scelta_1" == "Esame" ] ;then
    
    scelta=$(zenity  --width=170 --height=255 --list --title "Esami 2^ semestre" --text "Scegli l'esame di cui vuoi conoscere le date degli appelli della sessione estiva" --radiolist  --column "Scelta" --column "Esame" TRUE Continuo-P1 FALSE Continuo-P2 FALSE Discreto-P2 FALSE Fisica FALSE Statistica FALSE Programmazione)
    
    if [ "$scelta" == "Programmazione" ] ; then
       zenity --info --text "È ancora un appello oscuro..."
     else
          if [ "$scelta" == "Continuo-P1" ] ; then
             zenity --info --title "Info" --text "Gli appelli di $scelta sono:
    
    $continuo
    $continuo1
    $continuo2"
       else
              if [ "$scelta" == "Continuo-P2" ] ; then
    	     zenity --info --title "Info" --text "Gli appelli di $scelta sono:
    
    $continuop2
    $continuop2_1
    $continuop2_2"
         else
    	      if [ "$scelta" == "Discreto-P2" ] ; then
    	         zenity --info --title "Info" --text "Gli appelli di $scelta sono:
    
    $disc
    $disc_1
    $disc_2"
           else
    	          if [ "$scelta" == "Fisica" ] ; then
    		     zenity --info --title "Info" --text "Gli appelli di $scelta sono:
    
    $fisica
    $fisica1
    $fisica2"
             else
                          if [ "$scelta" == "Statistica" ] ; then
    		         zenity --info --title "Info" --text "Gli appelli di $scelta sono:
    
    $stat
    $stat_1
    $stat_2"
    		      fi
                      fi
                  fi
              fi
          fi
    fi
    
    else
    scelta_2=$(zenity  --width=130 --height=200 --list --title "Info" --text "Scegli il mese" --radiolist  --column "Scelta" --column "Mese" TRUE Giugno FALSE Luglio FALSE Settembre)
    if [ "$scelta_2" == "Giugno" ] ; then
    	zenity --info --title "Info" --text "Gli appelli di $scelta_2 sono:
    FISICA:      $fisica
    CONTINUO P1: $continuo
    CONTINUO P2: $continuop2
    DISCRETO P2: $disc
    STATISTICA:  $stat"
    
    else if [ "$scelta_2" == "Luglio" ] ; then
    	zenity --info --title "Info" --text "Gli appelli di $scelta_2 sono:
    FISICA:      $fisica1
    DISCRETO P2: $disc_1
    CONTINUO P1: $continuo1
    CONTINUO P2: $continuop2_1
    STATISTICA:  $stat_1"
    else if [ "$scelta_2" == "Settembre" ] ; then
    zenity --info --title "Info" --text "Gli appelli di $scelta_2 sono:
    STATISTICA:  $stat_2
    DISCRETO P2: $disc_2
    CONTINUO P1: $continuo2
    CONTINUO P2: $continuop2_2
    FISICA:      $fisica2"
    fi
    fi
    fi
    fi




Enjoy! :)
