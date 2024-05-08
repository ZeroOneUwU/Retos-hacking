## Objetivo

Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump [here](https://artifacts.picoctf.net/c/509/disassembler-dump0_a.txt).

## Pistas
## Solución

```
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Bit-O-Asm-1]
└─$ ls
disassembler-dump0_a.txt
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Bit-O-Asm-1]
└─$ cat disassembler-dump0_a.txt       
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x4],edi
<+11>:    mov    QWORD PTR [rbp-0x10],rsi
<+15>:    mov    eax,0x30
<+20>:    pop    rbp
<+21>:    ret
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Bit-O-Asm-1]
└─$ python3                                                    
Python 3.11.7 (main, Dec  8 2023, 14:22:46) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print(int("0x30",16))
48
>>> 




```

## Notas adicionales
## Referencias