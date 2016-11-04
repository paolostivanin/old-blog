---
comments: true
date: 2012-07-20 12:53:12+00:00
layout: post
title: 'Errore durante la compilazione: GCC Vs Clang'
---

Una cosa molto importante per un programmatore è che il compilatore fornisca un output dettagliato e chiaro in caso di errore in modo da poter facilmente capire il perchè è successo e come risolvere il problema.

Analizziamo ora l'output di due errori volutamente commessi:

<!-- more -->

[caption id="attachment_1960" align="aligncenter" width="300"][![]({{ site.baseurl }}/images/2012/07/gcc-error1-300x192.png)]({{ site.baseurl }}/images/2012/07/gcc-error1.png) Dichiarazione errata della funzione printf (GCC)[/caption]

[caption id="attachment_1961" align="aligncenter" width="300"][![]({{ site.baseurl }}/images/2012/07/clang-error1-300x190.png)]({{ site.baseurl }}/images/2012/07/clang-error1.png) Dichiarazione errata della funzione printf (Clang)[/caption]

[caption id="attachment_1962" align="aligncenter" width="300"][![]({{ site.baseurl }}/images/2012/07/gcc-error21-300x190.png)]({{ site.baseurl }}/images/2012/07/gcc-error21.png) ";" non messo alla fine dell'istruzione (GCC)[/caption]

[caption id="attachment_1963" align="aligncenter" width="300"][![]({{ site.baseurl }}/images/2012/07/clang-error21-300x190.png)]({{ site.baseurl }}/images/2012/07/clang-error21.png) ";" non messo alla fine dell'istruzione (Clang)[/caption]

Personalmente Clang mi ha colpito per la sua chiarezza nel fornire "il dove" si è presentato l'errore_ (stampa anche la freccia verde per dirti il punto esatto)_ quindi, data l'ottima impressione che mi ha dato, lo userò come compilatore predefinito per tutti i miei progetti in C :)
