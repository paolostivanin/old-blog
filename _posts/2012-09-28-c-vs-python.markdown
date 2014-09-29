---
author: pol@blog
comments: true
date: 2012-09-28 17:47:24+00:00
layout: post
slug: c-vs-python
title: C vs Python
wordpress_id: 2015
categories:
- Generale
- Programmazione
- Unix
---

<blockquote>**Premessa:** il codice compilato è più veloce del codice interpreato e, ad oggi, nessuno può affermare il contrario. Il mio "confronto" è una prova personale che ho voluto fare per vedere in modo tangibile quali sono le differenze di tempo tra i due modi di trattare il codice sorgente.</blockquote>


Ultimamente ho avuto modo di sviluppare diversi software in C il che mi ha portato ad ottenere una conoscenza molto buona di questo splendido linguaggio.

Ora però ho deciso di ampliare i miei orizzonti e passare a studiare qualcosa di diverso.

Premesso che già sto studiacchiando dei linguaggi web oriented come PHP, Javascript, JQuery e CSS, la mia intezione ora è quella di dedicarmi a linguaggi più nuovi e, sotto certi punti di vista, più versatili e semplici del C.

La lista iniziale prevedeva tre ottimi linguaggi: C++, Python e Java.

Dopo qualche ora di ricerca ho deciso che **Python** sarebbe stato il linguaggio che meritava il mio studio :D

<!-- more -->

Le ragioni sono molteplici e ora vi riporto quelle mi hanno attratto verso Python fin da subito:



	
  * Python è un linguaggio di programmazione orientato agli oggetti;

	
  * è estensibile tramite **una valanga** di moduli;

	
  * le cose che in C ho trovato complesse, laboriose e lunghe da implementare come SQLite3, GTK+3 e cifratura di files tramite AES256, Twofish, ecc in Python sono molto più semplici e chiare;

	
  * è estremamente versatile:

	
    * può essere usato come linguaggio _client side_ e _server side_;

	
    * può essere usato _"al posto di BASH"_ come linguaggio di scripting nel nostro sistema GNU/Linux;





Ma oltre i pregi ci sono, ovviamente, anche i difetti.

Ora io ho appena iniziato con Python quindi non lo conosco ancora benissimo ma un difetto si nota immediatamente: la velocità.

Essendo un linguaggio interpretato Python (come Java) "soffre" di questo problema.

Ma quanto pesa realmente questo problema? Quanto _"è lenta questa lentezza?"_

Ho voluto effettuare un piccolo test per capire che tempi di esecuzione hanno due semplicissimi programmi scritti uno in Python e uno in C. A voi i risultati :)

Programmino numero 1 (Python): stampa i numeri da 1 a 999:

    
    for i in range(1,1000):
    	print i;


e i tempi di esecuzioni del programma (5 prove):

    
    real 0.025 0.026 0.024 0.022 0.025
    user 0.008 0.020 0.012 0.004 0.012


Programmino numero 1 (C): stampa i numeri da 1 a 999:

    
    for(i=1; i<1000; i++) printf("%d ");


e i tempi di esecuzioni del programma (5 prove):

    
    real 0.002 0.002 0.003 0.002 0.002
    user 0.000 0.000 0.000 0.000 0.000


Programmino numero 2 (Python): stampa i numeri da 1 a 999 ed effettua 'a+i', quindi stampa 'a':

    
    for i in range(1,1000):
    	print i;
    	a+=i;
    print a;


questi sono i tempi di esecuzione (5 prove):

    
    real 0.059 0.028 0.025 0.022 0.023
    user 0.012 0.004 0.012 0.012 0.012


Programmino numero 2 (C): stampa i numeri da 1 a 999 ed effettua 'a+i', quindi stampa 'a':

    
    for(i=1; i<1000; i++){ printf("%d "); a+=i; } printf("%dn", a);


questi sono i tempi di esecuzione (5 prove):

    
    real 0.002 0.003 0.003 0.002 0.002
    user 0.000 0.000 0.000 0.000 0.000


Legenda:****



	
  * **real** = tempo (in secondi) trascorso tra l'invocazione del programma e la sua terminazione;

	
  * **user** = tempo (in secondi) usato dalla CPU in user mode


Come potete notare da questi semplici test se il programma da eseguire fosse un programma complesso la differenza temporale si farebbe certamente sentire ma, d'altra parte, è anche vero che se il tempo e lo spazio non sono fattori critici allora non abbiamo nulla di cui preoccuparci. :)

Ah, un'ultima nota per tutti quelli che dicono/scrivono che C è un linguaggio vecchio, obsoleto, poco potente, ecc ecc:

	
  * il kernel Linux è scritto in C;

	
  * il kernel di Windows è scritto in C;

	
  * il kernel di Mac OS X è scritto in C;

	
  * PHP è scritto in C;

	
  * Python è scritto in C;

	
  * la JVM è scritta in C;

	
  * parte di MySQL è scritta in C;

	
  * la maggior parte dei programmi che usano il toolkit GTK+ sono scritti in C.

	
  * ...vado avanti??? ;)


