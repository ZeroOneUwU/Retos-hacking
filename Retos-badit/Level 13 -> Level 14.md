## Objetivo 

La contraseña para el siguiente nivel se almacena en /etc/bandit_pass/bandit14 y solo puede ser leída por el usuario bandit14. Para este nivel, no obtiene la siguiente contraseña, pero obtiene una clave SSH privada que puede usarse para iniciar sesión en el siguiente nivel. 
Nota: localhost es un nombre de host que se refiere a la máquina en la que está trabajando
## Datos de acceso al nivel

user bandit13
password - wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
## Solucion

```
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).


bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
bandit14@bandit:~$ 




```

## Notas adicionales


ssh -i -> Para entrar con llave  
_SSH_ es un programa que permite acceder a otro ordenador a través de la red, ejecutar comandos en la máquina remota y mover ficheros entre dos máquinas. Provee autenticación y comunicaciones seguras sobre canales inseguros. 

_SSH_
El comando **ssh** ofrece comunicación encriptada y segura entre dos sistemas sobre una red no segura. Este comando reemplaza al **telnet**, **rlogin**, **rsh**.

Para iniciar una sesión en otra máquina usando **ssh**:

La sintaxis básica del comando **ssh** es:

| ssh user@hostname [command]  |
|---|
| |
## Referencias 

https://www3.uji.es/~galdu/ssh_vs_rsh/x165.html