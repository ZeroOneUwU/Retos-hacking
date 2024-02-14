## Objetivo 

La contraseña para el siguiente nivel se almacena en el archivo data.txt junto a la palabra **millionth**
## Datos de acceso al nivel

user bandit7 
password - z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
## Solucion

```
bandit7@bandit:~$ ls 
data.txt
bandit7@bandit:~$ wc data.txt
  98567  197133 4184396 data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
bandit7@bandit:~$ cat data.txt | grep millionth
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
bandit7@bandit:~$ 
```

## Notas adicionales

wc -l -> contar las lineas de un archivo de texto
head -> muestra las primeras 10 lineas
tail -> ultimas 10 lineas

**grep**  -> se puede usar para buscar líneas que contengan un patrón específico como seguir `grep <pattern>.` osea que filtra las lineas en base a un patron que en este caso es **millionth**

Con  (|), podemos canalizar la salida de cat a grep como entrada para revisar un archivo de texto.

## Referencias 

https://www.hostinger.mx/tutoriales/comando-grep-linux