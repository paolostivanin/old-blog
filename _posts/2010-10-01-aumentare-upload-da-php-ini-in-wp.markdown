---
author: pol@blog
comments: true
date: 2010-10-01 14:25:25+00:00
layout: post
slug: aumentare-upload-da-php-ini-in-wp
title: Aumentare upload da php.ini in WP!
wordpress_id: 963
categories:
- Generale
- Unix
---

Stavo cercando come aumentare i limiti di upload che WP ferma a **2MB/file.**

La soluzione è stata più semplice di quello che credevo e, se anche a voi serve, fate così:



	
  1. Tramite un qualsiasi programma FTP controllate se nel server remoto in _httpdocs/wp-admin_ è presente il file _php.ini_;

	
  2. Se non è presente creiamolo in locale, se è presente copiamolo in locale ed editiamolo come scritto sotto;

	
  3. Uppiamo il file_ php.ini_ nel server remoto_ (httpdocs/wp-admin)_

	
  4. Woilà, limite aumentato :)


**Come editare file php.ini:**


`file_uploads	= On ;permettere upload file tramite http
upload_max_filesize = 8M ;grandezza massima concesso, nota che M = MB
post_max_size = 8M ;alcuni non devono modificare/aggiungere questa riga, altri si. Provate voi e vedete!`
