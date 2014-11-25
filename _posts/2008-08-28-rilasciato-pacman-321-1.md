---
comments: true
date: 2008-08-28 13:03:48+00:00
layout: blog
title: Rilasciato Pacman 3.2.1-1
categories:
- ArchLinux
---

È stato rilasciato Pacman 3.2.1-1, il noto gestore pacchetti di Arch Linux. Vediamo un po' quali sono le modifiche apportate rispetto la versione 3.2.0:


DESCRIPTION OF PACMAN 3.2.1
-----------------------------------------------------------------------------
- drop special handling of file:// URLs
- display optdepends on install and upgrade
- fix segfault on x86_64 when using UseSyslog (FS#11096)
- fix detection of TotalDownload (FS#11180)
- fix "No such file" error during --force installs (FS#11218)
- better handling of progressbar when behind a proxy (FS#8725)
- repo-add: fix whitespace handling (FS#9171, FS#10630)
- repo-add: add optdepends to the sync DB (FS#10630)
- makepkg:
- allow specifying a download filename (related to FS#11292)
- fix download functions with weird URLs (FS#11076)
- fix creation of source package with local files (FS#11149)
- fix error when sourcing profile scripts (FS#11179)
- perform case-insensitive checksum comparison (FS#11283)
- documentation and help updates (including fix for FS#11203)
- new Ukrainian translation
- existing translation updates

Direi che ci sono stati solo bug-fix e traduzioni in questa minor-release (che di sicuro non fanno mai male).

Speriamo che un giorno il nostro amato Pacman sia riscritto e magari reso più snello e veloce (con un database per esempio) :D
