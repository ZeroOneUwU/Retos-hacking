## Objetivo 

La contraseña para el siguiente nivel se almacena en el archivo data.txt y es la única línea de texto que aparece solo una vez.
## Datos de acceso al nivel

user bandit8 
password TESKZC0XvTetK0S9xNwm25STk5iWrBvP
## Solucion

```
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ wc data.txt
 1001  1001 33033 data.txt
bandit8@bandit:~$ cat data.txt | sort | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
bandit8@bandit:~$ 
```

## Notas adicionales

sort -> ordena lineas en un archivo de texto.
uniq -u-> FIltra lineas que no se repiten  
uniq -c-> Cuenta las ocurrencias de una linea
uniq -d -> Muestra solo las lineas repetidas
uniq --help

uniq es un comando que filtra la entrada y escribe en la salida. En concreto, filtra basándose en líneas idénticas. Tiene una bandera -u, que filtra por líneas únicas (líneas que aparecen solo unas). Otra funcionalidad interesante es, por ejemplo, que también puede contar (-c) o solo devolver líneas duplicadas (-d).

El comando se utiliza a menudo con ordenar. Para que uniq filtre líneas únicas, es necesario ordenar las líneas. sort ordena las líneas de un archivo de texto. Además, tiene indicadores para ordenar al revés (-r) y ordenar numéricamente (-n).

## Referencias 

https://docs.rockylinux.org/es/books/admin_guide/04-advanced-commands/