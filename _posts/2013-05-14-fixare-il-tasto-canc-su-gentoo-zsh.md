---
comments: true
date: 2013-05-14 20:47:30+00:00
layout: blog
title: Fixare il tasto Canc su Gentoo + ZSH
category: blog
tags: [gentoo, shell, zsh]
---

L'altro giorno ho cambiato la shell di default da Bash a Zsh e ho riscontrato un piccolo problema che mi impediva di utilizzare in modo corretto il tasto Canc nel terminale.
Girovagando qua e là ho scoperto che basta inserire queste righe:


    bindkey "^[[3~" delete-char
    bindkey "^[3;5~" delete-char


nel file .zshrc e tutto si risolve ;-)
