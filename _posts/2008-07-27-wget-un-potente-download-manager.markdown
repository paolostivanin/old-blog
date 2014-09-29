---
comments: true
date: 2008-07-27 11:00:00+00:00
layout: post
title: Wget, un potente download manager!
categories:
- Unix
---

Oggi si parla di questo stupendo software: **WGET**! Chi di voi non lo hai mai sentito nominare??

Male se non l'avete mai sentito, anzi molto male ;-)

**WGET** è un download manager a riga di comando veramente potente!

Altro che tutti quei ciccì-coccò con grafica tanto bella e che poi non fanno niente XD

Ecco una breve guida con i comandi principali:

**Comando base:** Il comando di base per scaricare solo un file quando abbiamo un link diretto è

wget http://PERCORSO-FILE
**
Recupero di un download interrotto:** Se il download è stato interrotto, non è un problema basta un comando per far ripartire il download dal punto di arresto

wget -c http://PERCORSO-FILE

**Limite di velocità:** Non molto utilizzato, ma nel caso avete l’esigenza di diminuire la velocità del download basta digitare questo comando

wget --limit-rate=20k (mette il valore che volete, il k sta per kilobyte)

**File di Log:** La via migliore per sapere se qualcosa è andata male è salvare l’output in un file di log in questo modo

wget -o $HOME/log.txt
**
Background:** Se siete occupati a lavorare con la linea di comando e non volete attendere che wget finisca il download è eseguire il processo in background:

wget -b http://PERCORSO-FILE
**
Rinominare:** Per scaricare il file con un altro nome basta aggiungere questo paramentro

wget -O nome_file

**Scaricare l'index del sito:**

wget http://polslinux.wordpress.com/

** Scaricare l'index completo con immagini:**

wget -r http://polslinux.wordpress.com/

** Le altre opzioni importanti del comando sono:**

-p (seguito da una directory) scarica nella directory specificata dopo -p.

**Per salvare i dati nella directorty "MIA" specificata dal comando -p:**

wget -p ~/MIA http://polslinux.wordpress.com/

**Scaricare solo alcuni file:**

-A (seguito dalle estensioni dei file separate da virgole) scarica solo i file di estensione specificata dopo -A.

wget -r -A gif,jpg http://polslinux.wordpress.com/
scarica dal sito specificato solo i file di estensione gif e jpg.

**Escludere alcuni file:**

-R (seguito dalle estensioni dei file separate da virgole) non scarica i file di estensione specificata dopo -R. Volendo dopo -R si può specificare il nome di una directory racchiusa tra due *.

wget -r -R gif,jpg http://polslinux.wordpress.com/
scarica l’index ed i relativi link escludendo i file di estensione gif e jpg.

wget -r -R “*foto*” http://polslinux.wordpress.com/
scarica l’index ed i relativi link escludendo la directory “foto”.

**Altri comandi:**

-t (seguita da un numero) indica il numero di tentativi che wget esegue per scaricare. 0 consentire al programma di tentare un numero infinito di volte l’operazione di download.

-i (seguito dal nome di un file) legge una lista di url dal file specificato.

-c fa il resume del download, riprende a scaricare un download parziale.

-k converte i link da assoluti a relativi per visualizzare la pagina offline.

-N non scarica file più vecchi di quelli locali.

-nq evita di scaricare link che fanno riferimento ad altri siti.

-nc evita di scaricare i file già esistenti.

-nd non crea directory.

wget -r -l 1 -Q5m -D http://polslinux.wordpress.com/
Scarica solo 5 Mb di file dall’indirizzo specificato.

Ecco, spero che questa piccola ma (ri-spero) esauriente guida vi sia d'aiuto e ricordate, WGET è un bellissimo, comodissimo e potentissimo strumento, adatto ad ogni necessità!

Io vi consiglio di usarlo sempre (quando necessario ovviamente) e vi assicuro, non resterete delusi :D
