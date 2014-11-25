---
layout: blog
title: 'Data Structure in C: the Stack [part 1]'
date: 2014-01-16
comments: true
categories:
- programming
tags:
- c
- stack
---

La pila (_stack in inglese_) è un esempio di [struttura dati dinamica](http://it.wikipedia.org/wiki/Struttura_dati#Strutture_dati_dinamiche) (_da qui in poi SDD_) che utilizza il metodo LIFO (Last In First Out) per l'inserimento (push) e la rimozione (pop) dei dati.

<p align="center">
    <img align="center" src="{{ site.baseurl }}/images/2014/01/Stack.jpg" alt="Esempio di push e pop" />
</p>

Cosa sono le strutture dati (_e le SDD_) esula completamente dallo scopo di questo post ma, se vi interessa, posso sempre fare un approfondimento più avanti :-)

In questo post infatti, voglio mostrarvi come realizzare una semplice pila in C quindi, senza aggiungere tante altre parole, ecco a voi un esempio pratico.

```c
#include <stdio.h>
#include <stdlib.h>

struct node{ //dichiarazione della struttura. La struttura è composta da un numero intero e da un puntatore ad una struttura di tipo node (rappresenta il "nodo successivo").
	int val;
	struct node *ptr;
} *curr, *head, *tmp; //equivalente di "struct node *curr; struct node *head; struct node *tmp;". Dichiaro quidni 3 puntatori ad una struttura di tipo node

void free_list(); //prototipo della funzione che permette di liberare la memoria allocata

int main(void){ //funzione principale
	int i;

    head = NULL; //all'inizio assegno al puntatore il valore NULL (regole di buona programmazione)

	for(i=1; i<=10; i++){ //con questo ciclo creo 10 nodi che conterrano i valori 1,2,3...10
		curr = malloc(sizeof(struct node)); //alloco memoria per il nodo
		curr->val = i; //assegno il valore di "i" all'intero contenuto nella struttura
		curr->ptr = head; //assegno al puntatore ptr il valore del nodo precedentemente creato
		head = curr; //assegno al puntatore head l'indirizzo del nodo attuale (testa della pila)
	}

	while(curr){ //oppure while curr != NULL ovvero finchè non raggiungo il fondo dello stack
		printf("%d - %p - %p\n", curr->val, curr->ptr, curr); //stampo a schermo il valore dei vari interi
		curr = curr->ptr; //e assegno al puntatore l'indirizzo contenuto in ptr (ovvero quello del nodo successivo)
	}
	free_list(); //libero la memoria allocata
	return 0;
}

void free_list(){
	while(head){ //finchè head != NULL ovvero finchè non sono arrivato in fondo allo stack
		tmp = head; //assegno l'indirizzo di head ad un'altra variabile
		head = head->ptr; //assegno a head l'indirizzo del nodo successivo
		free(tmp); //libero la memoria allocata per il nodo attuale
	}
}
```

Ho commentato il codice cercando di essere il più chiaro possibile, spero di esserci riuscito ;-)

Ovviamente questo è un programma base che può essere ulteriormente migliorato, per esempio, aggiungendo queste due cose:

  1. facendo in modo che sia l'utente a decidere che numeri inserire;	
  2. implementando una funzione che permetta il "pop" dell'ultimo valore presente nello stack;

Nel prossimo post (_no, non passeranno mesi come l'ultima volta, prometto!_) vedremo come implementare i due punti qui sopra mentre nel post ancora successivo vedremo la coda, un altro tipo di struttura dati dinamica.
