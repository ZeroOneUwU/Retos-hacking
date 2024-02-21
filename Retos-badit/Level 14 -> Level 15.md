## Objetivo 

La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30000 en localhost.
## Datos de acceso al nivel

user bandit14
password - fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
## Solucion

```

bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

^C
bandit14@bandit:~$ ^C
bandit14@bandit:~$ 


//////////////////////////////////////////////////////

bandit14@bandit:~$ echo "fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq" | nc localhost 30000
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

bandit14@bandit:~$ ^C
bandit14@bandit:~$ 


```

## Notas adicionales

nmap 

Por la pregunta sabemos que hay un servicio que se ejecuta en el puerto 30,000. Podemos intentar conectarnos al servicio usando el comando netcat.
Nota: nc es un alias del comando netcat y se puede usar indistintamente

bandido14@bandido:~$ netcat localhost 30000
Contraseña
¡wrong! Por favor ingrese la contraseña actual correcta

Cuando ingresamos un valor aleatorio vemos que recibimos un mensaje que dice que la contraseña es incorrecta.

bandit14@bandit:~$ nc -lnvp 6666
Listening on 0.0.0.0 6666
Connection received on 127.0.0.1 58420
hola
hola
a
jajaj
adios
^C
## Referencias 

https://www.neoguias.com/comando-nc/