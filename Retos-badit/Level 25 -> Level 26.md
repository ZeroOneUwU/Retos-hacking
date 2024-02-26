## Objetivo 

Iniciar sesión en bandit26 desde bandit25 debería ser bastante fácil... El shell para el usuario bandit26 no es /bin/bash, sino algo más. Descubra qué es, cómo funciona y cómo salir de él.

## Datos de acceso al nivel

user bandit25
pass p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
## Solucion


```

bandit25@bandit:~$ ls -l
total 4
-r-------- 1 bandit25 bandit25 1679 Oct  5 06:19 bandit26.sshkey
bandit25@bandit:~$ 
bandit25@bandit:~$ ls
bandit26.sshkey
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$ cat :/usr/bin/showtext
cat: ':/usr/bin/showtext': No such file or directory
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0


  _                     _ _ _   ___   __  
 | |                   | (_) | |__ \ / /  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
:set shell=/bin/bash
:sh
bandit26@bandit:~$ id
uid=11026(bandit26) gid=11026(bandit26) groups=11026(bandit26)
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
bandit26@bandit:~$ 


```


## Notas adicionales

Cada usuario tiene un shell predeterminado de usuario. Esto es especialmente importante cuando se utiliza ssh, porque este es el shell que se mostrará. La información sobre qué shell es el predeterminado para un usuario se puede encontrar al final de la línea del usuario en el archivo '/etc/passwd'.

more -> es un comando de shell que permite la visualización de archivos en modo interactivo. Específicamente, este modo interactivo solo funciona cuando el contenido del archivo es demasiado grande para mostrarse por completo en la ventana del terminal. Un comando permitido en el modo interactivo es v. Este comando abrirá el archivo en el editor "vim".

Vim es un editor de texto. También le permite ejecutar comandos de shell. Es posible utilizar vim para salir de un entorno restringido y generar un caparazón. Para generar el shell predeterminado del usuario, se utiliza el comando :shell. Para cambiar el shell a '/bin/bash', el comando es: set shell=/bin/bash.

## Referencias 

https://www.neoguias.com/comando-more-linux/
