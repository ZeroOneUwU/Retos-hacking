## Objetivo 

La contraseña para el siguiente nivel se almacena en un archivo Léame en el directorio de inicio. Desafortunadamente, alguien ha modificado .bashrc para cerrar tu sesión cuando inicias sesión con SSH.
## Datos de acceso al nivel

user bandit18 -
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
## Solucion

```
┌──(kali㉿kali)-[~]
└─$ ssh bandit18@bandit.labs.overthewire.org -p 2220 /bin/bash
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: 
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
/bin/bash: line 1: hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg: command not found

cat readme
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

## Notas adicionales

'.bashrc' -> es un archivo que se ejecuta cada vez que se carga una terminal. Esto significa que también se ejecuta al iniciar sesión a través de SSH porque esto también carga una terminal.

SSH no solo nos permite iniciar sesión en una máquina de forma remota, sino que también permite la ejecución remota de comandos agregando los comandos después de la expresión SSH común.
## Referencias 


https://www.zeppelinux.es/descripcion-y-uso-de-los-archivos-bashrc-y-etc-bashrc/
