## Objetivo 

La contraseña para el siguiente nivel se almacena en un archivo en algún lugar del directorio interno y tiene todas las siguientes propiedades:
- human-readable
- 1033 bytes in size
- not executable
## Datos de acceso al nivel

user bandit5 
pass lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

## Solucion

```
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ find . -readable -type f -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

```

## Notas adicionales

ls -R -> Lista archivos de manera recursiva
find -> Permite buscar archivos 

Con más archivos, es fácil perder la visión general.

Para obtener el tamaño del archivo, usamos el comando du. Específicamente, para obtener el tamaño en bytes, también usamos el indicador -b. Para ver todos los archivos, incluidos los ocultos, se ofrece la opción -a.

Además: el comando ls -l también muestra el tamaño de los archivos en la quinta columna.

Para buscar archivos no ejecutables, se puede utilizar el comando **find**. Tiene el indicador -executable, que busca archivos ejecutables y permite operadores como '!' para la negación.

Algunas banderas interesantes adicionales para buscar:

Tiene una bandera para ver el tamaño del archivo en bytes `**-size <bytes>**.`

También tiene la opción de mirar solo archivos `-type f` (sin directorios/no ejecutables).

Tiene un `-readable` flag, pero esto significa que tiene permiso para leer los archivos, no que sean legibles por humanos.

## Referencias 

https://www.ionos.mx/digitalguide/servidores/configuracion/comando-linux-find/