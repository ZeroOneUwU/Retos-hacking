## Objetivo
## Pistas
## Solución

```


Username	investigator
Password	TryHackMe123!

investigator@ip-10-10-146-188:~$ export PATH=/mnt/usb/bin:/mnt/usb/sbin
investigator@ip-10-10-146-188:~$ export LD_LIBRARY_PATH=/mnt/usb/lib:/mnt/usb/
lib64
investigator@ip-10-10-146-188:~$ check-env
THM{5514ec4f1ce82f63867806d3cd95dbd8}
investigator@ip-10-10-146-188:~$ 


----------------------------


investigator@ip-10-10-146-188:/home/bob$ cd ../
investigator@ip-10-10-146-188:/home/bob$ ls
investigator@ip-10-10-146-188:/home/bob$ cd bob/
investigator@ip-10-10-146-188:/home/bob$ ls -al
investigator@ip-10-10-146-188:/home/bob$ find / -user bob -type f -cmin -1
investigator@ip-10-10-146-188:/home/bob$ find / -type f -cmin -1 -user bob 2>/dev/null 
investigator@ip-10-10-146-188:/home/bob$ cat /var/tmp/findme.txt
THM{0b1313afd2136ca0faafb2daa2b430f3}


investigator@ip-10-10-146-188:/$ sudo su
[sudo] password for investigator: 
root@ip-10-10-146-188:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
root@ip-10-10-146-188:/# cd var 
root@ip-10-10-146-188:/var# ls
backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp  www
root@ip-10-10-146-188:/var# cd www
root@ip-10-10-146-188:/var/www# ls
html
root@ip-10-10-146-188:/var/www# cd html
root@ip-10-10-146-188:/var/www/html# ls
assets  index.html  upload.php  uploads
root@ip-10-10-146-188:/var/www/html# cd assets
root@ip-10-10-146-188:/var/www/html/assets# ls
reverse.elf
root@ip-10-10-146-188:/var/www/html/assets# 

root@ip-10-10-146-188:/var/www/html/assets# exiftool reverse.elf
ExifTool Version Number         : 11.88
File Name                       : reverse.elf
Directory                       : .
File Size                       : 250 bytes
File Modification Date/Time     : 2024:02:13 00:26:28+00:00
File Access Date/Time           : 2024:11:07 03:37:27+00:00
File Inode Change Date/Time     : 2024:02:13 00:34:50+00:00
File Permissions                : rwxr-xr-x
File Type                       : ELF executable
File Type Extension             : 
MIME Type                       : application/octet-stream
CPU Architecture                : 64 bit
CPU Byte Order                  : Little endian
Object File Type                : Executable file
CPU Type                        : AMD x86-64
root@ip-10-10-146-188:/var/www/html/assets# 


root@ip-10-10-146-188:/home# ls
bob  investigator  jane  ubuntu
root@ip-10-10-146-188:/home# stat /etc/hosts
  File: /etc/hosts
  Size: 221       Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713dInode: 49          Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-11-07 02:44:36.996000000 +0000
Modify: 2020-10-26 21:10:44.000000000 +0000
Change: 2020-10-26 23:32:25.957900650 +0000
 Birth: -
root@ip-10-10-146-188:/home# 


-------------------------

root@ip-10-10-146-188:/home# cat /etc/passwd
.....
b4ckd00r3d:x:0:1004::/home/b4ckd00r3d:/bin/sh
root@ip-10-10-146-188:/home# 

root@ip-10-10-146-188:/home# cat /etc/group
......
video:x:44:ubuntu,investigator
sasl:x:45:
plugdev:x:46:ubuntu,investigator

root@ip-10-10-146-188:/home# cat /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaultsenv_reset
Defaultsmail_badpass
Defaultssecure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
rootALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudoALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

jane ALL=(ALL) /usr/bin/pstree
root@ip-10-10-146-188:/home# 


------------------------

root@ip-10-10-146-188:/home# ls
bob  investigator  jane  ubuntu
root@ip-10-10-146-188:/home# cd jane/
root@ip-10-10-146-188:/home/jane# ls
root@ip-10-10-146-188:/home/jane# ls -al
total 32
drwxr-xr-x 4 jane jane 4096 Feb 13  2024 .
drwxr-xr-x 6 root root 4096 Feb 12  2024 ..
-rw------- 1 jane jane  317 Feb 13  2024 .bash_history
-rw-r--r-- 1 jane jane  220 Feb 12  2024 .bash_logout
-rw-r--r-- 1 jane jane 3771 Feb 12  2024 .bashrc
drwx------ 2 jane jane 4096 Feb 12  2024 .cache
-rw-r--r-- 1 jane jane  807 Feb 12  2024 .profile
drwxr-xr-x 2 jane jane 4096 Feb 12  2024 .ssh
root@ip-10-10-146-188:/home/jane# cat .bash_history
whoami
groups
cd ~
ls -al
find / -perm -u=s -type f 2>/dev/null
/usr/bin/python3.8 -c 'import os; os.execl("/bin/sh", "sh", "-p", "-c", "cp /bin/bash /var/tmp/bash && chown root:root /var/tmp/bash && chmod +s /var/tmp/bash
")'
ls -al /var/tmp
exit
useradd -o -u 0 b4ckd00r3d
exit
THM{f38279ab9c6af1215815e5f7bbad891b}
root@ip-10-10-146-188:/home/jane# 


root@ip-10-10-146-188:/home# ls
bob  investigator  jane  ubuntu
root@ip-10-10-146-188:/home# cd bob
root@ip-10-10-146-188:/home/bob# ls
root@ip-10-10-146-188:/home/bob# ls -al
total 36
drwxr-xr-x 4 bob  bob  4096 Feb 12  2024 .
drwxr-xr-x 6 root root 4096 Feb 12  2024 ..
-rw-r--r-- 1 bob  bob   220 Feb 12  2024 .bash_logout
-rw-r--r-- 1 bob  bob  3771 Feb 12  2024 .bashrc
drwx------ 2 bob  bob  4096 Feb 12  2024 .cache
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden21
.....
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden31
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden32
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden33
-rw-rw-r-- 1 bob  bob    38 Feb 12  2024 .hidden34
.....
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden9
drwxrwxr-x 3 bob  bob  4096 Feb 12  2024 .local
-rw-r--r-- 1 bob  bob   807 Feb 12  2024 .profile
-rw-rw-r-- 1 bob  bob    66 Feb 12  2024 .selected_editor
root@ip-10-10-146-188:/home/bob# cat .hidden34
THM{6ed90e00e4fb7945bead8cd59e9fcd7f}
root@ip-10-10-146-188:/home/bob# 

root@ip-10-10-146-188:/home# cd jane
root@ip-10-10-146-188:/home/jane# ls
root@ip-10-10-146-188:/home/jane# ls -al
total 32
drwxr-xr-x 4 jane jane 4096 Feb 13  2024 .
drwxr-xr-x 6 root root 4096 Feb 12  2024 ..
-rw------- 1 jane jane  317 Feb 13  2024 .bash_history
-rw-r--r-- 1 jane jane  220 Feb 12  2024 .bash_logout
-rw-r--r-- 1 jane jane 3771 Feb 12  2024 .bashrc
drwx------ 2 jane jane 4096 Feb 12  2024 .cache
-rw-r--r-- 1 jane jane  807 Feb 12  2024 .profile
drwxr-xr-x 2 jane jane 4096 Feb 12  2024 .ssh
root@ip-10-10-146-188:/home/jane# cd .ssh
root@ip-10-10-146-188:/home/jane/.ssh# ls
authorized_keys  id_rsa  id_rsa.pub
root@ip-10-10-146-188:/home/jane/.ssh# cat authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQD1a8StkAtopiMgFLPyHaETqxKQYetG6h3YoY09wUssYKY0anbSGRBfDC7PdTiTju81YeDvqh7JLo2ToN3Uu6Kv8EVaBIyM6mT4LldNafnMVMxGnnUgG8lmBS
NeLGDjLjgV7DC8PvsTqsUMVY1qVX6k6gYsZTWzRsDvk/uCTdGqMlOSGKQG912y35INEo9HATgM+sGThRaDswXNml+ENjGXY63ohqhe7XEAdr+692nPiQ4o0nl8xR6er+75zi4h1Hrk3GER5eRRehMpP5YWiiwe
W9tiIPR2K7KXgbPBor3Ppi7jHsyu8lh2bejovLHbR06Onjb7MQdyLHn+3TMvKIG2gC7y3UgStmE3hLyuewlpBwWdVhzJojGGoO31j9RzFrFA8GzBxMTaeoEooZonzsiwS67f0m61L9zmXVYTxhisGr98G41iV+
hiXguvoI+wZKqtJzxm2Hwt2OhzSWCt30ovOw1aHdsVVaCO3gXbetnBcyXEaTldRcVPKDKhi5S2OnltpIyDUuiOitz52lCU+kC1P2pVHaFYLtSaQtBbJlMgcrKf8m0+3wDYloc/wx4kQa7bGEqcU5BfUk58wqii
acSzGM1yIDmV/oXpS5ysbVADRBrVjvY1VtGMrntrAzJ2VidWT+bBdI9GLtrX/8eEIR4cUklv1DUrcrJ+q4GbgX90Uw== jane@ip-10-10-25-169
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDE+QX6Zf8Lhyy+VAkwF9ATyW5FXsW3uE3b9s/DCnaiEJX39I59Vpiy5h8QM9FajO/GLhLHcQS7YI8AkYHpYgw2PUTZUcBb2dWtEd8YbXZd6IzQAdhxZZX2xx
siN1XdzF4uW1xzfsD/xAaEuXWs7zNjCN6bja+HhfmClghjFlg8TOCQbeeZooVXJ+SklRnp7MX9dk5ceLoU0Fv1VHQ7yOQHUeBochHRCexWLZJm+9otO7y0xn93VVMT+qnbqnV4hbprx1GNd5WaVlATjE9juxf8
zAXywpusvK8BuRnBiEQxAUQ0dBSaCg/mn5ffz5o07qPYNL+kByoTZFMdHaUkdHzD backdoor
root@ip-10-10-146-188:/home/jane/.ssh# stat authorized_keys
  File: authorized_keys
  Size: 1136      Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713dInode: 257561      Links: 1
Access: (0666/-rw-rw-rw-)  Uid: ( 1002/    jane)   Gid: ( 1002/    jane)
Access: 2024-11-07 03:52:39.792000000 +0000
Modify: 2024-02-13 00:34:16.005897449 +0000
Change: 2024-02-13 00:34:16.005897449 +0000
 Birth: -
root@ip-10-10-146-188:/home/jane/.ssh# 

root@ip-10-10-146-188:/home/investigator# debsums --help
debsums checks the MD5 sums of installed debian packages.

Usage: debsums [OPTIONS] [PACKAGE|DEB] ...

Options:
 -a, --all                    check configuration files (normally excluded)
 -e, --config                 check only configuration files
 -c, --changed                report changed files (implies -s)
 -l, --list-missing           list packages which don't have an md5sums file
 -s, --silent                 only report errors
 -m, --md5sums=FILE           read list of deb checksums from FILE
 -x, --report-mismatches      report errors and print the md5sums mismatch
 -r, --root=DIR               root directory to check (default /)
 -d, --admindir=DIR           dpkg admin directory (default /var/lib/dpkg)
 -p, --deb-path=DIR[:DIR...]  search path for debs
 -g, --generate=[all][,keep[,nocheck]]
                              generate md5sums from deb contents
     --no-locale-purge        report missing locale files even if localepurge
                              is configured
     --no-prelink             report changed ELF files even if prelink is
                              configured
     --ignore-obsolete        ignore obsolete conffiles.
     --help                   print this help, then exit
     --version                print version number, then exit
root@ip-10-10-146-188:/home/investigator# 

root@ip-10-10-146-188:/etc# debsums -c -e
/etc/sudoers
root@ip-10-10-146-188:/etc# 

root@ip-10-10-146-188:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
root@ip-10-10-146-188:/# cd etc/
root@ip-10-10-146-188:/etc# ls
NetworkManager                 cron.hourly           gshadow              lighttpd        netplan                  rc0.d          subuid
PackageKit                     cron.monthly          gshadow-             locale.alias    network                  rc1.d          subuid-
X11                            cron.weekly           gss                  locale.gen      networkd-dispatcher      rc2.d          sudoers
acpi                           crontab               hdparm.conf          localtime       networks                 rc3.d          sudoers.d
adduser.conf                   cryptsetup-initramfs  hibagent-config.cfg  logcheck        newt                     rc4.d          sysctl.conf
aliases                        crypttab              hibinit-config.cfg   login.defs      nsswitch.conf            rc5.d          sysctl.d
alternatives                   dbus-1                host.conf            logrotate.conf  opt                      rc6.d          systemd
apache2                        dconf                 hostname             logrotate.d     os-release               rcS.d          terminfo
apparmor                       debconf.conf          hosts                lsb-release     overlayroot.conf         resolv.conf    timezone
apparmor.d                     debian_version        hosts.allow          ltrace.conf     overlayroot.local.conf   resolvconf     tmpfiles.d
apport                         default               hosts.deny           lvm             pam.conf                 rkhunter.conf  ubuntu-advantage
apt                            deluser.conf          init.d               machine-id      pam.d                    rmt            ucf.conf
at.deny                        depmod.d              initramfs-tools      magic           passwd                   rpc            udev
bash.bashrc                    dhcp                  inputrc              magic.mime      passwd-                  rsyslog.conf   ufw
bash_completion                dpkg                  insserv.conf.d       mail.rc         perl                     rsyslog.d      update-manager
bash_completion.d              e2scrub.conf          iproute2             mailcap         php                      screenrc       update-motd.d
bindresvport.blacklist         ec2_version           iscsi                mailcap.order   pki                      security       update-notifier
binfmt.d                       environment           issue                manpath.config  pm                       selinux        vim
byobu                          ethertypes            issue.net            mdadm           polkit-1                 services       vmware-tools
ca-certificates                fonts                 kernel               mime.types      pollinate                shadow         vtrgb
ca-certificates.conf           fstab                 kernel-img.conf      mke2fs.conf     popularity-contest.conf  shadow-        wgetrc
ca-certificates.conf.dpkg-old  fuse.conf             landscape            modprobe.d      postfix                  shells         xattr.conf
calendar                       fwupd                 ld.so.cache          modules         ppp                      skel           xdg
chkrootkit.conf                gai.conf              ld.so.conf           modules-load.d  profile                  sos            zsh_command_not_found
cloud                          groff                 ld.so.conf.d         mtab            profile.d                ssh
console-setup                  group                 ldap                 multipath       protocols                ssl
cron.d                         group-                legal                multipath.conf  python3                  subgid
cron.daily                     grub.d                libaudit.conf        nanorc          python3.8                subgid-
root@ip-10-10-146-188:/etc# md5sum /var/tmp/bash
7063c3930affe123baecd3b340f1ad2c  /var/tmp/bash
root@ip-10-10-146-188:/etc# 

--------------------

root@ip-10-10-146-188:/# sudo chkrootkit

................
Searching for Mumblehard Linux ...                          * * * * * /var/tmp/findme.sh
Possible Mumblehard backdoor installed

root@ip-10-10-146-188:/# sudo rkhunter --check --sk --rwo | grep UID
root@ip-10-10-146-188:/# sudo rkhunter --check --sk --rwo | grep UID
 : Account 'b4ckd00r3d' is root equivalent (UID = 0)
root@ip-10-10-146-188:/# 


```
## Notas adicionales
## Referencias