---
comments: true
date: 2008-11-14 16:15:22+00:00
layout: post
title: ArchLinux e i filmati .WMV per WMP online!
categories:
- ArchLinux
- Unix
---

Qualche giorno fa ho avuto necessità di vedere un video online .WMV (Windows Media Video) che era guardabile solo con WMP (Windows Media Player).

Mi sono accorto che (essendo su Arch) non riuscivo a visualizzare niente (perchè giustamente non c'è WMP per Unix) e, erroneamente pensando che non c'era soluzione, stavo per chiudere tutto.

Per sfizio però ho cercato un po' in giro e, dopo qualche ricerca, ho scoperto che per risolvere questo (ora) banalissimo problema basta aprire il terminale e digitare:


`su`



_password_


`pacman -S mplayer mplayer-plugin`



Questo installerà [Mplayer](http://www.mplayerhq.hu/design7/news.html) e i relativi plugin per web!

Digitando infatti


`about:plugins`



in Firefox, si potrà notare come a diverse estensioni video sia stato associato Mplayer :D

Ma che cos' Mplayer?


<blockquote>MPlayer is a movie player which runs on many systems (see the documentation). 	It plays most MPEG/VOB, AVI, Ogg/OGM, VIVO, ASF/WMA/WMV, QT/MOV/MP4, 	RealMedia, Matroska, [NUT](http://www.nut-container.org/), NuppelVideo, 	FLI, YUV4MPEG, FILM, RoQ, PVA files, supported by many native, XAnim, 	and Win32 DLL codecs. **You can watch VideoCD, SVCD, DVD, 3ivx, DivX 3/4/5, WMV 	and even H.264 movies.**

Another great feature of MPlayer is the wide range of supported output 	drivers. It works with X11, Xv, DGA, OpenGL, SVGAlib, fbdev, AAlib, 	DirectFB, but you can use GGI, SDL (and this way all their 	drivers), VESA (on every VESA compatible card, even without X11!) and 	some low level card-specific drivers (for Matrox, 3Dfx and ATI), too! 	Most of them support software or hardware scaling, so you can enjoy movies in 	fullscreen. MPlayer supports displaying through some hardware MPEG 	decoder boards, such as the Siemens DVB, DXR2 and DXR3/Hollywood+.

MPlayer has an onscreen display (OSD) for status information, nice 	big antialiased shaded subtitles and visual feedback for keyboard controls. 	European/ISO 8859-1,2 (Hungarian, English, Czech, etc), Cyrillic and Korean 	fonts are supported along with 12 subtitle formats (MicroDVD, SubRip, OGM, 	SubViewer, Sami, VPlayer, RT, SSA, AQTitle, JACOsub, PJS and our own: MPsub). 	DVD subtitles (SPU streams, VOBsub and Closed Captions) are supported as 	well</blockquote>


In sostanza Mplayer è un video-player che supporta tutti i tipi di video/audio sopra descritti.

Ecco uno screen di come appare Mplayer:

[![](http://www.allfreeportal.com/imghost/thumbs/294010Schermata.png)](http://www.allfreeportal.com/imghost/viewer.php?id=294010Schermata.png)

Spero di esservi stato utile :D
