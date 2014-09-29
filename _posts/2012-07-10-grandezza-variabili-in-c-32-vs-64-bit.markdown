---
author: pol@blog
comments: true
date: 2012-07-10 09:01:12+00:00
layout: post
slug: grandezza-variabili-in-c-32-vs-64-bit
title: Grandezza variabili in C, 32 vs 64 bit
wordpress_id: 1934
categories:
- Programmazione
- Unix
tags:
- c
- programmazione
- unix
---

Se si compila un programma su un'architettura a 32 bit e su una a 64 bit si avrà come risultato una variazione nella grandezza dei tipi delle variabili e quindi - se non si sta attenti - si può andare incontro ad un possibile segfault, ad un "comportamento indesiderato" oppure ad un buffer overflow.

Vediamo insieme la grandezza di ogni tipo di dato e come varia se compilato in un'architettura a 32 o a 64 bit._ (per una facilitazione nella lettura ho messo in grassetto i tipi di dato che cambiano)_


[table align="center" caption="Tipi di dato in C (in bytes)"]
32 bit,64 bit
int: 4,int: 4
double: 8, double: 8
**long double: 12**,**long double: 16**
float: 4,float: 4
**long int: 4**,**long int: 8**
unsigned int: 4,unsigned int: 4
**unsigned long int: 4**,**unsigned long int: 8**
short int: 2,short int: 2
unsigned short int: 2,unsigned short int: 2
unsigned: 4,unsigned: 4
char: 1,char: 1
unsigned char: 1,unsigned char: 1
**pointer: 4**,**pointer: 8**
**size_t: 4**,**size_t: 8**
[/table]
