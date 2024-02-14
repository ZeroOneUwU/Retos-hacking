## Objetivo 

La contraseña para el siguiente nivel se almacena **en algún lugar del servidor** y tiene todas las siguientes propiedades:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size
## Datos de acceso al nivel

user  bandit6 
password - P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

## Solucion

```bash
bandit6@bandit:~$ ls
bandit6@bandit:~$ ls -la
total 20
drwxr-xr-x  2 root root 4096 Oct  5 06:19 .
drwxr-xr-x 70 root root 4096 Oct  5 06:20 ..
-rw-r--r--  1 root root  220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root root 3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root root  807 Jan  6  2022 .profile
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
bandit6@bandit:~$ 
```
## Notas adicionales

En este nivel, se nos presenta el gran tema de los permisos de archivos de Linux. En concreto, al ámbito de la propiedad. Cada archivo es propiedad de un usuario y un grupo. Puede ver qué usuario y grupo posee un archivo con el comando ls y su etiqueta -l.

Ejemplo:

```
1 bandit6@bandit:/var/lib/dpkg/info$ ls -l bandit7.password 
2 -rw-r----- 1 bandit7 bandit6 33 May  7  2020 bandit7.password
```

La tercera columna muestra el usuario, la cuarta muestra el grupo propietario del archivo.

El comando **find** se puede utilizar para buscar archivos en el servidor. Ofrece indicadores para buscar archivos propiedad de un **usuario específico** `(-user <username>)` y un **grupo específico** `(-group <groupname>).`

Necesitamos ejecutar el comando desde el directorio raíz para buscar en todo el sistema. Sin embargo, ejecutar el comando find / -type f -user bandit7 -group bandit6 -size 33c también imprimirá un error de Permiso denegado para los archivos para los que no tenemos permiso. 

**Podemos agregar 2>/dev/null, que "ocultará" todos los mensajes de error** que enviara la salida de error al dispositivo null


## Referencias

https://www.linux.org/threads/what-does-dev-null-do-in-the-command-line.31573/