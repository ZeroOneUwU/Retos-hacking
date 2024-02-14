## Objetivo 
La contraseña para el siguiente nivel se almacena en un archivo oculto en el directorio interno.
## Datos de acceso al nivel
user bandit3  
pass aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
## Solucion

```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Oct  5 06:19 .
drwxr-xr-x 3 root    root    4096 Oct  5 06:19 ..
-rw-r----- 1 bandit4 bandit3   33 Oct  5 06:19 .hidden
bandit3@bandit:~/inhere$ cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
bandit3@bandit:~/inhere$ 
```
## Notas adicionales

Para recorrer los directorios, existe el comando “cambiar directorio”: `cd <ruta>.`

La ruta del comando puede ser una ruta absoluta (ruta desde el directorio raíz /) o una ruta relativa (ruta desde el directorio de trabajo actual).

Los usos interesantes del comando son:

     cd .. va al directorio principal
     cd / va al directorio raíz
     cd ~ va al directorio de inicio (del usuario actual)


Un archivo oculto en Linux comienza con a  .. El comando ls muestra solo archivos no ocultos. Sin embargo, con el indicador -a muestra todos los archivos, específicamente también los archivos ocultos.

Las dos primeras entradas ocultas en los directorios representan el directorio actual (.) y el directorio principal (..).

Para listar el contenido detallado usa el flag -l

Asi que para esta ocasion teniamos que sacar el password de un archivo oculto.


## Referencias 

https://ed.team/blog/10-comandos-linux-que-debes-conocer