---
comments: true
date: 2008-06-10 17:42:33+00:00
layout: post
title: Tips & Tricks
categories:
- Ubuntu
---

In questo topic vi insegnerò un trucco per abbreviare i comandi da dare nel terminale quando dobbiamo fare qualcosa!

Allora, innanzitutto digitiamo nel terminale:
`
sudo gedit  ~/.bashrc`

(Questo affare qui --> **~** si ottiene premendo PAG-giù nel terminale)

E si apre un file di testo, andiamo nella parte in cui ci sono scritte queste cose qui:


<blockquote># some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'</blockquote>


E aggiungiamo sotto all'ultimo "#alias" un "alias" che useremo noi. Per esempio:


<blockquote>alias agi='sudo apt-get install'

alias agu='sudo apt-get update'

alias agd='sudo apt-get dist-upgrade'</blockquote>


Capito come no?

Quindi, in riassunto, si fa così:

**alias _SCORCIATOIA PERSONALE_='_COMANDO COMPLETO CHE SI USA_'**

N.B.: ricordarsi i** --> ' <-- **all'inizio e alla fine del **COMANDO COMPLETO CHE SI USA** e **NON** mettere # prima di alias altrimenti non sarà letto il comando!
