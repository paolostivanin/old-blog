---
comments: true
date: 2014-01-19
layout: blog
title: 'Data Structure in C: the Stack [part 2]'
categories:
- programming
tags:
- c
- stack
---

Nell'articolo precedente ho scritto che il programma che simula lo stack può essere migliorato aggiungendo due cose:

  1. l'utente decide che valore inserire;
  2. pop dell'ultimo valore inserito nella pila;

Supponendo che il programma della scorsa volta lo abbiate chiamato orig.c e che la patch la chiamiate linkedList.patch, il comando da dare per ottenere il sorgente finale è:
    
```sh
patch orig.c -i linkedList.patch -o final.c
```

E questa di seguito è la patch che implementa le due richieste sopra scritte.
    
```diff
--- orig.c	2014-01-19 18:22:22.790943930 +0100
+++ mod.c	2014-01-19 18:24:03.543942255 +0100
@@ -7,27 +7,74 @@
 } *curr, *head, *tmp;

 void free_list();
+void push(int);
+void pop();
+void display();

 int main(void){
-	int i;
+	int ch, toPush;
+	
+	head = NULL;

-    head = NULL;
-    
-	for(i=1; i<=10; i++){ 
-		curr = malloc(sizeof(struct node));
-		curr->val = i;
-		curr->ptr = head;
-		head = curr;
+	while(1){
+		printf("1 - push a value into the stack\n");
+		printf("2 - pop a value from the stack\n");
+		printf("3 - display stack\n");
+		printf("4 - exit\n");
+		printf("Type your choice: ");
+		scanf("%d", &ch);
+		printf("\n");
+		switch(ch){
+			case 1:
+				printf("Enter value to push: ");
+				scanf("%d", &toPush);
+				printf("\n");
+				push(toPush);
+				break;
+			case 2:
+				pop();
+				break;
+			case 3:
+				display();
+				break;
+			case 4:
+				free_list();
+				return 0;
+			default:
+				break;
+		}
 	}
+	
+	return 0;
+}
+
+void push(int num){
+	curr = malloc(sizeof(struct node));
+	curr->val = num;
+	curr->ptr = head;
+	head = curr;
+}

-	while(curr){
-		printf("%d - %p - %p\n", curr->val, curr->ptr, curr);
-		curr = curr->ptr;
+void pop(){
+	if(head == NULL){
+		printf("Empty list\n");
+		return;
 	}
-	free_list();
-	return 0;
+	tmp = head;
+	head = head->ptr;
+	printf("Value %d popped\n", tmp->val);
+	free(tmp);
 }

+void display(){
+	tmp = head;
+	while(tmp){
+		printf(" <- %d", tmp->val);
+		tmp = tmp->ptr;
+	}
+	printf("\n");
+}	
+
 void free_list(){
 	while(head){
 		tmp = head;
```

Per concludere ci tengo a farvi notare due cose:
	
  * l'uso di scanf è **altamente sconsigliato** per motivi di sicurezza;
  * non viene fatta validazione dell'input;

Vi lascio come esercizio i due punti qui sopra in quanto, per tenere il programma il più semplice possibile, ho preferito non essere troppo fiscale nello sviluppo :-)
