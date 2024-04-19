## Objetivo

I have these 2 images, can you make a flag out of them? [scrambled1.png](https://mercury.picoctf.net/static/e8054e22552c6aba591cdf7440eb25e4/scrambled1.png) [scrambled2.png](https://mercury.picoctf.net/static/e8054e22552c6aba591cdf7440eb25e4/scrambled2.png)
## Pistas
## Solución

```
┌──(kali㉿kali)-[~/Documents/PicoCTF/pixalated]
└─$ convert scrambled1.png scrambled2.png -compose Add -composite flag.png
                                                                                                           
┌──(kali㉿kali)-[~/Documents/PicoCTF/pixalated]
└─$ ls
flag.png  scrambled1.png  scrambled2.png
                                                                                                           
┌──(kali㉿kali)-[~/Documents/PicoCTF/pixalated]
└─$ 



```
## Notas adicionales

imagemagick

## Referencias