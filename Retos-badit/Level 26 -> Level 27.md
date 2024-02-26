## Objetivo 

¡Buen trabajo consiguiendo un caparazón! ¡Ahora date prisa y consigue la contraseña de bandit27!

## Datos de acceso al nivel

user bandit26
pass c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
## Solucion

```

 | |                   | (_) | |__ \ / /  
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
:sh
bandit26@bandit:~$ ls
bandit27-do  text.txt
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ ./bandit27-do id
uid=11026(bandit26) gid=11026(bandit26) euid=11027(bandit27) groups=11026(bandit26)
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
bandit26@bandit:~$ 


```

## Notas adicionales

Una vez que tenemos el shell, podemos encontrar un archivo llamado bandit27-do en el directorio de inicio de bandit26. El nombre sugiere que eso es lo que debemos comprobar.
Podemos simplemente imprimir el archivo de contraseña.
## Referencias 

https://kinsta.com/es/blog/linux-comandos/