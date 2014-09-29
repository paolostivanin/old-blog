---
author: pol@blog
comments: true
date: 2010-10-26 20:51:30+00:00
layout: post
slug: alias-nella-schermata-altf2
title: Alias nella schermata Alt+F2!
wordpress_id: 994
categories:
- ArchLinux
- Gentoo
- Ubuntu
- Unix
---

Avete mai desiderato di poter usufruire di un comodo _"alias"_ per la schermata invocata col comando **Alt+F2**?

[caption id="attachment_995" align="aligncenter" width="300" caption="Alt+F2"][![]({{ site.baseurl }}/images/2010/10/Schermata2-300x148.png)]({{ site.baseurl }}/images/2010/10/Schermata2.png)[/caption]

Si???

Bene allora questa guida è ciò che fa per voi :)

Per prima cosa dobbiamo creare uno script che abbia il nome del comando alias e che contenga il comando dell'applicazione che vogliamo eseguire, ovvero:


`nano -w gt`


E scriviamo:


`#!/bin/bash`




`gnome-terminal`


In pratica con questo script vogliamo dire che con il comando **gt **eseguiamo gnome-terminal.

Fatto ciò rendiamo eseguile lo script con:


`chmod +x gt`


E spostiamolo in /usr/local/bin con:


`sudo mv -v gt /usr/local/bin`


Ed ora se premiamo **Alt+F2 **e scriviamo **gt** vedremo eseguirsi gnome-terminal:

[caption id="attachment_1004" align="aligncenter" width="300" caption="Alt+F2 con alias!"][![]({{ site.baseurl }}/images/2010/10/gt1-300x144.png)]({{ site.baseurl }}/images/2010/10/gt1.png)[/caption]
