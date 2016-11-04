---
comments: true
date: 2012-10-18 09:56:15+00:00
layout: post
title: 'Dropbox: GLIBCXX_3.4.11 not found'
---

Avviando Dropbox da terminale mi sono accorto che ottenevo questo avviso:

`$ dropbox start
Starting Dropbox.../var/lib/dropbox/.dropbox-dist/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libproxy.so.1)
Failed to load module: /usr/lib/x86_64-linux-gnu/gio/modules/libgiolibproxy.so
Done!`

Andando ad analizzare la libreria `libstdc++.so.6` fornita da Dropbox mi sono accorto del perchè di questo avviso:

<!-- more -->

`$ strings /var/lib/dropbox/.dropbox-dist/libstdc++.so.6 | grep GLIBC
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBC_2.3
GLIBC_2.4
GLIBC_2.2.5
GLIBCXX_FORCE_NEW`

Come potete vedere manca la stringa GLIBCXX_3.4.11.

Eseguendo questo controllo anche sulla libreria presente all'interno del sistema ottengo un output diverso dal precedente nonchè utile alla risoluzione dell'avviso sopra scritto:

`$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBC
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
**GLIBCXX_3.4.11**
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBC_2.2.5
GLIBC_2.3
GLIBC_2.14
GLIBC_2.4
GLIBC_2.3.4
GLIBC_2.3.2
GLIBCXX_DEBUG_MESSAGE_LENGTH`

Per risolvere questo piccolo bug basta quindi eliminare la libreria fornita da Dropbox e successivamente creare un link simbolico alla libreria presente nel nostro sistema tramite questi comandi:

`sudo rm /var/lib/dropbox/.dropbox-dist/libstdc++.so.6
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /var/lib/dropbox/.dropbox-dist/libstdc++.so.6`

_PS: attenzione che se avete un sistema un sistema** 32 bit** dovete sostituire_ `x86_64-linux-gnu` _con_ `i386-linux-gnu`
