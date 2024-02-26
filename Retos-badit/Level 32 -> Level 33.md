## Objetivo 

Después de todo esto, es hora de otro escape. ¡Buena suerte!

## Datos de acceso al nivel

user bandit32
pass rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
## Solucion


```

WELCOME TO THE UPPERCASE SHELL
>> $0
$ pwd
/home/bandit32
$ id
uid=11033(bandit33) gid=11032(bandit32) groups=11032(bandit32)
$ cat /etc/bandit_pass/bandit33                               
odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
$ 

///////////////////////////////

WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> $0
$ ls
uppershell
$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Oct  5 06:19 .
drwxr-xr-x 70 root     root      4096 Oct  5 06:20 ..
-rw-r--r--  1 root     root       220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root      3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root     root       807 Jan  6  2022 .profile
-rwsr-x---  1 bandit33 bandit32 15128 Oct  5 06:19 uppershell
$ whoiam
sh: 3: whoiam: Permission denied
$ whoami
bandit33
$ cat /etc/bandit_pass/bandit33
odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
$ 



bandit33@bandit:~$ ls
README.txt
bandit33@bandit:~$ cat README.txt
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
bandit33@bandit:~$ 

```

## Notas adicionales

Linux tiene variables llamadas variables locales (válidas en el shell actual), variables de shell (configuradas por el shell) y variables de entorno (válidas en todo el sistema). Estas variables tienen sus nombres sólo en mayúsculas. Se definen escribiendo VAR_NAME=var_value en la línea de comando. Para ver el contenido de una variable, puedes escribir echo $VAR_NAME.

Para imprimir todas las variables de entorno, puede utilizar printenv.

Algunos comunes que es bueno saber son:

     TERM - emulación de terminal actual
     HOME: la ruta al directorio de inicio del usuario                 actualmente conectado
     LANG: configuración regional actual
     PATH: lista de directorios que se buscarán al ejecutar            comandos
     PWD: nombre de ruta del directorio de trabajo actual
     SHELL/0 - la ruta del shell del usuario actual
     USER: usuario actualmente conectado


Lo único que está en mayúsculas en Linux son las variables. Específicamente, la variable $0 tiene una referencia a un shell. Puedes ver esto con echo $0 en tu máquina

Podemos ver que el archivo 'uppershell' se ejecuta como bandit33 (propiedad del usuario 'bandit33' y SUID). Al comprobar esto, podemos ver que en realidad somos 'bandit33' y por lo tanto, podemos leer el archivo de contraseña:

## Referencias 


https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux-es
