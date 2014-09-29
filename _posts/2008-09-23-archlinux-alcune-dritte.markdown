---
author: pol@blog
comments: true
date: 2008-09-23 15:28:19+00:00
layout: post
slug: archlinux-alcune-dritte
title: ArchLinux, alcune dritte!
wordpress_id: 292
categories:
- ArchLinux
- Unix
---

Ma ciao gente!

Finalmente torno qua sul mio blog a scrivere, cominciato settembre, cominciati i casini, cominciati gli impegni! Solo la settimana scorsa ho avuto 8 riunioni in 6 giorni!

Ma vabbè, lasciamo perdere la mia RL, siamo qui per parlare di altro!

Oggi vi scrivo alcuni tricks che ho scoperto in questo tempo di inattività dal blog!

**1)** Allora, per cominciare, per chi utilizza **GNOME** ho una domanda: vi siete accorti che su Arch non si può modificare il menù di Gnome? Beh, per risolvere il problema basta _aprire il terminale e scrivere:_


`pacman -S alacarte`



**Alacarte**, per chi non lo sapesse, è un plug-in che permette di modificare il menù Gnome a nostro piacimento :D

**2)** Per installare flashplugin 10 (che funziona perfettamente su architetture i686 mentre X86_64 non so) _apriamo il terminale e scriviamo:_


pacman -R flashplugin



**TORNIAMO NORMAL-USER **_e scriviamo:_


`yaourt -S flashplugin-mozilla`



E siamo a posto :D

**3)** Installiamo e configuriamo LOGROTATE. Questo programma, fatta spicciola, serve per mantenere in ordine e di piccole dimensioni, la cartella /var/log.


`pacman -S logrotate`




`nano /etc/logrotate.conf`



Ora ci troviamo davanti il file di configurazione di Logrotate. Io consiglio di tenerlo così tranne che per una cosa: TOGLIERE il # davanti la parola _compress _in questo modo i log saranno compressi e risparmieremo spazio su disco :D

**4) **Ottimizziamo Pacman con questi semplici comandi:


`su`




`PASSWORD`




`pacman-optimize`




`sync`



**5) **Creiamo delle scorciatoie da usare nel terminale, per esempio, io uso queste:


`su`




`PASSWORD`




`nano ~/.bashrc`



E incollate questo:


# pacman upgrade alias
alias psyu='pacman -Syu'                # Sincronizza e aggiorna
alias ps='pacman -S'            # installa un pacchetto
alias prt='pacman -Rnsc'        # rimuove un pacchetto
alias pacs='pacman -Ss'         # cerca un pacchetto
alias unp='rm -r /var/lib/pacman/db.lck'    # sblocca pacman
alias ys='yaourt -S'                            # installa un pacchetto da AUR
alias ysy='yaourt -Ss'                         # cerca un pacchetto su AUR



#other aliases
alias nbr='nano ~/.bashrc'  # per editare il bashrc

Ho pure commentato i comandi così capite (anche se penso lo sappiate) a cosa servono! Ovviamente ognuno li può modificare come vuole quei comandi ;)

Ecco finito!

Spero sia stato di vostro interesse ed aiuto questo articolo!

Ciao a tutti e buona settimana :D
