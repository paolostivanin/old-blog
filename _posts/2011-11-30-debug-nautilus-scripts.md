---
comments: true
date: 2011-11-30 11:12:49+00:00
layout: post
title: Debug Nautilus Scripts
---

Se avete un _nautilus-script_ e avete bisogno di effettuarne il debug ma non sapete come fare, questa semplice soluzione vi sarà (molto) d'aiuto :)

Aprite il vostro script con un editor di testo qualsiasi (testuale o meno decidete voi ;)) e aggiungete queste righe:

    
    #!/bin/bash -x
    (
    #VOSTRO SCRIPT
    ) &>/home/$USER/script_debug



Spiegazione veloce:



	
  * -x abilita il debugging

	
  * &> redirecta sia lo stdout che lo stderr (fd1 e fd2) sul file script_debug che verrà creato nella vostra $HOME


Enjoy :)
