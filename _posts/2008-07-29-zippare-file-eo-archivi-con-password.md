---
comments: true
date: 2008-07-29 12:10:27+00:00
layout: blog
title: Zippare file e/o archivi con password!
categories:
- Generale
---

Oggi mi son trovato in fronte la necessità di creare un archivio protetto da password con dentro dei file molto importanti.

Accendo il pc e...cavolo non so come fare!

Allora prendi, cerca, metti insieme le info che trovi e comincia a smanettare per vedere come funziona!

Detto ciò vi comunico che il metodo è testato per:

**Debian e derivate (xu/k/u/buntu, mint, ecc), Arch Linux.**



	
  * Debian e simili:


`sudo apt-get install zip`



	
  * Arch:


`pacman -Sy zip`



	
  * Il comando generale è:


`zip [OPZIONI] [NOME-ARCHIVIO-CHE-SI-VUOLE-DARE.zip] [NOME-REALE-ARCHIVIO E/O FILE]`

La cosa bella è che, se zippate con password un archivio, non si può nemmeno vedere cosa c'è dentro finchè non si mette la password!

Allora, prendiamo in esame un cartella che si trova nella SCRIVANIA e che si chiama _pol-cartella_ e supponiamo di doverla **zippare con password**.

`cd Scrivania`

`zip -er ciufciuf.zip pol-cartella`

Ci chiederà poi la password che vorremmo inserire, la inseriamo ed ecco fatto!

**Abbiamo creato un archivo .zip protetto da password!** :D

Ecco un tabella coi comandi disponibili:
<table border="1" >
<tbody >
<tr >

<td >f   freshen: solo i file cambiati
</td>

<td >-u   update: solo cambiamenti o nuovi file
</td>

<td >-d   cancella le entrate nei file zip
</td>

<td >-m   muove nell zipfile (cancella files)
</td>
</tr>
<tr >

<td >-r   ricorsivo nella directory (ovvero crea l'archivio zip con il contenuto della cartella)
</td>

<td >-j


junk (non registrano) I nomi delle directory

</td>

<td >-0   solo archiviazione
</td>

<td >-l   converte LF in CR LF (-ll CR LF to LF)
</td>
</tr>
<tr >

<td >-1   compressione veloce
</td>

<td >-9   compressione migliore
</td>

<td >-q   operazione calma
</td>

<td >-v   scrive l'operazione/mostra info versione
</td>
</tr>
<tr >

<td >-c   aggiunge una linea di commento
</td>

<td >-z   aggiunge uno zipfile di commento
</td>

<td >-@   legge i nomi da stdin
</td>

<td >-o   crea uno zipfile vecchio come l'ultima entrata
</td>
</tr>
<tr >

<td >-x   esclude i seguenti nomi
</td>

<td >-i  include solo i seguenti nomi
</td>

<td >-F   fissa uno zipfile (-FF try harder)
</td>

<td >-D   non aggiugne il nome delle directory
</td>
</tr>
<tr >

<td >-A   aggiusta gli autoestraenti exe
</td>

<td >-J   junk il prefisso dei zipfile (unzipsfx)
</td>

<td >-T   controlla l'integrità dello zipfile
</td>

<td >-X   esclude gli attributi extra dei file
</td>
</tr>
<tr >

<td >-y


memorizzare link simbolici come link al posto del file di riferimento

</td>

<td >-R   PKZIP recursivo (vedi manuale)
</td>

<td >-e  cripta
</td>

<td >-n   non comprime i seguenti suffissi
</td>
</tr>
</tbody></table>
**Ecco uno screen d'aiuto:**

[![](http://www.allfreeportal.com/imghost/thumbs/741553Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=741553Schermata.png)
