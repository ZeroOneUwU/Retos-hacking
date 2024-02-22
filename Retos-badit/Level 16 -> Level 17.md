## Objetivo 

Las credenciales para el siguiente nivel se pueden recuperar enviando la contraseña del nivel actual a un puerto en localhost en el rango 31000 a 32000. Primero averigüe cuál de estos puertos tiene un servidor escuchando en ellos. Luego averigüe cuáles de ellos hablan SSL y cuáles no. Solo hay 1 servidor que le dará las siguientes credenciales, los demás simplemente le enviarán todo lo que les envíe.

## Datos de acceso al nivel

user bandit16
password - JQttfApK4SeyHwDlI9SXGR50qclOAil1
## Solucion

```
/////////////////////////

bandit16@bandit:~$ nmap -p 31000-32000 localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2024-02-21 18:27 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds
bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)

bandit15@bandit:~$ openssl s_client -connect localhost:31790


┌──(kali㉿kali)-[~/Documents/CIberseguridad]
└─$ chmod 600 lallave.txt
                                                                                                 
┌──(kali㉿kali)-[~/Documents/CIberseguridad]
└─$ ls -la lallave.txt
-rw------- 1 kali kali 1675 Feb 21 13:31 lallave.txt
                                                                                                 
┌──(kali㉿kali)-[~/Documents/CIberseguridad]
└─$ ssh -i lallave.txt bandit17@bandit.labs.overthewire.org -p 2220

bandit17@bandit:~$  cat /etc/bandit_pass/bandit17
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
bandit17@bandit:~$ 





```

## Notas adicionales

El escaneo de puertos es un método para encontrar puertos abiertos en un host. Un puerto puede verse como una dirección para un servicio específico. Cada computadora tiene puertos con los números del 0 al 65535. Algunos servicios tienen puertos estándar, como HTTP/80 o SSH/22. Un puerto abierto significa que el host ofrece un servicio a la red en este puerto.

Nmap -> es un escáner de red. Puede realizar descubrimiento de host, escaneo de puertos, detección de versiones (detección de servicios) y mucho más. 
La bandera -p es importante. Esta bandera nos permite elegir qué puertos escanear. De forma predeterminada, Nmap escanea los 1000 puertos principales (no los primeros 1000 puertos). 
Utilice p- para escanear todos los puertos 65535. El indicador -sV nos permite realizar un análisis de detección de servicio/versión. Es posible hacer que Nmap realice todos los análisis posibles con el indicador -A, aunque esto llevará un tiempo. Un análisis completo tendría el siguiente comando:` nmap -p- -A <host>, donde <host>` podría ser una dirección IP o el nombre.


## Referencias 

https://www.icm.es/2022/05/06/nmap-analisis-de-puertos-y-monitorizacion-de-redes/