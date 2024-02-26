## Objetivo 

Hay un repositorio git en ssh://bandit30-git@localhost/home/bandit30-git/repo a través del puerto 2220. La contraseña para el usuario bandit30-git es la misma que para el usuario bandit30.

Clona el repositorio y busca la contraseña para el siguiente nivel.

## Datos de acceso al nivel

user bandit30
pass xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
## Solucion

```
bandit30@bandit:/tmp/bandit30_ex$ git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo



bandit30@bandit:/tmp/bandit30_ex$ ls
repo
bandit30@bandit:/tmp/bandit30_ex$ cd repo
bandit30@bandit:/tmp/bandit30_ex/repo$ ls
README.md
bandit30@bandit:/tmp/bandit30_ex/repo$ cat README.md
just an epmty file... muahaha
bandit30@bandit:/tmp/bandit30_ex/repo$ git log
commit d39631d73f786269b895ae9a7b14760cbf40a99f (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:45 2023 +0000

    initial commit of README.md
bandit30@bandit:/tmp/bandit30_ex/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
bandit30@bandit:/tmp/bandit30_ex/repo$ git tag
secret
bandit30@bandit:/tmp/bandit30_ex/repo$ git show secret
OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
bandit30@bandit:/tmp/bandit30_ex/repo$ 


```

## Notas adicionales


Git tagging  es una forma de marcar puntos específicos en el historial del repositorio. Un ejemplo sería marcar los puntos de lanzamiento del software.
El comando para ver las etiquetas es **git tag**. 
Para crear una etiqueta, el comando es **git tag -a <tag_name> -m <"tag description/message">**. Para ver más detalles, como el mensaje de etiqueta y la confirmación, puede usar el siguiente comando: **git show <nombre_etiqueta>.


El README no nos proporciona ninguna información. Al revisar la etiqueta git, encontramos un punto en el historial llamado "secret", que parece prometedor.
## Referencias 


https://www.atlassian.com/es/git/glossary