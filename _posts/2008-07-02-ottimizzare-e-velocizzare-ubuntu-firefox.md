---
comments: true
date: 2008-07-02 11:29:29+00:00
layout: post
title: Ottimizzare e velocizzare Ubuntu & Firefox!
categories:
- Ubuntu
---

**PREMESSA: i codici da usare nel terminale saranno riconosciuti perchè usano il tag "code"; le righe di colore rosso sono parole o frasi da aggiungere o sovrascrivere.**

In questa guida, vi insegno come si fa a togliere le cose superflue da Ubuntu e migliorarne quindi le performance!

Allora, cominciamo:

**Disabilitiamo l'IPv6 (scarsamente usato per ora):**

`sudo nano /etc/modprobe.d/aliases
`

Modificare la riga dell'ipv6 come sotto:


alias net-pf-10 off # ipv6


aggiungiamo questa riga:


alias ipv6 off


poi forziamo il kernel a non caricare il modulo per gestire l'IPv6


`sudo nano /etc/modprobe.d/blacklist
`

ed aggiungiamo a fine file questa riga:


blacklist ipv6

**Aumentiamo ora leggermente la velocità di boot** **abilitando l'esecuzione concorrente dei processi di avvio:**

`sudo nano /etc/init.d/rc `

modificate _CONCURRENCY=none_ con:
CONCURRENCY=shell
**N.B.: questa modifica POTREBBE indurre errori in "hal" all' avvio**,                se accadono, ripristinare questa opzione al valore "none"

**Disabilitamo i caratteri orientali in Firefox:** se non visitate                siti con caratteri in lingue orientali disabilitate Pango (rende più snello FF)

`sudo nano /etc/environment`

aggiungere questa riga:
MOZ_DISABLE_PANGO="1"

**Ora v****elocizziamo il caricamento dei programmi tramite prelink:**

`sudo apt-get install prelink`

abilitiamo prelink alla funzione di prelinking editiamo il file                /etc/default/prelink
`
sudo nano /etc/default/prelink`

cerchiamo ad inizio file e modifichiamo la riga come qui sotto riportato:
PRELINKING=yes
quindi forziamo un primo prelink delle applicazioni come da specifiche                del file di configurazione /etc/prelink.conf lanciando:


`sudo /etc/cron.daily/prelink`

**Ora o****ttimizziamo ulteriormente l'accesso al disco su partizioni ext3**

`sudo nano /etc/fstab`

aggiungiamo **noatime,data=writeback** come da esempio:

# Entry for /dev/sda1 :
UUID=8...... / ext3 defaults,errors=remount-ro,**noatime,data=writeback** 0 1 
poi editiamo

`sudo nano /boot/grub/menu.lst`

facendo attenzione a non togliere i # troviamo qualcosa di simile; una volta trovate le righe, aggiungete la parte in rosso:
#defoptions=quiet splash **rootflags=data=writeback**
#altoptions=(recovery mode) single **rootflags=data=writeback **

poi aggiorniamo Grub con:
`
sudo update-grub
`

Poi digitiamo ancora:


`sudo tune2fs -o journal_data_writeback /dev/sda2`** <-- INSERITE IL NUMERO VOSTRO DOPO SDA!**

`sudo tune2fs -l /dev/sda2 ` **<-- INSERITE IL NUMERO VOSTRO DOPO SDA!**

**Assicuratevi di avere un disco live di Linux quello di                installazione di Ubuntu va bene**, perchè se sbagliate                a scrivere vi servirà per ripristinare le cose, e fate ripartire                la macchina.

**Ora ottimizziamo i**** parametri kernel protocollo tcp/ip **

` sudo nano /etc/sysctl.conf `

net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

**Infine ottimizziamo ****il processo di boot (avvio)**

Se avete fatto molte modifiche potreste ottimizzare il processo                di boot così:
Riavviare Ubuntu, al riavvio quando appare Grub                premere il tasto "e" (edit) sulla riga indicante il vostro                kernel di default, cambierà la schermata: andate alla seconda                riga, quella con i parametri del kernel e premete il tasto "e" , successivamente andate               in fondo al termine della riga aggiungete ****

**profile**

**** premete                invio, e premeter il tasto "b" per avviare.
_**Il processo di avvio, solo in questo caso durerà di più,                i riavvi successivi saranno ottimizzati.**_

---------------------------------

**Ora ottimizziamo FIREFOX in questo modo:**

**1.** Premete **CTRL+T** e si aprirà una nuova scheda; sulla barra degli indirizzi della nuova finestra scrivete **about:config** e premete invio da tastiera.
**2.** Cercate queste opzioni (per filtrare cio' che dobbiamo          modificare scrivete parte del nome nella riga filtro) e cambiatele (cliccando          su ogni singola riga da modificare) in:


browser.turbo.enabled: true  -> se non esiste          createla: tasto destro del mouse, nuovo valore booleano
network.dns.disableIPv6: true
network.http.max-connections: 48 
network.http.max-connections-per-server: 24
network.http.max-persistent-connections-per-proxy: 12
network.http.max-persistent-connections-per-server: 6
network.http.pipelining.firstrequest: true
network.http.pipelining: true
network.http.pipelining.maxrequests: 24
network.http.proxy.pipelining: true


**Impostare il valore di network.http.pipelining.maxrequests          a 32 renderà molto veloce FireFox ma potreste venire "bannati"          ovvero esclusi da qualche server.**

**3.** Cliccate sul bottone destro del mouse e selezionate Nuovo ->          Intero.
Impostate il nome di questo nuovo parametro come:
nglayout.initialpaint.delay
Impostate il suo valore a 0 (zero).

**4. **Per diminuire l'occupazione della memoria ram create un nuovo valore booleano:
config.trim_on_minimize

ed imponete il suo          valore a true esso riduce l'occupazione di          20 MB – 30 MB

Infine una tips per noi linuxiani:

Modificando          il valore della variabile: browser.backspace_action che normalmente è 2 ed immettendo          il valore 0 potrete usare il tasto          backspace (quello sopra all'invio) per tornate alla pagina precedente          durante la navigazione.
