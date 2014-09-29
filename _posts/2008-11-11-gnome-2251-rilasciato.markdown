---
comments: true
date: 2008-11-11 17:24:10+00:00
layout: post
title: Gnome 2.25.1 RILASCIATO!
categories:
- Ubuntu
- Unix
---

È stato da poco rilasciato [**Gnome 2.25.1**](http://ftp.gnome.org/pub/GNOME/desktop/2.25/2.25.1/NEWS), la unstable branch della futura **2.26**!

Vediamo quali sono le novità:


<blockquote>

> 
> **NEWS: bug-buddy-2.25.1**
> 
> 


> 
> 2.25.1 ("The Feel-Good vibe")
* Drop libgnome and libgnomeui dependencies.
* Make google-breakpad support optional (but enabled by default).
Thanks to Sjoerd Simons.
* Obtain the real path of the crashed process by looking in /proc.
Thanks to Sam Morris and Matt Keenan.
* Add an option to delete the included file after bug-buddy has
processed it.
* Implement a logger for pasting critical and fatal warnings in the
stacktraces.
* Include the loaded GTK+ modules in the stacktraces sent to bugzilla.
* Update google-breakpad to SVN r290.
* Compile with all the GLib/GTK+ deprecation flags.

> 
> **NEWS: cheese-2.25.1**
> 
> 


> 
> - change the default font of the countdown widget to bitstream vera sans bold
- drop libgnome/libgnome-vfs dependencies, fixes bug #556580, courtesy of Cosimo Cecchi
- exit correctly with unknown command line arguments, fixes bug #556084.
- change the ui behaviour of the fullscreen toolbar, to show always when in
effects chooser mode, fixes bug #548546


> 
> **
NEWS: deskbar-applet 2.25.1**


> 
> In this release all gnomevfs calls have been ported
to gio and from glade files are replaced GTK builder UI
files. Therefore, pygobject 2.15.3 or later is required.


> 
> - Fixed #557570, Crash when proxy port changed (Sebastian PÃ¶lsterl)
- Fixed #551218, Use of strings "Croation" and "Croatian" (Sebastian PÃ¶lsterl)
- Fixed #552203, Typo: affect (Sebastian PÃ¶lsterl)

> 
> **NEWS: evolution-exchange-2.25.1**
> 
> 


> 
> Bug Fixes:
#552261: Don't expose sqlite3 header outside. (Srinivasa Ragavan)

> 
> **NEWS: gnome-control-center-2.25.1**
> 
> 


> 
> General:
- resurrect gnome-font-viewer and gnome-thumbnail-font (Davyd Madeley)
- reduce libgnome* usage (SÃ¸ren Sandmann)
- require GTK+ 2.13.1 (Jens Granseuer)
- require gnome-desktop 2.25.1 (Jens Granseuer)
- code cleanups (Jens Granseuer, Christian Persch, Kjartan Maraas, Bastien Nocera)


> 
> Common:
- use translated names for icon themes if available (Jens Granseuer) (#554272)
- fix error handling when launching help (Jens Granseuer)


> 
> Appearance:
- connect the help buttons to the most appropriate sections in the user guide
(Matthias Clasen) (#554957)


> 
> Default application:
- add Listen to the list of media players (Julien Lavergne)


> 
> Display:
- show an error dialog instead of crashing when initialization fails due to
XRandR not being available (Matt Keenan) (#553762)
- fix preview orientation when using left or right rotation (Jens Granseuer) (#555241)
- use new clone mode API in gnome-desktop (SÃ¸ren Sandmann)
- XOR the old and the new regions instead of subtracting old from new (SÃ¸ren
Sandmann) (#551566)


> 
> Keybindings:
- fix editability of group headings (Matthias Clasen) (#556967)
- avoid duplicate custom keybindings (Matthias Clasen) (#556977)
- add UI for adding and removing named custom shortcuts (Matthias Clasen) (#114796)


> 
> Keyboard:
- fix group sorting (Sergey Udaltsov)
- update group expander highlighting dynamically (Sergey Udaltsov)
- connect the stickykeys_two_key_off button (Jens Granseuer) (#556818)
- remember sorted list of expanders in properties (Sergey Udaltsov)
- scroll the options window when the keyboard focus moves out of the visible
part (Jens Granseuer) (#557944)
- hide/show the "Default" column depending on the "layout per window" checkbox
(Sergey Udaltsov) (#555261)


> 
> Sound:
- make the filechooser default to a sensible directory (Bastien Nocera)


> 
> Windows:
- Use the right values for the h/v maximization titlebar doubleclick action
(Matthias Clasen) (#554962)

> 
> **NEWS: gnome-desktop-2.25.1.1**
> 
> 

> 
> 

> 
> Quick release to not depend on an unreleased glib.
> 
> 

> 
> libgnome-desktop
> 
> 


> 
> * GnomeDesktopThumbnail: disable check for preview::icon, since it's
not available in glib 2.18 (Vincent)

> 
> Misc
> 
> 

> 
> * Require glib 2.18 instead of 2.19 (Vincent)
> 
> 

> 
> **NEWS: gnome-keyring-2.25.1**
> 
> 


> 
> Changes in version 2.25.1 are:
* Remove usage of deprecated glib/gtk stuff.

> 
> **NEWS: gnome-settings-daemon-2.25.1**
> 
> 


> 
> - Ignore the 'activate' signal for deselected items so that the rotation
setting doesn't reset when the systray menu is opened (Eric Piel)
(#554951)
- Don't make togglekeys_enable depend on global AccessX state (Jens
Granseuer) (#555009)
- Fix picking up of the GDM layout (Matthias Clasen) (#554525 and
#555873)
- Use printf safely (Christian Persch) (#555553)
- Show the shutdown dialog when the power button is pressed (Matthias
Clasen) (#556307)
- Support the Gtk/ButtonImages XSetting (Matthias Clasen) (#556797)
- Clean-up volume initialization (Jens Granseuer) (#552383)
- Make the composited volume images more clear (Bogdan Butnaru)
(#557307)
- Spawn screensaver process in idle callback (Rodrigo Moya)
- Remove sound plugin (Jens Granseuer) (#557806)
- Replace gnome_help_display_desktop with gtk_show_uri (Jens Granseuer)
(#557808)
- Listen for X device changes and reconfigure the mouse if necessary
(William Grant) (#549267)
- Remove AM_MAINTAINER_MODE (Jens Granseuer) (#558503)
- Disable xrdb plugin by default (Behdad Esfahbod) (#557807)
- Improve performance logging annotations (Behdad Esfahbod) (#559162)
- Cleanup font module (Behdad Esfahbod) (#559163)
- Don't trap errors around grab_key (Behdad Esfahbod) (#559164)
- Don't run 'mousetweaks -s' at startup (Behdad Esfahbod) (#559165)
- Start fontconfig monitors, mouse and clipboard managers in idle
callbacks (Behdad Esfahbod) (#559166)
- Preload gconf dirs when feasible (Behdad Esfahbod) (#559167)
- Wait for initialization processes to be done before spawning other
processes (Behdad Esfahbod) (#559168)
- Don't close stderr to not lose warnings (Behdad Esfahbod)
- Use a pipe to communicate between children and parent process instead
of a signal (Behdad Esfahbod)

> 
> ** NEWS: gtksourceview-2.4.1**
> 
> 


> 
> * Fix a crash when inserting images in the buffer
* Improvements to some of the lang files
* Updated translations

> 
> 
</blockquote>




Il resto o non è stato aggiornato o erano spiegazione per lo più tecniche che a noi comuni mortali non interessano :-)




Vedremo nella prossima guida come compilare Gnome, ma non con Garnome stavolta! (mi è basta [l'ultima volta](http://polslinux.wordpress.com/2008/06/15/compilazione-gnome-unstable/) **LOL **ahuahuahu :D )




Vedremo un metodo diverso che, spero, funzionerà :D
