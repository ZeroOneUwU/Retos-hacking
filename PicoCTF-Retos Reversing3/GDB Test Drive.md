## Objetivo

Can you get the flag? Download this [binary](https://artifacts.picoctf.net/c/86/gdbme). Here's the test drive instructions:

- `$ chmod +x gdbme`
- `$ gdb gdbme`
- `(gdb) layout asm`
- `(gdb) break *(main+99)`
- `(gdb) run`
- `(gdb) jump *(main+104)`
## Pistas
## Solución

```
┌──(kali㉿kali)-[~/Documents/PicoCTF/GDB TEST]
└─$ ls            
gdbme
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/GDB TEST]
└─$ chmod +x gdbme
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/GDB TEST]
└─$ ./gdbme       
^C
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/GDB TEST]
└─$ gdb gdbme





(gdb) set disassembly-flavor intel
(gdb) disassemble main


- `$ chmod +x gdbme`
- `$ gdb gdbme`
- `(gdb) layout asm`
- `(gdb) break *(main+99)`
- `(gdb) run`
- `(gdb) jump *(main+104)`

ctrl xa

picoCTF{d3bugg3r_dr1v3_72bd8355}

```
## Notas adicionales
## Referencias