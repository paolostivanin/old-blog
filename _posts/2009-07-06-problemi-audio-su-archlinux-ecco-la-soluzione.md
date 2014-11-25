---
comments: true
date: 2009-07-06 14:28:34+00:00
layout: blog
title: Problemi audio su Archlinux? Ecco la soluzione!
categories:
- ArchLinux
- Unix
---

Ecco la guida anche per gli arcieri che presentano il problema dell'audio all'avvio!

A me ad ogni riavvio/accensione del pc, il volume mi si settava su "disattivato".

Se anche voi avete questo problema (o simile), oggi vi spiegherò come risolverlo! :-)

Innazitutto date permesso di scrittura e lettura al file _asound.state_ con:


`sudo chmod +rw /etc/asound.state`



poi _"intestatelo"_ al vostro user con:


`sudo chown NOMEUTENTE /etc/asound.state`



e infine **settate manualmente (dall'applet per capirci) il livello audio** e poi aprite un terminale e date **DA ROOT**:


`alsactl store`



Bene, ora resta da compiere l'ultimo passo:

andate su **Sistema --> Preferenze --> Applicazioni d'Avvio** ed aggiungete:


**Nome:** Alsa level restore




**Comando:** `alsactl restore`




**Commento:** Quello che volete :-)



Bene, ecco risolto ogni problema ;-)
