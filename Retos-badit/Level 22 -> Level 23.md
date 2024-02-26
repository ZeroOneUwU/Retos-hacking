## Objetivo 

Un programa se ejecuta automáticamente a intervalos regulares desde cron, el programador de trabajos basado en el tiempo. Busque en /etc/cron.d/ la configuración y vea qué comando se está ejecutando.

NOTA: Mirar scripts de shell escritos por otras personas es una habilidad muy útil. El guión de este nivel se ha hecho intencionadamente fácil de leer. Si tiene problemas para entender lo que hace, intente ejecutarlo para ver la información de depuración que imprime.

## Datos de acceso al nivel

user bandit22
pass WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff

## Solucion

```
bandit22@bandit:~$ ls
bandit22@bandit:~$ cat /etc/cron.d/
cat: /etc/cron.d/: Is a directory
bandit22@bandit:~$ cat /etc/cron.d
cat: /etc/cron.d: Is a directory
bandit22@bandit:~$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
# You can also override PATH, but by default, newer versions inherit it from the environment
#PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
bandit22@bandit:~$ ls /etc/cron.d
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24       e2scrub_all  sysstat
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root  otw-tmp-dir
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh 
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:~$ cat /tmp/$mytarget
cat: /tmp/: Permission denied
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
bandit22@bandit:~$ 
```

## Notas adicionales


Lo nuevo en esta tarea son las variables en las secuencias de comandos bash. Una variable es como un contenedor para un valor. Para declarar una variable en scripts bash, utilice la siguiente sintaxis: var_name=var_value. Es posible guardar la salida de un comando en una variable con la siguiente sintaxis: var_name=$(comando). Acceda al valor de una variable existente como esta: $var_name

Se observo el script '/usr/bin/cronjob_bandit23.sh', la última línea es similar al nivel 22. Este script solo introduce variables. La primera variable es "myname" y guarda el resultado del comando whoami. Debido a que este script se ejecutará como bandit23, el comando whoami imprimirá 'bandit23'. Entonces, la última línea nos dice que la contraseña de bandit23 se escribirá en un archivo en la carpeta '/tmp'. El nombre del archivo se crea con la línea  echo I user $myname | md5sum | cut -d ' ' -f 1. Sólo necesitamos sustituir $myname por bandit23, ejecutarlo y el resultado es el nombre del archivo.


## Referencias 

https://www.redeszone.net/tutoriales/servidores/cron-crontab-linux-programar-tareas/