## Objetivo 

Hay un binario setuid en el directorio de inicio que hace lo siguiente: establece una conexión con el host local en el puerto que especifica como argumento de la línea de comando. Luego lee una línea de texto de la conexión y la compara con la contraseña del nivel anterior (bandit20). Si la contraseña es correcta, transmitirá la contraseña para el siguiente nivel (bandit21).

NOTA: Intente conectarse a su propio demonio de red para ver si funciona como cree
## Datos de acceso al nivel

user bandit20 -
pass VxCazJaVykI6W36BkBU0mJTCM8rR95XT
## Solucion

```
bandit20@bandit:~$ ls
suconnect
bandit20@bandit:~$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Oct  5 06:19 .
drwxr-xr-x 70 root     root      4096 Oct  5 06:20 ..
-rw-r--r--  1 root     root       220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root      3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root     root       807 Jan  6  2022 .profile
-rwsr-x---  1 bandit21 bandit20 15600 Oct  5 06:19 suconnect
bandit20@bandit:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
bandit20@bandit:~$ nc -lnvp 6669
Listening on 0.0.0.0 6669
^C
bandit20@bandit:~$ nc -lnvp 6669 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT &
[1] 3065096                                                                                      
bandit20@bandit:~$ Listening on 0.0.0.0 6669                                                     
jobs
[1]+  Running                 nc -lnvp 6669 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT &
bandit20@bandit:~$ fg
nc -lnvp 6669 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT
^C
bandit20@bandit:~$ jobs
bandit20@bandit:~$ nc -lnvp 6669 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT &
[1] 3067051
bandit20@bandit:~$ Listening on 0.0.0.0 6669

bandit20@bandit:~$ jobs
[1]+  Running                 nc -lnvp 6669 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT &
bandit20@bandit:~$ ./suconnect 6669
Connection received on 127.0.0.1 35820
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
[1]+  Done                    nc -lnvp 6669 <<< VxCazJaVykI6W36BkBU0mJTCM8rR95XT
bandit20@bandit:~$ 

```

## Notas adicionales

Netcat o nc 
Para crear un servidor en localhost, se necesita el indicador -l (que significa escuchar). Para especificar un puerto, se necesita el indicador -p. Para crear un "servidor único", un servidor que envía un mensaje y luego se desconecta, podemos usar la canalización (| - nivel 6) y el eco para ingresar el mensaje.

Si es necesario ejecutar un comando, pero no necesita interactuar con él por un tiempo y desea seguir usando el mismo terminal con otros comandos mientras se ejecuta el comando, puede usar &. El signo comercial enviará el comando en segundo plano. Esto es parte de la gestión de procesos de Linux. Específicamente, si desea obtener más información sobre esto, consulte también el comando de trabajos, muestra procesos/comandos/trabajos que se ejecutan en segundo plano y en primer plano.


CTRL B 
TMUX setw -g mouse on

## Referencias 

