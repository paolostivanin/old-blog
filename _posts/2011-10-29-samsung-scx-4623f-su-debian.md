---
comments: true
date: 2011-10-29 14:26:32+00:00
layout: post
title: Samsung SCX-4623F su Debian
---

A causa della rottura della vecchia stampante oggi son dovuto andare a prenderne un'altra.

Dopo svariate ricerche ho optato per una Samsung SCX-4623F (laser :D) anche spinto dal fatto che Samsung offre i driver per GNU/Linux :)

Montata la stampante (che fa anche da fotocopiatrice, scanner e fax) accendo il PC con Debian e provo ad installare i driver forniti da Samsung.

Ovviamente non va mai tutto liscio ed infatti al passaggio "trova scanner" mi dice che non ho le API di SANE installate.

Vado quindi a cercare su Synaptic tutto quello che riguarda sane ma con mio stupore i pacchetti sono già tutti installati O.o

Inizia quindi la ricerca in giro per la grande rete per trovare una soluzione e fortuna vuole che [un'ottima persona, una grandissima persona, un genio, un premio nobel per la semplificazione della vita altrui, ecc ecc](http://www.bchemnet.com/suldr/) abbia fatto un repository per semplificare l'installazione delle stampanti Samsung (e relative funzioni quali scanner) :) :)

Seguendo infatti la semplice guida sopra linkata (che per comodità vostra riporto) ora tutto funziona a meraviglia, ma con una piccola postilla... ;)

<!-- more -->

Partiamo innanzitutto con l'aggiungere il repository scrivendo **da root:**

    
    echo -e "n# Stampante Samsungndeb http://www.bchemnet.com/suldr/ debian extra" | tee -a /etc/apt/sources.list
    wget -O - http://www.bchemnet.com/suldr/suldr.gpg | apt-key add -


Ed ora installiamo tutto il necessario con:

    
    sudo apt-get install samsungmfp-driver samsungmfp-data samsungmfp-scanner


Ora andiamo su_ Sistema --> Amministrazione --> Stampa_ ed aggiungiamo la stampante seguendo il wizard :)

**_Postilla:_**_i p_er lo scanner invece **bisogna installare XSane** in quanto con Simple Scan non funziona (non chiedetemi perchè dato che entrambi usano SANE come backend...mah xD)

Enjoy :)
