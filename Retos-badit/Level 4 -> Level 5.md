## Objetivo 

La contraseña para el siguiente nivel se almacena en el único archivo legible por humanos en el directorio interno. Consejo: si tu terminal está estropeado, prueba el comando “reset”.
## Datos de acceso al nivel

user bandit4  
pass 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
## Solucion
```
bandit4@bandit:~$ ls 
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ cat ./-file00
QRrtZ�i�        �H
                  |��ȧ����^��bandit4@bandit:~/inhere$ 
bandit4@bandit:~/inhere$ file ./-file00
./-file00: data
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
bandit4@bandit:~/inhere$ 
```
## Notas adicionales

El comando file nos da el tipo de datos del archivo. Algunos ejemplos serían: 'ELF', 'script Perl', 'texto ASCII', 'datos' y más.

Para esta tarea, buscamos específicamente archivos legibles por humanos. Significa que los datos se presentan para que podamos leer la información. Un archivo ELF, por ejemplo, no es legible por humanos. Si intentara imprimir su contenido (head <elf_file_name>), el resultado se vería así: �������$��$,0�%��0�'��0<u�� �8�w���9�t�.

Las codificaciones de datos más comunes legibles por humanos son ASCII y Unicode.

Si queremos aplicar/usar un comando en todos los archivos en el directorio actual, repetir el comando o escribir todos los nombres de archivos es tedioso. 

Para usar el comando en todos los archivos del directorio sin escribir mucho, podemos usar '*', que se denomina 'símbolo comodín'. '*' puede representar cualquier número de caracteres literales. Un ejemplo podría ser file*, que coincidiría con todo lo que comience con "file", como "file00", "file", "fileAA", etc. Reemplaza la opción nombre de archivo/ruta en el comando.

El comando _file_ sirve para determinar el tipo de archivo.

Con este comando podemos comprobar fácilmente el tipo de fichero, esto es útil porque no tiene extensión, que por algún motivo creemos no es la correcta o porque desconfiamos por alguna razón. Y entre otras cosas muestra la codificación de caracteres de los archivos de texto, srt, etc.

## Referencias 

https://travesuras.wordpress.com/2013/02/28/20130228-1/