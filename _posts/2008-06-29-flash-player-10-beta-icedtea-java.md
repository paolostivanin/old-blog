---
comments: true
date: 2008-06-29 16:25:47+00:00
layout: blog
title: Flash Player 10 beta & IcedTea (java)
categories:
- Ubuntu
---

Gli amiconi di Adobe hanno rilasciato la beta di Flash Player 10, che include molte novità (per linux meno novità rispetto a windows han detto sti maledetti).

Quindi mi son detto "perchè non provarlo dato che il 9 mi crea qualche problema?"

Vado sul sito di Adobe, scarico, faccio per installarlo ma...."error X86_64 is not supported by installer"

Alè mi son detto, a posto!

Così ho preso e a manina mi son messo li a farlo andare...ora funziona alla perfezione, se volete provarlo, seguite questa semplice e breve guida:

-----------------------------------------

**Disclaimer:**

_**N.B.: LA GUIDA VALE PER UBUNTU HARDY 64 BIT, NON MI RITENGO RESPONSABILE DI EVENTUALI DANNI ARRECCATI AL VOSTRO PC A CAUSA DI QUESTA GUIDA O NEL CASO FLASH PLAYER DECIDESSE DI DEATOMIZZARE TUTTO QUELLO CHE AVETE!**_

** CHI POSSIEDE ARCHITETTURA 32 BIT È PREGATO DI ANDARE A LEGGERE IN BASSO SU COME INSTALLARLO.**

-----------------------------------------

**PREPARAZIONE INSTALLAZIONE 64 BIT:**

`sudo apt-get remove flashplugin-nonfree
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get remove --purge ia32-libs nspluginwrapper` **(prima di purge ci sono due "-" e non uno come sempre fa visualizzare wordpress)
**
**INSTALLAZIONE 64 BIT:**

`sudo apt-get install ia32-libs nspluginwrapper
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz
tar zxf flashplayer10_install_linux_051508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/`

**PREPARAZIONE INSTALLAZIONE 32 BIT:**

`sudo apt-get remove flashplugin-nonfree
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get remove --purge ia32-libs nspluginwrapper`

**INSTALLAZIONE 32 BIT:**

`sudo apt-get install ia32-libs nspluginwrapper
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
tar zxf flashplayer10_install_linux_051508.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer`

Ecco, ora avete flash player 10 pronto all'uso!

**
**

**ORA INSTALLIAMO ICEDTEA** (java open source, funziona meglio dell'originale e non da problemi):

`sudo apt-get install icedtea-gcjwebplugin icedtea-java7-jre
sudo update-alternatives --config java
`
**(prima di config ci sono due "-" e non solo uno come fa sempre visualizzare wordpress)**

Ecco fatto, installato anche il plugin java!

Per conferma date da termianle:

`java -version`

Spero che questa guida vi sia utile e sopratutto vi funzioni! :D (a me si)
