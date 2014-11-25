---
comments: true
date: 2008-07-07 09:45:27+00:00
layout: blog
title: Comandi utili Shell Bash
categories:
- Unix
---

Prima di passare alla guida su come compilare il kernel a mano, è utile sapere cosa sono i comandi che vengono scritti, a cosa servono e quando usarli!

**QUESTI COMANDI VANNO BENE PER QUASI TUTTE LE DISTRO LINUX (mandriva, fedora, debian, sidux, arch, slackware, elive, opengeu, gentoo, foresight, ecc ecc)!**

Allora, con calma, partiamo!

Il comando **cd** serve per spostarsi all'interno delle directory del filesystem. La sintassi del comando è la seguente:

`cd [directory]`

Alcuni esempi di uso del comando:



	
  * `cd .. ` Serve per spostarsi alla directory superiore.

	
  * `cd` Serve per spostarsi, da qualsiasi punto, alla propria directory home. È equivalente a: `cd ~`

	
  * `cd _/etc_` Serve per spostarsi nella directory _/etc_


Il comando **mkdir** serve per creare directory all'interno del filesystem.  La sintassi del comando è:

`mkdir [opzioni] directory`

Alcuni esempi di uso del comando **mkdir**:



	
  * `mkdir _prova_` Verrà creata la directory _prova_ all'interno della directory in corrente.

	
  * `mkdir -p /prova1/bin` In questo modo verranno create tutte le directory comprese nel percorso, anche se la prima directory specificata non esiste.


Il comando **cp** serve per:



	
  * copiare un file in un altro file cp

	
  * copiare un file in un'altra directory cp

	
  * copiare più file in un'altra directory

	
  * copiare directory


La sintassi del comando è la seguente:

`cp [opzioni] origine destinazione`

Alcune opzioni da utilizzare con il comando **cp**:



	
  1. **-b** esegue automaticamente una copia di backup di ogni file di destinazione esistente

	
  2. **-f** forza la sovrascrittura dei file, senza richiedere interventi da parte dell'utente

	
  3. **-i** attiva la modalità interattiva, che chiede conferma prima dell'eventuale sovrascrittura di file preesistenti

	
  4. **-p** mantiene, se possibile, gli attributi del file

	
  5. **-r** permette di attivare la modalità ricorsiva, consentendo la copia di directory

	
  6. **-v** attiva la modalità "verbose", visualizza ciò che il sistema ha fatto in seguito al comando


Alcuni esempi di uso del comando **cp**:



	
  * `cp /prova/miofile /prova1`
Copia il file _miofile_ della directory _prova_ nella directory _/prova1_.

	
  * `cp /prova/miofile /prova1/nuovofile`
Copia il file _miofile_ della directory _/prova_ nella directory _/prova1_ dandogli il nome _nuovofile_.

	
  * `cp -r /prova /prova_copia`
Copia la cartella _/prova_, e tutto il suo contenuto, nella cartella _/prova_copia_.


Il comando **mv** serve per spostare, o rinominare, file e directory.  La sintassi del comando è la seguente:

`mv [opzioni] origine destinazione`

Le opzioni sono le stesse del comando **cp**. Alcuni esempi di uso del comando **mv**:



	
  * `mv miofile nuovofile`
Cambierà il nome al file _miofile_ in _nuovofile_.

	
  * `mv miofile /prova`
Sposterà il file _miofile_ nella directory _/prova_ sovrascrivendo un eventuale file con lo stesso nome.

	
  * `mv /prova /prova_nuova`
Cambierà il nome alla directory _/prova_ in _/prova_nuova_.


Il comando **rm** serve per cancellare file o directory dal file system.  La sintassi del comando è la seguente:

`rm [opzioni] file `

Alcune opzioni da utilizzare con il comando **rm**:



	
  1. **-i** chiede conferma prima di cancellare

	
  2. **-f** forza la cancellazione del file senza chiedere conferma

	
  3. **-r** abilita la modalità ricorsiva usata per la cancellazione delle directory


Il comando **uname** mostra informazioni sul sistema. La sintassi è la seguente:

`uname [opzione]`

Le varie opzioni sono:



	
  1. **-a** Visualizzerà tutte le informazioni del sistema

	
  2. **-m** Mostra il tipo di macchina

	
  3. **-n** Mostra il nome host del nodo di rete della macchina

	
  4. **-s** Mostra il nome del sistema operativo

	
  5. **-r** Mostra la release del sistema operativo


I comandi **cat** e **less** servono per mostrare il contenuto di un file:



	
  * **cat** mostra semplicemente il contenuto del file specificato,

	
  * **less** visualizza il contenuto di file, permette di spostarsi avanti e indietro nel testo utilizzando i tasti freccia quando i file occupano più di una pagina di schermo. È inoltre possibile eseguire delle ricerche nel testo digitando _/_ seguito dalla parola da cercare e premendo **Invio**. Per terminare il programma premere il tasto **q**.


La sintassi del comando **cat** è la seguente:

`cat nomefile`

La sintassi del comando **less** è la seguente:

`less nomefile`

Il comando **ln** serve a creare un collegamento (link) ad un file o una directory. Un collegamento è un file speciale che non contiene dati, ma solo un riferimento ad un altro file: ogni operazione effettuata sul collegamento viene in realtà eseguita sul file a cui punta. La sintassi del comando **ln** è la seguente:

`ln -s /percorso_file_da_collegare/file_da_collegare /percorso_del_collegamento/nome_del_collegamento`

L'opzione **-s** specifica che verrà creato un collegamento simbolico: è raccomandato usare **-s**.
Per maggiori informazioni sul comando **ln** digitare:

`man ln`

**Per estarre i file .tar.X** esistono svariati comandi, a seconda dell'estensione:

Se l'archivio è** .tar.bz2**, allora si darà:

`sudo tar xjvf file.tar.bz2`

Se l'archivio è **.tar.gz**, allora sarà:

`sudo xvfz file.tar.gz`

Alcune info utili:

`-f` (specifica un file da estrarre o da creare)
`-x` (estrae un archivio)
`-t` (permette di mostrare il contenuto degli archivi)
`-v` (dà  in output maggiori informazioni sui file compressi o decompressi)

Nota:** **tar serve solo ad archiviare, non riduce lo spazio occupato dai file; al contrario gzip e bzip2 comprimono ma non archiviano; **combinandone l’uso è possibile archiviare comprimendo** (basta aggiungere una _z_, gzip, o _j_, bzip2, alle opzioni del comando tar).
