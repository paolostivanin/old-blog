---
comments: true
date: 2011-02-17 11:20:48+00:00
layout: post
title: CMus, player audio...molto minimale!
categories:
- ArchLinux
- Debian &amp; Co
- Gentoo
- Ubuntu
- Unix
tags:
- audio
- cmus
- player
- terminale
---

Qualche giorno fa stavo girovagando fra le _"decine"_ di pacchetti di Synaptic quando ho visto un pacchetto che mi ha incuriosito: [CMUS](http://cmus.sourceforge.net/)

Cmus sta per _C Music Player_ ma è molto diverso dagli altri player che conoscete scritti in C e sapete perchè? Perchè** si usa da terminale** grazie alle [librerie ncurses](http://www.gnu.org/software/ncurses/)

Come potete vedere dal sito le features sono molte e anche molto interessanti:


<blockquote>**Features**
Input/Output Plugins
Input: Ogg/Vorbis, MP3, FLAC, Musepack, WavPack, WMA, WAV, AAC, MP4, APE, and everything supported by libmodplug

Output: PulseAudio, ALSA, OSS, libao, aRts, Sun, and WaveOut (Windows)
Playing
Gapless playback
ReplayGain support
MP3 and Ogg streaming (Shoutcast/Icecast)
Powerful playlist filters
Play queue

Interface
Instant startup, even with thousands of tracks
Easy to use directory browser
Customizable colors
Dynamic keybindings. You can bind a key to any command, :seek +1m for example
Vi / less style search mode
Vi style command mode with tab completion

Misc
UTF-8 support
Excellent compilations handling
Can run external commands for the currently selected files (tag-editor for example)
Can be controlled via UNIX socket using cmus-remote command
Known to work on Linux, OS X, FreeBSD, NetBSD, OpenBSD and Cygwin</blockquote>


<!-- more -->
Dopo averlo installato_ (apt-get install cmus o pacman -S cmus o emerge media-sound/cmus)_ basta aprire il terminale e digitare


`cmus`


e **istantaneamente** avete sotto gli occhi la semplice ed intuitiva interfaccia.

Ci sono 7 tabs (ci si sposta nei vari tab premendo i tasti da 1 a 7) contenenti ognuno diverse cose, nello specifico:



	
  * tab  1: visualizzazione generale

	
  * tab 2: libreria salvata

	
  * tab 3: playlist salvata

	
  * tab 4: tracce in coda

	
  * tab 5: browser

	
  * tab 6: filtri

	
  * tab 7: lista dei comandi


La sintassi, come riportato nelle features, è come quella dell'editor VI/VIM (:quit per uscire, :player stop per stoppare ecc).

Comunque state tranquilli non è fondamentale conoscere queste cose perchè, come potete vedere nella lista dei comandi _(tab 7)_, gli sviluppatori hanno creato una shortcut per ogni cosa :)

Devo dire che a me piace molto, lo trovo semplice, leggero e veloce! Per l'uso che ne faccio io di un player audio (niente copertine, testi, plugin, ecc) ne sono rimasto veramente soddisfattissimo!

[gallery]
