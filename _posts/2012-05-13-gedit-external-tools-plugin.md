---
comments: true
date: 2012-05-13 10:24:55+00:00
layout: post
title: GEdit External Tools Plugin
---

Qualche giorno fa, mentre stavo sviluppando un progettino in C/GTK+3, ho avuto la necessità di voler compilare "al volo" il codice e, dato che uso GEdit, ho abilitato e configurato un plugin veramente interessante e potente che mi ha permesso di associare alcune scorciatoie a dei comandi prestabiliti da me :)

In particolare ho associato la scorciatoia CTRL+F9 per compilare semplici programmi in C _(quindi senza linkare altre librerie tipo -lm, -lcrypto, ecc)_ e CTRL+F10 per compilare programmi in C/GTK+3.

Vediamo passo passo come fare :)

<!-- more -->

1. Abilitare il plugin _"Strumenti Esterni"_ da _Modifica -> Preferenze -> Plugin_:

[caption id="attachment_1855" align="aligncenter" width="300"][![Abilitare Plugin]({{ site.baseurl }}/images/2012/05/plugin1-300x23.png)]({{ site.baseurl }}/images/2012/05/plugin1.png) Abilitare Plugin[/caption]

2. Andare su _Strumenti -> Manage External Tools_ per accedere alla configurazione del plugin:

[caption id="attachment_1858" align="aligncenter" width="300"][![Configurazione External Tools]({{ site.baseurl }}/images/2012/05/strumenti1-300x171.png)]({{ site.baseurl }}/images/2012/05/strumenti1.png) Configurazione External Tools[/caption]

3. Aggiungere i comandi che vi interessano. Per fare ciò basta cliccare sul + in basso a sinistra:

[caption id="attachment_1859" align="aligncenter" width="300"][![Script per compilare programmi C]({{ site.baseurl }}/images/2012/05/c1-300x249.png)]({{ site.baseurl }}/images/2012/05/c1.png) Script per compilare programmi C[/caption]

[caption id="attachment_1860" align="aligncenter" width="300"][![Script per compilare programmi C/GTK+3]({{ site.baseurl }}/images/2012/05/gtk31-300x247.png)]({{ site.baseurl }}/images/2012/05/gtk31.png) Script per compilare programmi C/GTK+3[/caption]

Andiamo ad analizzare in dettagli i vari campi.

_Tasto Scorciatoia:_ una volta cliccato in quel campo basta premere i tasti della scorciatoia da tastiera desiderata

_Salva:_ scegliere se salvare o meno il documento corrente o tutti i documenti aperti prima di eseguire lo script

_Input:_ scegliere cosa dare come input allo script (niente, il file corrente, una selezione, una parola selezionata, ecc)

_Output:_ scegliere cosa fare dell'output prodotto (visualizzarlo in un pannello che si aprirà in fondo allo schermo, salvare l'output su un file, sostituire una selezione, ecc)

_Applicabilità:_ scegliere a che documento applicare lo script (ai soli documenti salvati, a tutti i documenti, ai documenti locali o remoti, ecc) e anche a che tipo di documento applicare tale script (C, C++, Ada, Fortran, F#, DOS, ecc)

Ovviamente nel caso di decidesse di impostare un comando per compilare (per esempio GCC) e il campo "Salva" viene lasciato su _"Niente"_ è **obbligatorio** mettere come _"Applicabilità"_ la voce _"Solo ai documenti salvati"_.

Ora non resta che analizzare le voci da scrivere all'interno dello script.

    
    #!/bin/sh
    
    dir=$GEDIT_CURRENT_DOCUMENT_DIR
    file=$GEDIT_CURRENT_DOCUMENT_NAME
    out_file=$(basename $file .c)
    gcc -Wall -g -O1 -o ${dir}/${out_file} ${dir}/${file}


La prima e la seconda riga contengono delle variabili d'ambiente che vogliono dire rispettivamente _"Percorso completo della directory in cui si trova il file"_ e _"Nome del file attualmente aperto"_. Altre variabili d'ambiente che possono essere usate sono:



	
  * GEDIT_CURRENT_DOCUMENT_URI

	
  * GEDIT_CURRENT_DOCUMENT_SCHEME

	
  * GEDIT_CURRENT_DOCUMENT_PATH

	
  * GEDIT_DOCUMENTS_URI

	
  * GEDIT_DOCUMENTS_PATH


La terza riga contiene il nome del file che produrrà GCC (con il suffisso ".c" dico a _basename_ di prendere il nome del file e togliere l'estensione ".c").

Infine la quarta riga contiene il comando GCC con le varie opzioni _(-Wall per abilitare tutti gli avvisi, -g produce informazioni di debug nel formato nativo del sistema operativo e -O1 indica il livello di ottimizzazione, ndr)_

E questo, per quanto riguarda le opzioni, è tutto. Ora manca solo il risultato :)

Infatti con le mie impostazioni il risultato finale, una volta salvato il file e premuto CTRL+F10, è:

[caption id="attachment_1861" align="aligncenter" width="300"][![Risultato Esecuzione Script]({{ site.baseurl }}/images/2012/05/risultato1-300x171.png)]({{ site.baseurl }}/images/2012/05/risultato1.png) Risultato Esecuzione Script[/caption]


