---
comments: true
date: 2012-06-12 13:07:49+00:00
layout: post
title: Usare intptr_t in C
categories:
- Generale
- programming
- Unix
tags:
- c
- cast
- programmazione
- puntatori
---

Bisogna stare attenti quando si eseguono i cast in C perchè, a seconda dell'architettura a 32 o 64 bit, avremo un puntatore grande 4 o 8 bytes. Questo rappresenta un problema di portabilità nelle architetture a 64 bit e ora andremo a vedere il motivo.

Prendiamo come esempio questo cast esplicito:
`(void *)num`
esso provocherà un warning nella compilazione (nello specifico questo avviso:  _warning: cast to pointer from integer of different size_) e un molto probabile errore di segmentazione durante l'esecuzione.

Ma perchè accade questo?

<!-- more -->

Semplicemente questo accade perchè un tipo di dato _int_ è grande 4 bytes (sia su 32 e che su 64 bit) mentre un puntatore - come detto sopra - ha un grandezza di 4 o 8 bytes a seconda che la macchina sia a 32 o 64 bit.

In una macchina a 32 bit il cast sopra scritto si può tradurre come: "fai stare i 4 bytes di _int_ nei 4 bytes di _pointer_" e fin qui va bene ma se si esegue quel codice in una macchina a 64 bit è come dire "fai stare i 4 bytes di _int_ negli 8 bytes di _pointer_" e questo è errato in quanto i bytes non possono essere mappati "1 a 1".

Per risolvere tale problema si può usare il seguente metodo che, essendo quello che fornisce una maggiore portabilità, è il più usato.



	
  1. Includere i seguenti headers: _stdint.h_ e _inttypes.h_

	
  2. Dichiarare il dato _num_ con _intptr_t_ in questo modo: `intptr_t num;`

	
  3. Se si necessita di usare _printf_ bisogna formattare l'istruzione nel seguente modo: `printf("Questo è un numero: %" PRIdPTR "n", (intptr_t)(void *)num);`_**
Il casting finale è consigliato per una maggiore portabilità.**_


E questo è quanto :)

Enjoy!
