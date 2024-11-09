## Descripcion 

We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.
## Solucion

┌──(kali㉿kali)-[~/Documents/PicoCTF/Corrupt]
└─$ xxd -l 100 mystery  
┌──(kali㉿kali)-[~/Documents/PicoCTF/Corrupt]
└─$ cp mystery flag
Vemos el encabezado
Checamos los magic bytes

0000000  89 50 4E 47  0D 0A 1A 0A
Corregimos

Cambiamos de formato
┌──(kali㉿kali)-[~/Documents/PicoCTF/Corrupt]
└─$ mv flag flag.png 

Volvemos a corregir
00 00 00 0D  49 48 44 52 

Corregimos los chuck
 AA 00   16 25 0
 00
┌──(kali㉿kali)-[~/Documents/PicoCTF/Corrupt]
└─$ hexeditor flag.png

┌──(kali㉿kali)-[~/Documents/PicoCTF/Corrupt]
└─$ hexeditor flag.png  

picoCTF{c0rrupt10n_1847995}

## Notas adicionales
