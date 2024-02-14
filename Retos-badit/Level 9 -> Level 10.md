## Objetivo 

La contraseña para el siguiente nivel se almacena en el archivo data.txt en una de las pocas cadenas legibles por humanos, precedida por varios caracteres "=".
## Datos de acceso al nivel

user bandit9 
password - EN632PlfYiZbn3PhVK3XOGSlNInNE00t
## Solucion

```
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ file data.txt
data.txt: data
bandit9@bandit:~$ strings data.txt | grep ==
x]T========== theG)"
========== passwordk^
========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
bandit9@bandit:~$ 
```

## Notas adicionales

string -> Extrae las cadenas de un archivo binario

## Referencias 
