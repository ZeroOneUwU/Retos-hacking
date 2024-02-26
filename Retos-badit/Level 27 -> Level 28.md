## Objetivo 

Hay un repositorio git en ssh://bandit27-git@localhost/home/bandit27-git/repo a través del puerto 2220. La contraseña para el usuario bandit27-git es la misma que para el usuario bandit27.

Clona el repositorio y busca la contraseña para el siguiente nivel.

## Datos de acceso al nivel

user bandit27
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS

## Solucion

```

bandit27@bandit:~$ cd /tmp
bandit27@bandit:/tmp$ cd bandit27_certa
-bash: cd: bandit27_certa: No such file or directory
bandit27@bandit:/tmp$ mkdir bandit27_aux
bandit27@bandit:/tmp$ cd bandit27_aux


bandit27@bandit:/tmp/bandit27_aux$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit27/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit27/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit27-git@localhost's password: 
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
bandit27@bandit:/tmp/bandit27_aux$ ls 
repo
bandit27@bandit:/tmp/bandit27_aux$ cd repo
bandit27@bandit:/tmp/bandit27_aux/repo$ ls
README
bandit27@bandit:/tmp/bandit27_aux/repo$ cat README
The password to the next level is: AVanL161y9rsbcJIsFHuw35rjaOM19nR
bandit27@bandit:/tmp/bandit27_aux/repo$ 


```


## Notas adicionales

Git es un sistema de control de versiones distribuido, gratuito y de código abierto” - https://git-scm.com/. Le permite guardar su código, así como el historial y los cambios que ha realizado en su código. También simplifica la colaboración y el trabajo en equipo con el mismo código.

El sistema Git contiene muchos comandos. Algunos de los comandos más esenciales son:

     git init, para crear un nuevo repositorio/proyecto Git
     git clone, para copiar un repositorio git existente
     git push, actualiza el repositorio remoto
     git pull, obtenga actualizaciones desde el repositorio remoto. También es posible utilizar un cliente Git que tenga una GUI para una interacción más sencilla (https://git-scm.com/downloads/guis).

Diferentes servicios le brindan una forma de alojar su repositorio de forma remota (pública o privada). Si está interesado en el código abierto, estos suelen ser también los lugares donde puede obtener el software o contribuir. Los más famosos serían Github y GitLab.

El directorio '.git' contiene toda la información necesaria para el control de versiones. Contiene información sobre confirmaciones, la dirección del repositorio remoto, un registro y más.

El archivo README se encuentra a menudo en un repositorio de git. Se utiliza como una descripción general de todos los archivos en un directorio o el proyecto git. Al crear un proyecto git, un archivo README es útil para recordar de qué se trata el proyecto, así como otra información que los usuarios y desarrolladores puedan necesitar. Por ejemplo, una breve explicación del proyecto, instrucciones de configuración e instalación, información de licencia y más.

## Referencias 

https://www.atlassian.com/es/git/glossary