---
comments: true
date: 2012-09-02 13:29:06+00:00
layout: blog
title: '[Soluzione] Libreoffice 3.6.1 non parte su Archlinux'
categories:
- ArchLinux
- Unix
---

Se dopo l'aggiornamento a Libreoffice 3.6.1-2 ricevete un errore oppure lo spash screen si mettere a lampeggiare perennemente allora dovete installare questi pacchetti:

`pacman -S libreoffice-extension-presentation-minimizer lcms2 clucene`

Ed ecco che il problema è _automagicamente_ risolto! :)

**EDIT: con la versione 3.6.1-3 il problema è stato risolto :)**
