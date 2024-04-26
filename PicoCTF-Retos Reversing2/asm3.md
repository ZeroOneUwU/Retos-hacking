## Objetivo

What does asm3(0xba6c5a02,0xd101e3dd,0xbb86a173) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/cb753ae52bca4aa303deca5fbfb01bfb/test.S)
## Pistas
## Solución

push 0xbb86a173
push 0xd101e3dd
push 0xba6c5a02
call asm3

asm3:
         push   ebp
         mov    ebp,esp
         xor    eax,eax
         mov    ah,BYTE PTR [ebp+0xb]
         shl    ax,0x10
         sub    al,BYTE PTR [ebp+0xd]
         add    ah,BYTE PTR [ebp+0xc]
         xor    ax,WORD PTR [ebp+0x12]
         nop
         pop    ebp
         ret 

ponemos esto en assembly emulador 

le damos en step, windows,  registers
Le damos hasta pop
vemos lo que hay en eax
0x0000669B
0x669B
## Notas adicionales

https://carlosrafaelgn.com.br/Asm86/
## Referencias