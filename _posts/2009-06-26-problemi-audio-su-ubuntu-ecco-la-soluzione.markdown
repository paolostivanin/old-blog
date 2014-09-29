---
author: pol@blog
comments: true
date: 2009-06-26 09:47:56+00:00
layout: post
slug: problemi-audio-su-ubuntu-ecco-la-soluzione
title: Problemi audio su Ubuntu? Ecco la soluzione!
wordpress_id: 737
categories:
- Ubuntu
- Unix
---

Era da un po' che questo problema mi infastidiva:

ad ogni riavvio/accensione del pc, il volume era settato su "disattivato".

Bene, se anche voi avete questo problema, oggi vi spiegherò come risolverlo! :-)

Innazitutto date permesso di scrittura e lettura al file _asound.state_ con:


`sudo chmod +rw /var/lib/alsa/asound.state`



poi _"intestatelo"_ al vostro user con:


`sudo chown NOMEUTENTE /var/lib/alsa/asound.state`



e infine **settate manualmente il livello audio** e poi aprite un terminale e date **NON DA ROOT**:


`alsactl store`



Bene, ora resta da compiere l'ultimo passo:

andate su **Sistema --> Preferenze --> Applicazioni d'Avvio** ed aggiungete:


**Nome:** Alsa level restore




**Comando:** `alsactl restore`




**Commento:** Quello che volete :-)



Bene, ecco risolto ogni problema ;-)
