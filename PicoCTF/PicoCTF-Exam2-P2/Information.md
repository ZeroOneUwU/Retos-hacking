## Objetivo

Los archivos siempre se pueden cambiar de forma secreta. ¿Puedes encontrar la bandera? gato.jpg
## Pistas
## Solución

┌──(kali㉿kali)-[~/Documents/PicoCTF/Information]
└─$ exiftool cat.jpg 

Vemos que la licencia tiene un numero en base 64
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9

Usamos cyberchef

picoCTF{the_m3tadata_1s_modified}

## Notas adicionales
## Referencias