---
comments: true
date: 2008-11-10 15:37:45+00:00
layout: blog
title: Foresight 2.0.4 provata per voi!
categories:
- Unix
---

Ancora a settembre, avevo provato [**Foresight Linux**](www.foresightlinux.org), una distro gnommosa!

Gnommosa?!?

Si, gnommosa nel senso che è **SEMPRE** aggiornata con gli ultimissimi pacchetti Gnome, sia Gnome stesso, sia i software ad esso correlati!

Durante la mia esperienza di qualche ora, posso dire che l'ho trovata una distro leggera, veloce, e reattiva, graficamente bella ed avvincente!

Avvincente perchè il gestore pacchetti è **Conary**, un gestore a me sconosciuto finchè non ho provato Foresight!

Non saprei spiegarvi molto su questo PM, ma se devo dare un parere sui comandi, alcuni sono banali, come _conary updateall_, altri invece astrusi come _sudo conary update package=@fl:2-devel-type._

Nel complesso la trovo un'ottima distro, anche se come contro le darei proprio **Conary** perchè è un gestore pacchetti molto lento, soprattutto nell'aggiornare, perchè fa duemila giri e rigiri di dipendenze e questo e quello, prima di aggiornare!

Certo, poi è questione di abitudine e di gusti, però preferisco di gran lunga **Pacman**.

Vi lascio alcuni comandi, così se qualcuno la prova almeno sa come giostrarsi:

**Trovare un pacchetto:**


`conary q `_package_ `--troves`



**Vedere se un pacchetto è installato:**


`conary q `_package_



**Installare O aggiornare UN pacchetto:**


`conary update `_package_



**Aggiornare TUTTO il sistema**


`conary updateall`



**Rimuovere un pacchetto:**


`conary erase` _package_







A voi qualche screen:






[![](http://www.allfreeportal.com/imghost/thumbs/13150Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=13150Schermata.png)

[![](http://www.allfreeportal.com/imghost/thumbs/915898Schermata-1.png)](http://www.allfreeportal.com/imghost/viewer.php?id=915898Schermata-1.png)

[![](http://www.allfreeportal.com/imghost/thumbs/600571Schermata-3.png)](http://www.allfreeportal.com/imghost/viewer.php?id=600571Schermata-3.png)

[![](http://www.allfreeportal.com/imghost/thumbs/361459Schermata-4.png)](http://www.allfreeportal.com/imghost/viewer.php?id=361459Schermata-4.png)

[![](http://www.allfreeportal.com/imghost/thumbs/764929Schermata-5.png)](http://www.allfreeportal.com/imghost/viewer.php?id=764929Schermata-5.png)

[![](http://www.allfreeportal.com/imghost/thumbs/435271Schermata-6.png)](http://www.allfreeportal.com/imghost/viewer.php?id=435271Schermata-6.png)

[![](http://www.allfreeportal.com/imghost/thumbs/545224Schermata-9.png)](http://www.allfreeportal.com/imghost/viewer.php?id=545224Schermata-9.png)

[![](http://www.allfreeportal.com/imghost/thumbs/285894Schermata-7.png)](http://www.allfreeportal.com/imghost/viewer.php?id=285894Schermata-7.png)

Queste recensione è stata fatta su una versione "vecchia", nel senso che è già uscita da parecchio la versione **2.0.5** che include Gnome **2.24.1**, Packagekit **0.3.4**, e molti altri updates!

Per quanto riguardo il kernel, nella minor release 2.0.5, è il **2.6.26**!

Ecco, se posso darvi un consiglio, [SCARICATELA](http://www.foresightlinux.org/gnome.html) (<-- clicca li), merita veramente di essere provata, soprattutto se siete dei fan di Gnome :D
