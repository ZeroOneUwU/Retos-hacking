## Objetivo
I accidentally wrote the flag down. Good thing I deleted it! You download the challenge files here:

    challenge.zip

https://artifacts.picoctf.net/c_titan/76/challenge.zip

## Solución
En este nivel, podemos observar que al descargar el archivo zip, contiene una carpeta llamada .git, esta carpeta se encuentra en todas las carpetas que han usado git para manejar su información, y el creador del nivel nos dice que tenía ahí la bandera pero después la borró, como sabemos que está usando git, podemos hacer un rollback a la versión que todavía tenía la bandera

Mediante el comando git log, podemos ver el historial de commits que se hicieron al repositorio.

```powershell
C:\Users\mgarcia\Desktop\drop-in>dir
 El volumen de la unidad C no tiene etiqueta.
 El número de serie del volumen es: 9EDD-9F93

 Directorio de C:\Users\mgarcia\Desktop\drop-in

09/03/2024  15:10    <DIR>          .
09/03/2024  15:10    <DIR>          ..
09/03/2024  15:10    <DIR>          .git
09/03/2024  15:10                11 message.txt
               1 archivos             11 bytes
               3 dirs  421,400,363,008 bytes libres

C:\Users\mgarcia\Desktop\drop-in>git log
commit a6dca68e4310585eac3b5c9caf0f75967dfe972c (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:06 2024 +0000

    remove sensitive info

commit e720dc26a1a55405fbdf4d338d465335c439fb3e
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:06 2024 +0000

    create flag


```

Como podemos observar, hay un commit donde se indica que se borró información sensible, entonces ahora con el comando git checkout podemos ir a esa versión que tenía la bandera

```powershell
C:\Users\mgarcia\Desktop\drop-in>git checkout e720dc26a1a55405fbdf4d338d465335c439fb3e
Note: switching to 'e720dc26a1a55405fbdf4d338d465335c439fb3e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at e720dc2 create flag

C:\Users\mgarcia\Desktop\drop-in>dir
 El volumen de la unidad C no tiene etiqueta.
 El número de serie del volumen es: 9EDD-9F93

 Directorio de C:\Users\mgarcia\Desktop\drop-in

12/03/2024  20:02    <DIR>          .
12/03/2024  20:02    <DIR>          ..
12/03/2024  20:02    <DIR>          .git
12/03/2024  20:02                28 message.txt
               1 archivos             28 bytes
               3 dirs  421,393,752,064 bytes libres

C:\Users\mgarcia\Desktop\drop-in>type message.txt
picoCTF{s@n1t1z3_7246792d}

C:\Users\mgarcia\Desktop\drop-in>
```

## Notas adicionales
## Referencias