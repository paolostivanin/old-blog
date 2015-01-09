---
comments: true
date: 2008-09-01 17:45:28+00:00
layout: post
title: Risoluzione problema Xorg 1.5rc6 con Intel X3100
categories:
- ArchLinux
- Unix
---

Per quelli di voi che hanno aggiornato Xorg su Arch e hanno una Intel X3100, hanno riscontrato sicuramente il mio stesso problema, che si risolve in modo molto semplice, ovvero:

`su`

`PASSWORD`

`nano /etc/X11/xorg.conf`


Section "Files"
RgbPath      "/usr/share/X11/rgb"
ModulePath   "/usr/lib/xorg/modules"
FontPath     "/usr/share/fonts/misc"
FontPath     "/usr/share/fonts/100dpi:unscaled"
FontPath     "/usr/share/fonts/75dpi:unscaled"
FontPath     "/usr/share/fonts/TTF"
FontPath     "/usr/share/fonts/Type1"
EndSection

**E la trasformiamo in questo modo:**


Section "Files"
#RgbPath      "/usr/share/X11/rgb"
ModulePath   "/usr/lib/xorg/modules"
FontPath     "/usr/share/fonts/misc"
FontPath     "/usr/share/fonts/100dpi:unscaled"
FontPath     "/usr/share/fonts/75dpi:unscaled"
FontPath     "/usr/share/fonts/TTF"
FontPath     "/usr/share/fonts/Type1"
EndSection

Dobbiamo, in sostanza, commentare RgbPath ponendo un # davanti alla riga!

Ed ecco qui, problema risolto :D
