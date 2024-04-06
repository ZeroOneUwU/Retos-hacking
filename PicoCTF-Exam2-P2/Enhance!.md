## Objetivo

Download this image file and find the flag.

- [Download image file](https://artifacts.picoctf.net/c/100/drawing.flag.svg)

## Pistas
## Solución

┌──(kali㉿kali)-[~/Documents/PicoCTF/Enhance!]
└─$ ls
drawing.flag.svg                                      
┌──(kali㉿kali)-[~/Documents/PicoCTF/Enhance!]
└─$ strings -n 10 drawing.flag.svg | grep pico
┌──(kali㉿kali)-[~/Documents/PicoCTF/Enhance!]
└─$ strings -n 10 drawing.flag.svg  
p
i
c
o
C
T
F { 3 n h 4 n
c 3 d _ a a b 7 2 9 d d }
picoCTF{3nh4nc3d_aab729dd}
## Notas adicionales
## Referencias