---
author: pol@blog
comments: true
date: 2011-01-18 22:57:26+00:00
layout: post
slug: installare-drupal-in-localhost
title: Installare Drupal in localhost!
wordpress_id: 1070
categories:
- Generale
- Unix
---

Se volete provare [Drupal 7.0](http://ftp.drupal.org/files/projects/drupal-7.0.tar.gz) in localhost (previa installazione [xampp](http://www.apachefriends.org/it/xampp.html)) bisogna usare un piccolo _trucco_ quando vi viene chiesto di impostare il DB.

Infatti a causa di un problemino di Drupal 7.0 localhost non viene riconosciuto come 127.0.0.1.

Perciò quando siete nella pagina delle impostazione del DB dovete cliccare su _Avanzate_ e sostituire _localhost_ con _127.0.0.1_

Ora l'installazione procederà normalmente e una volta terminato potrete vedere il vostro sito di prova all'indirizzo **http://localhost/drupal** _ (ammesso che la cartella presente in /opt/lampp/htdocs sia drupal)_

[gallery]

_ _

_ _
