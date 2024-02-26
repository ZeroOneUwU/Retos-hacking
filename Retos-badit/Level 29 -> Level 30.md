## Objetivo 

Hay un repositorio git en ssh://bandit29-git@localhost/home/bandit29-git/repo a través del puerto 2220. La contraseña para el usuario bandit29-git es la misma que para el usuario bandit29.

Clona el repositorio y busca la contraseña para el siguiente nivel.

## Datos de acceso al nivel

user bandit29
pass tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
## Solucion

```
bandit29@bandit:/tmp/bandit29_ex$ ls
repo
bandit29@bandit:/tmp/bandit29_ex$ cd repo
bandit29@bandit:/tmp/bandit29_ex/repo$ ls
README.md
bandit29@bandit:/tmp/bandit29_ex/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/bandit29_ex/repo$ git log 
commit 4364630b3b27c92aff7b36de7bb6ed2d30b60f88 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:43 2023 +0000

    fix username

commit fca34ddb7d1ff1f78df36538252aea650b0b040d
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:43 2023 +0000

    initial commit of README.md
bandit29@bandit:/tmp/bandit29_ex/repo$ git checkout^C
bandit29@bandit:/tmp/bandit29_ex/repo$ git checkout 4364630b3b27c92aff7b36de7bb6ed2d30b60f88
Note: switching to '4364630b3b27c92aff7b36de7bb6ed2d30b60f88'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 4364630 fix username
bandit29@bandit:/tmp/bandit29_ex/repo$ ls
README.md
bandit29@bandit:/tmp/bandit29_ex/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/bandit29_ex/repo$ git branch -a
* (HEAD detached at 4364630)
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/bandit29_ex/repo$ git checkout remotes/origin/dev
Previous HEAD position was 4364630 fix username
HEAD is now at 1d160de add data needed for development
bandit29@bandit:/tmp/bandit29_ex/repo$ ls
code  README.md
bandit29@bandit:/tmp/bandit29_ex/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS

bandit29@bandit:/tmp/bandit29_ex/repo$ 


```

## Notas adicionales

Git branching es otra característica del sistema de control de versiones. Permite dividir el desarrollo en diferentes ramas. En concreto, existe una rama maestra de la que se puede tomar el software y trabajar en él por separado. Puede cambiar y agregar funciones mientras mantiene una rama maestra en funcionamiento. Una vez realizado el trabajo, se puede integrar nuevamente en la rama maestra. Esto permite un control de versiones adicional. Puede ofrecer una rama de producción con software utilizable, mientras corrige errores o agrega funciones en una rama de desarrollo diferente.

Los comandos básicos para trabajar con ramas son:

    git branch`: List (`-a`), create, or delete branches
-   `git checkout <branch_name>/git switch <branch_name>`: Switch branches (cambiar de rama)
-  ` git merge`: Join two or more branches (unir dos o más ramas)

## Referencias 

https://www.atlassian.com/es/git/glossary