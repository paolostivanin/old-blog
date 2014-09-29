---
comments: true
date: 2013-01-04 13:00:43+00:00
layout: post
title: Aggiungere funzioni al file .bashrc
categories:
- ArchLinux
- Debian &amp; Co
- Gentoo
- programming
- Ubuntu
- Unix
tags:
- c
- gtk3
---

Per compilare i programmi che necessitano delle librerie GTK+ versione 3 e maggiori è necessario passare a GCC il parametro `pkg-config --cflags --libs gtk+-3.0` che si occupa di trovare ed elencare le librerie necessarie.

<!-- more -->



Giusto per informazione l'output del comando sopra scritto è:


`-pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/pixman-1 -I/usr/include/libpng12 -lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo -lgobject-2.0 -lglib-2.0
`


Per evitare di dover scrivere il parametro `pkg-config --cflags --libs gtk+-3.0` (o il suo output) ad ogni esecuzione di GCC è necessario modificare il file `.bashrc` presente all'interno della nostra `$HOME` aggiungendo le seguenti righe:


`gtkcc() {
NAME=$1
INPUT=$2
PARAM="-Wall -Wextra -O2 -D_FORTIFY_SOURCE=2"
gcc $PARAM -o $NAME $INPUT $(pkg-config --cflags --libs gtk+-3.0)
}`


Una volta salvato il file o si chiude e si riapre il terminale oppure si esegue **non da root **il comando: `cd /home/$USER && source .bashrc`

Per usare questa nuova funziona basta quindi scrivere


`gtkcc $nome_file_output $nome_file_input.c`
