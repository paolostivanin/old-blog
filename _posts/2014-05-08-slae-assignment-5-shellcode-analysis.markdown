---
comments: true
date: 2014-05-08
layout: post
title: 'SLAE Assignment 5: Shellcode Analysis'
categories:
- programming
- SLAE
tags:
- asm-x86
- nasm
- slae
---

This is the fifth of the seven assignment necessary to accomplish the [SecurityTube Linux Assembly Expert](http://www.securitytube-training.com/online-courses/securitytube-linux-assembly-expert/index.html) certification. The instructions for this assignment are:

  1. Take up at least three shellcode samples created using msfpayload for linux/x86

  2. Use GDB/Ndisasm/Libemu to dissect the functionality of the shellcode
	
  3. Present the three shellcode analysis

The first shellcode which I chose to analyze is `linux/x86/chmod` which changes the permssion of a given file to a given mode.

Using the following command I was able to get the shellcode which changes the permission of the file `/home/polslinux/assignment-5/slae-id-526.txt` to `0666`:

```
msfpayload linux/x86/chmod FILE=/home/polslinux/assignment-5/slae-id-526.txt MODE=0666 C
```

The output of the above command is:

```c
/*
 * linux/x86/chmod - 69 bytes
 * FILE=/home/polslinux/assignment-5/slae-id-526.txt, MODE=0666
 */
unsigned char buf[] = 
  "\x99\x6a\x0f\x58\x52\xe8\x2d\x00\x00\x00\x2f\x68\x6f\x6d\x65"
  "\x2f\x70\x6f\x6c\x73\x6c\x69\x6e\x75\x78\x2f\x61\x73\x73\x69"
  "\x67\x6e\x6d\x65\x6e\x74\x2d\x35\x2f\x73\x6c\x61\x65\x2d\x69"
  "\x64\x2d\x35\x32\x36\x2e\x74\x78\x74\x00\x5b\x68\xb6\x01\x00"
  "\x00\x59\xcd\x80\x6a\x01\x58\xcd\x80";
```

With the command `msfpayload linux/x86/chmod FILE=/home/polslinux/assignment-5/slae-id-526.txt MODE=0666 R | ndisasm -u -` it is possible to disassemble the shellcode:

```nasm    
00000000  99                cdq
00000001  6A0F              push byte +0xf
00000003  58                pop eax
00000004  52                push edx
00000005  E82D000000        call dword 0x37
0000000A  2F                das
0000000B  686F6D652F        push dword 0x2f656d6f
00000010  706F              jo 0x81
00000012  6C                insb
00000013  736C              jnc 0x81
00000015  696E75782F6173    imul ebp,[esi+0x75],dword 0x73612f78
0000001C  7369              jnc 0x87
0000001E  676E              a16 outsb
00000020  6D                insd
00000021  656E              gs outsb
00000023  742D              jz 0x52
00000025  352F736C61        xor eax,0x616c732f
0000002A  652D69642D35      gs sub eax,0x352d6469
00000030  3236              xor dh,[esi]
00000032  2E7478            cs jz 0xad
00000035  7400              jz 0x37
00000037  5B                pop ebx
00000038  68B6010000        push dword 0x1b6
0000003D  59                pop ecx
0000003E  CD80              int 0x80
00000040  6A01              push byte +0x1
00000042  58                pop eax
00000043  CD80              int 0x80
```

Now i'm going to explain the execution flow of the above shellcode.
	
  1. `cdq` is used to zeroing out the `edx` register (later we'll know why);
	
  2. The byte `0x0f` (15 in decimal format) is pushed onto the stack and then is popped inside `eax`. This byte identifies the syscall `sys_chmod(const char *filename [ebx], mode_t mode [ecx])`

```
    $ grep 15 /usr/src/linux/arch/x86/syscalls/syscall_32.tbl 
    15 i386 chmod sys_chmod
```

  3. `edx` is pushed onto the stack. This is needed because the file name **must be** null-terminated. A non-null terminated file name will cause the program to crash (segfault);

  4. From `0000000A` to `00000035` there are some dynamic created instructions (due to the use of msfpayload) which set up the stack so that the chose string is available without any other pushing;

  5. The address of the file path is popped inside `ebx`, the mode `0666` (which is `0x1b6` in hex) is pushed onto the stack and then popped inside `ecx`. After that the syscall is executed.
	
  6. Finally the `sys_exit` syscall is called without any error_number (which should be written inside the `ebx` register)

[![ass5_s1]({{ site.baseurl }}/images/2014/05/ass5_s1.png)]({{ site.baseurl }}/images/2014/05/ass5_s1.png)

Please note that with `sctest` we can see what the program is doing but not what we are chmoding. This problem is due to how metasploit treats the payload (see point #4).

[![ass5_s1g]({{ site.baseurl }}/images/2014/05/ass5_s1g.png)]({{ site.baseurl }}/images/2014/05/ass5_s1g.png)

* * *

The second shellcode I chose to analyze is `linux/x86/exec` configured to execute the command `echo SLAE-ID-526`. The output of msfpayload `linux/x86/exec cmd="echo SLAE-ID-526`  is:
    
```c
/*
 * linux/x86/exec - 52 bytes
 * CMD=echo SLAE-ID-526
 */
unsigned char buf[] = 
  "\x6a\x0b\x58\x99\x52\x66\x68\x2d\x63\x89\xe7\x68\x2f\x73\x68"
  "\x00\x68\x2f\x62\x69\x6e\x89\xe3\x52\xe8\x11\x00\x00\x00\x65"
  "\x63\x68\x6f\x20\x53\x4c\x41\x45\x2d\x49\x44\x2d\x35\x32\x36"
  "\x00\x57\x53\x89\xe1\xcd\x80";
```

Using msfpayload `linux/x86/exec cmd="echo SLAE-ID-526" R |ndisasm -u -`  I was able to disassemble the shellcode:

```nasm
00000000  6A0B              push byte +0xb
00000002  58                pop eax
00000003  99                cdq
00000004  52                push edx
00000005  66682D63          push word 0x632d
00000009  89E7              mov edi,esp
0000000B  682F736800        push dword 0x68732f
00000010  682F62696E        push dword 0x6e69622f
00000015  89E3              mov ebx,esp
00000017  52                push edx
00000018  E811000000        call dword 0x2e
0000001D  6563686F          arpl [gs:eax+0x6f],bp
00000021  20534C            and [ebx+0x4c],dl
00000024  41                inc ecx
00000025  45                inc ebp
00000026  2D49442D35        sub eax,0x352d4449
0000002B  3236              xor dh,[esi]
0000002D  005753            add [edi+0x53],dl
00000030  89E1              mov ecx,esp
00000032  CD80              int 0x80
```

Thanks to libemu we can better understand what the shellcode do:

```c
int execve (
  const char * dateiname = 0x00416fc0 => 
          = "/bin/sh";
  const char * argv[] = [
          = 0x00416fb0 => 
              = 0x00416fc0 => 
                 = "/bin/sh";
          = 0x00416fb4 => 
              = 0x00416fc8 => 
                 = "-c";
          = 0x00416fb8 => 
              = 0x0041701d => 
                 = "echo SLAE-ID-526";
          = 0x00000000 => 
              none;
         ];
  const char * envp[] = 0x00000000 => 
          none;
  ) =  0;
```

As we can see there is only one syscall which is a `sys_execve(const char *filename, char *const argv[], char *const envp[])``

This syscall uses four registers:
	
  * `eax` for the syscall number `(0xb)``

  * `ebx` for the address of `/bin/sh`
	
  * `ecx` for the address of `/bin/sh -c echo SLAE-ID-526`  (from `0000018` to `0000002D` see the point #4 of the first shellcode to understand why there are so many instructions)
	
  * `edx` for the `NULL` value (zeroed using `cdq`)


[![ass5_s2]({{ site.baseurl }}/images/2014/05/ass5_s2.png)]({{ site.baseurl }}/images/2014/05/ass5_s2.png)

* * *

The third and last shellcode which has been analyzed is `linux/x86/read_file` which read up to 4096 bytes from the file `/etc/passwd` and then print the result to the standard output (FD #1). The shellcode has been configured using `msfpayload linux/x86/read_file PATH=/etc/passwd FD=1 C`. This is the output of the above command:

```c    
/*
 * linux/x86/read_file - 73 bytes
 * PATH=/etc/passwd, FD=1
 */
unsigned char buf[] = 
 "\xeb\x36\xb8\x05\x00\x00\x00\x5b\x31\xc9\xcd\x80\x89\xc3\xb8"
 "\x03\x00\x00\x00\x89\xe7\x89\xf9\xba\x00\x10\x00\x00\xcd\x80"
 "\x89\xc2\xb8\x04\x00\x00\x00\xbb\x01\x00\x00\x00\xcd\x80\xb8"
 "\x01\x00\x00\x00\xbb\x00\x00\x00\x00\xcd\x80\xe8\xc5\xff\xff"
 "\xff\x2f\x65\x74\x63\x2f\x70\x61\x73\x73\x77\x64\x00";
```

Using ndisasm we can disassemble the shellcode and get this result:

```nasm    
00000000  EB36              jmp short 0x38
00000002  B805000000        mov eax,0x5
00000007  5B                pop ebx
00000008  31C9              xor ecx,ecx
0000000A  CD80              int 0x80
0000000C  89C3              mov ebx,eax
0000000E  B803000000        mov eax,0x3
00000013  89E7              mov edi,esp
00000015  89F9              mov ecx,edi
00000017  BA00100000        mov edx,0x1000
0000001C  CD80              int 0x80
0000001E  89C2              mov edx,eax
00000020  B804000000        mov eax,0x4
00000025  BB01000000        mov ebx,0x1
0000002A  CD80              int 0x80
0000002C  B801000000        mov eax,0x1
00000031  BB00000000        mov ebx,0x0
00000036  CD80              int 0x80
00000038  E8C5FFFFFF        call dword 0x2
0000003D  2F                das
0000003E  657463            gs jz 0xa4
00000041  2F                das
00000042  7061              jo 0xa5
00000044  7373              jnc 0xb9
00000046  7764              ja 0xac
00000048  00                db 0x00
```

In the above snippet we can see that this is a `JMP(00000000)` - `CALL(00000038)` - `POP(00000007)` shellcode and four syscalls have been used:

  * `sys_open(eax=0x5, ebx=filename, ecx=0)`;
	
  * `sys_read(eax=0x3, ebx=return_value_of_open, ecx=buffer, edx=0x1000)`;
	
  * `sys_write(eax=0x4, ebx=1, ecx=buffer, edx=return_value_of_read)`;
	
  * `sys_exit(eax=0x1, ebx=0)`;

This is all for this assignment, I hope I was clear enough to let you better understand the art of the shellcoding :-)

All the sources can be found in my [Github page](https://github.com/polslinux/SLAE/).


This blog post has been created for completing the requirements of the SecurityTube Linux Assembly Expert certification: [http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/](http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/)


**Student ID: SLAE-526**
