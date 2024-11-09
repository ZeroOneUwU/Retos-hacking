## Objetivo

Download this image and find the flag.

- [Download image](https://artifacts.picoctf.net/c/216/pico.flag.png)

## Pistas
## Solución

```


┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0]
└─$ binwalk pico.flag.png

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 585 x 172, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, default compression


┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0]
└─$ zsteg -a pico.flag.png | grep "pico"
b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_a1062667}$t3g0"









//////////////////////////////








┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0]
└─$ git clone https://github.com/djrobin17/image-stego-tool.git
Cloning into 'image-stego-tool'...
remote: Enumerating objects: 32, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (29/29), done.
remote: Total 32 (delta 10), reused 6 (delta 2), pack-reused 0
Receiving objects: 100% (32/32), 27.92 KiB | 397.00 KiB/s, done.
Resolving deltas: 100% (10/10), done.

┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0]
└─$ ls                                                         
image-stego-tool  pico.flag.png

┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0]
└─$ cd image-stego-tool/              

┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0/image-stego-tool]
└─$ ls
README.md  stego.py  stego-start.png

┌──(kali㉿kali)-[~/Documents/PicoCTF/St3g0/image-stego-tool]
└─$ python3 stego.py ../pico.flag.png 

--Welcome to $t3g0--
1: Encode
2: Decode
2
Enter Source Image Path
/home/kali/Documents/PicoCTF/St3g0/pico.flag.png
Enter Password

Decoding...
Hidden Message: 



```
## Notas adicionales

¿QUÉ ES LA STEGANOGRAPHY?

La esteganografía es la ciencia que implica comunicar datos secretos en un soporte multimedia apropiado, por ejemplo, archivos de imagen, audio y vídeo. Se parte del supuesto de que si la característica es visible, el punto de ataque es evidente, por lo que el objetivo aquí es siempre ocultar la existencia misma de los datos incrustados.

zsteg

## Referencias

https://medium.com/swlh/lsb-image-steganography-using-python-2bbbee2c69a2

https://linuxcommandlibrary.com/man/zsteg
https://github.com/zed-0xff/zsteg