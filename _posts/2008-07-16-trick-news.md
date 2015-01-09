---
comments: true
date: 2008-07-16 15:43:52+00:00
layout: post
title: Trick & News!
categories:
- Unix
---

Nell'attesa che possa rimettermi a provare distro (**in teoria domani con Debian Testing**), scrivo qualcosina di utile e non!



	
  * **RELEASE SCHEDULE** di Intrepid Ibex (Ubuntu 8.10):


24 luglio --> ALPHA 3 (con live + installazione funzionanti)

14 agosto --> ALPHA 4

4 settembre --> ALPHA 5

18 settembre --> ALPHA 6

23 ottobre --> VERSIONE BETA

26 ottobre --> RELEASE CANDIDATE

30 ottobre --> FINAL RELEASE

Maggiori info su: [RELEASE SCHEDULE UBUNTU 8.10](https://wiki.ubuntu.com/IntrepidReleaseSchedule)



	
  * **Ho varato la riforma sulla partizione del mio HD (LOL) ora così suddiviso:**


100 GB per Arch Linux - 8,5 GB per Intrepid Ibex - 7,5 GB per distro-testing - 1 GB swap.

	
  * **Sintassi e uso del comando CHMOD che molte volte vediamo e in molti non capiscono:**


Allora, CHMOD è il comando per le gestione dei permessi e si usa in questo modo:

`chmod [OPZIONI] permessi nomefile`

_Dove per [OPZIONI] abbiamo:_
<table border="0" >
<tbody >
<tr >

<td style="background-color:#f6d358;text-align:center;" >


**Opzioni**



</td>

<td style="background-color:#f6d358;text-align:center;" >


**Definizione**



</td>
</tr>
<tr >

<td style="text-align:center;" >


u



</td>

<td >


proprietario



</td>
</tr>
<tr >

<td style="text-align:center;" >


g



</td>

<td >


gruppo



</td>
</tr>
<tr >

<td style="text-align:center;" >


o



</td>

<td >


altri



</td>
</tr>
<tr >

<td style="text-align:center;" >


x



</td>

<td >


esecuzione



</td>
</tr>
<tr >

<td style="text-align:center;" >


w



</td>

<td >


scrittura



</td>
</tr>
<tr >

<td style="text-align:center;" >


r



</td>

<td >


lettura



</td>
</tr>
<tr >

<td style="text-align:center;" >


+



</td>

<td >


aggiungi permesso



</td>
</tr>
<tr >

<td style="text-align:center;" >


-



</td>

<td >


annulla permesso



</td>
</tr>
<tr >

<td style="text-align:center;" >


=



</td>

<td >


imposta permesso



</td>
</tr>
</tbody></table>
_E dove per PERMESSI abbiamo:_
<table border="0" >
<tbody >
<tr >

<td style="background-color:#f6d358;text-align:center;" >


**Simbolo**



</td>

<td style="background-color:#f6d358;text-align:center;" >


**Permesso**



</td>

<td style="background-color:#f6d358;text-align:center;" >


**Azione**



</td>
</tr>
<tr >

<td style="text-align:center;" >


r



</td>

<td >


read



</td>

<td >


lettura



</td>
</tr>
<tr >

<td style="text-align:center;" >


w



</td>

<td >


write



</td>

<td >


scrittura



</td>
</tr>
<tr >

<td style="text-align:center;" >


x



</td>

<td >


execute



</td>

<td >


esecuzione



</td>
</tr>
</tbody></table>
Maggiori info su: [CHMOD](http://wiki.ubuntu-it.org/AmministrazioneSistema/PermessiFile?action=show&redirect=PermessiFile)
