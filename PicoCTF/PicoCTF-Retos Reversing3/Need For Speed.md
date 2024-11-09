## Objetivo

The name of the game is [speed](https://www.youtube.com/watch?v=8piqd2BWeGI). Are you quick enough to solve this problem and keep it above 50 mph? [need-for-speed](https://jupiter.challenges.picoctf.org/static/f9abc386dfb1309e687344783f208b20/need-for-speed).
## Pistas
## Solución

```
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ ls
need-for-speed
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ chmod +x need-for-speed  
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ ./need-for-speed   
Keep this thing over 50 mph!
============================

Creating key...
Not fast enough. BOOM!
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ 

┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ gdb -q need-for-speed

///////////// 1 FORMA //////////////////

End of assembler dump.
(gdb) break *(main+30)
Breakpoint 1 at 0x938
(gdb) run
Starting program: /home/kali/Documents/PicoCTF/Need For Speed/need-for-speed 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Keep this thing over 50 mph!
============================


Breakpoint 1, 0x0000555555400938 in main ()
(gdb) jump *(main+35)
Continuing at 0x55555540093d.
Creating key...
Finished
Printing flag:
PICOCTF{Good job keeping bus #190ca38b speeding along!}
[Inferior 1 (process 44485) exited normally]
(gdb) 


////////////////// 2 FORMA //////////

End of assembler dump.
(gdb) break *(main+30)
Note: breakpoint 1 also set at pc 0x555555400938.
Breakpoint 2 at 0x555555400938
(gdb) run
Starting program: /home/kali/Documents/PicoCTF/Need For Speed/need-for-speed 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Keep this thing over 50 mph!
============================


Breakpoint 1, 0x0000555555400938 in main ()
(gdb) call (int) get_key()
Creating key...
Finished
$1 = 9
(gdb) call (int) print_flag()
Printing flag:
PICOCTF{Good job keeping bus #190ca38b speeding along!}
$2 = 56
(gdb) 



/////////// 3 FORMA /////////////

─(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ gdb -q CRACKED       
Reading symbols from CRACKED...
(No debugging symbols found in CRACKED)
(gdb) dissamble main
Undefined command: "dissamble".  Try "help".
(gdb) disassemble main
Dump of assembler code for function main:
   0x000000000000091a <+0>:     push   rbp
   0x000000000000091b <+1>:     mov    rbp,rsp
   0x000000000000091e <+4>:     sub    rsp,0x10
   0x0000000000000922 <+8>:     mov    DWORD PTR [rbp-0x4],edi
   0x0000000000000925 <+11>:    mov    QWORD PTR [rbp-0x10],rsi
   0x0000000000000929 <+15>:    mov    eax,0x0
   0x000000000000092e <+20>:    call   0x8d8 <header>
   0x0000000000000933 <+25>:    mov    eax,0x0
   0x0000000000000938 <+30>:    call   0x82f <set_timer>
   0x000000000000093d <+35>:    mov    eax,0x0
   0x0000000000000942 <+40>:    call   0x87d <get_key>
   0x0000000000000947 <+45>:    mov    eax,0x0
   0x000000000000094c <+50>:    call   0x8ac <print_flag>
   0x0000000000000951 <+55>:    mov    eax,0x0
   0x0000000000000956 <+60>:    lea


Abrimos el hexeditor 
Vamos a la direccion del salto 0x938
Ahi ponemos 90 90 90 90 90
guardamos

┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ hexeditor CRACKED      
                                                                                                                     
┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ ./CRACKED            
Keep this thing over 50 mph!
============================

Creating key...
Finished
Printing flag:
PICOCTF{Good job keeping bus #190ca38b speeding along!}
                                                                                                                     
┌──(kali㉿kali)-[~/Documents/PicoCTF/Need For Speed]
└─$ 


```

## Notas adicionales
## Referencias