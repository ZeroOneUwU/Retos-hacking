## Objetivo 

Hay un repositorio git en ssh://bandit28-git@localhost/home/bandit28-git/repo a través del puerto 2220. La contraseña para el usuario bandit28-git es la misma que para el usuario bandit28.

Clona el repositorio y busca la contraseña para el siguiente nivel.

## Datos de acceso al nivel

user bandit28
AVanL161y9rsbcJIsFHuw35rjaOM19nR
## Solucion

```

bandit28@bandit:/tmp/bandit28_tmp/repo$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit28/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password: 
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
bandit28@bandit:/tmp/bandit28_tmp/repo$ ls
README.md  repo
bandit28@bandit:/tmp/bandit28_tmp/repo$ cd repo
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ ls
README.md
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ git log
commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    fix info leak

commit f08b9cc63fa1a4602fb065257633c2dae6e5651b
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    add missing data

commit a645bcc508c63f081234911d2f631f87cf469258
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    initial commit of README.md
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ git show 14f754b3ba6531a2b89df6ccae6446e8969a41f3 commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3
fatal: ambiguous argument 'commit': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ git show 14f754b3ba6531a2b89df6ccae6446e8969a41f3 
commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    fix info leak

diff --git a/README.md b/README.md
index b302105..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
+- password: xxxxxxxxxx
 
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ 


/////////////////////////2 OP//////


bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ git log
commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3 (HEAD, origin/master, origin/HEAD, master)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    fix info leak

commit f08b9cc63fa1a4602fb065257633c2dae6e5651b
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    add missing data

commit a645bcc508c63f081234911d2f631f87cf469258
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    initial commit of README.md
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ git checkout f08b9cc63fa1a4602fb065257633c2dae6e5651b
Previous HEAD position was 14f754b fix info leak
HEAD is now at f08b9cc add missing data
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ ls
README.md
bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S

bandit28@bandit:/tmp/bandit28_tmp/repo/repo$ 


```

## Notas adicionales

La introducción a Git se puede encontrar en el Nivel 28. Para este nivel, necesitamos conocer dos comandos adicionales:

`git log` -> nos muestra el registro de confirmación.
`git show <commit>` -> nos muestra el contenido de una confirmación (al crear un repositorio público es importante tener en cuenta la información que envía, ya que se guardan los cambios y las versiones anteriores. Por lo tanto, los datos confidenciales, como las contraseñas, aún podrían estar almacenados). recuperado).

Además: el archivo README a menudo está escrito en formato Markdown. 
## Referencias 


https://www.atlassian.com/es/git/glossary