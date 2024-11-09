## Objetivo
What was I last working on? I remember writing a note to help me remember... You can download the challenge files here:

    challenge.zip

https://artifacts.picoctf.net/c_titan/67/challenge.zip

## Solución
Este reto podemos observar que está manejado por un repositorio de git, y gracias al título time machine, nos damos cuenta de que si tratamos de volver al pasado, podremos encontrar la bandera que estamos buscando, así que si usamos el comando git log, puede que nos ayude a poder ver al pasado

```
C:\Users\mgarcia\Desktop>cd drop-in

C:\Users\mgarcia\Desktop\drop-in>dir
 El volumen de la unidad C no tiene etiqueta.
 El número de serie del volumen es: 9EDD-9F93

 Directorio de C:\Users\mgarcia\Desktop\drop-in

09/03/2024  15:10    <DIR>          .
09/03/2024  15:10    <DIR>          ..
09/03/2024  15:10    <DIR>          .git
09/03/2024  15:10                87 message.txt
               1 archivos             87 bytes
               3 dirs  421,187,796,992 bytes libres

C:\Users\mgarcia\Desktop\drop-in>type message.txt
This is what I was working on, but I'd need to look at my commit history to know why...
C:\Users\mgarcia\Desktop\drop-in>git log
commit b92bdd8ec87a21ba45e77bd9bed3e4893faafd0f (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:29 2024 +0000

    picoCTF{t1m3m@ch1n3_5cde9075}

C:\Users\mgarcia\Desktop\drop-in>
```

Y efectivamente ahí estuvo lo que buscabamos

## Notas adicionales
## Referencias