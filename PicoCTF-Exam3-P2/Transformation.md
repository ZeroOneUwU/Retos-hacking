## Objetivo

I wonder what this really is... [enc](https://mercury.picoctf.net/static/a757282979af14ab5ed74f0ed5e2ca95/enc) `''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
## Pistas
## Solución

```
┌──(kali㉿kali)-[~/Documents/PicoCTF/Transformation]
└─$ ls
enc
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Transformation]
└─$ cat enc          
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彤㔲挶戹㍽                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Transformation]
└─$ python3       
Python 3.11.7 (main, Dec  8 2023, 14:22:46) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> enc=open("enc").read()
>>> print(enc)
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彤㔲挶戹㍽
>>> for c in enc :                                                                         print(hex(ord(c)).lstrip("0x"),end='')
... 
7069636f4354467b31365f626974735f696e73743334645f6f665f385f64353263366239337d>>> 




```

Vamos a convertir el numero en hexa a ascii
https://www.rapidtables.com/convert/number/hex-to-ascii.html

picoCTF{16_bits_inst34d_of_8_d52c6b93}
## Notas adicionales
## Referencias