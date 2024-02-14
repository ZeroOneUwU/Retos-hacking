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

## Referencias 