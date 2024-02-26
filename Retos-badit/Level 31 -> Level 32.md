## Objetivo 

Hay un repositorio git en ssh://bandit31-git@localhost/home/bandit31-git/repo a través del puerto 2220. La contraseña para el usuario bandit31-git es la misma que para el usuario bandit31.

Clona el repositorio y busca la contraseña para el siguiente nivel.

## Datos de acceso al nivel

user bandit31
pass OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
## Solucion

```

bandit31@bandit:/tmp/bandit31_ex$ ls
repo
bandit31@bandit:/tmp/bandit31_ex$ cd repo
bandit31@bandit:/tmp/bandit31_ex/repo$ ls
README.md
bandit31@bandit:/tmp/bandit31_ex/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/bandit31_ex/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/bandit31_ex/repo$ ls -la
total 24
drwxrwxr-x 3 bandit31 bandit31 4096 Feb 26 01:36 .
drwxrwxr-x 3 bandit31 bandit31 4096 Feb 26 01:32 ..
drwxrwxr-x 8 bandit31 bandit31 4096 Feb 26 01:33 .git
-rw-rw-r-- 1 bandit31 bandit31    6 Feb 26 01:33 .gitignore
-rw-rw-r-- 1 bandit31 bandit31   15 Feb 26 01:36 key.txt
-rw-rw-r-- 1 bandit31 bandit31  147 Feb 26 01:33 README.md


bandit31@bandit:/tmp/bandit31_ex/repo$ ls
key.txt  README.md
bandit31@bandit:/tmp/bandit31_ex/repo$ cat key.txt
May I come in?
bandit31@bandit:/tmp/bandit31_ex/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/bandit31_ex/repo$ ls
key.txt  README.md
bandit31@bandit:/tmp/bandit31_ex/repo$ cat key.txt
May I come in?
bandit31@bandit:/tmp/bandit31_ex/repo$ git add key.txt
bandit31@bandit:/tmp/bandit31_ex/repo$ ls -a
.  ..  .git  .gitignore  key.txt  README.md
bandit31@bandit:/tmp/bandit31_ex/repo$ cat .gitinore
cat: .gitinore: No such file or directory
bandit31@bandit:/tmp/bandit31_ex/repo$ cat .gitinore *.txt
cat: .gitinore: No such file or directory
May I come in?
bandit31@bandit:/tmp/bandit31_ex/repo$ cat .gitignore
*.txt
bandit31@bandit:/tmp/bandit31_ex/repo$ git add -f key.txt
bandit31@bandit:/tmp/bandit31_ex/repo$ git commit -m "Upload key.txt"
[master f32aad3] Upload key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/bandit31_ex/repo$ git push -u origin master
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit31/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 328 bytes | 328.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: rmCBvG56y58BXzv98yZGdO7ATVL5dW8y 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://localhost:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)

```


## Notas adicionales


git commit  -> guarda los cambios realizados actualmente con un mensaje que describe estos cambios. La bandera -a garantiza que todos los archivos modificados/eliminados estén preparados.

git Push -> actualiza los cambios locales en repositorios remotos. Al presionar por primera vez, también debes definir la rama con -u.

git ignore -> es un archivo con el nombre de archivo '.gitignore'. En este archivo, se escriben todos los nombres/extensiones de archivo que la confirmación debe ignorar. Esto significa que si se crea/cambia un archivo que está en el archivo ignorado, no formará parte de la confirmación/repositorio. 
git ignore también permite comodines. (Por ejemplo, '*.pyc' significa que se ignorarán todos los archivos con la terminación '.pyc'). Hay archivos preescritos para situaciones y lenguajes específicos, como este para Python.

git add -> actualiza qué archivos formarán parte de la próxima confirmación. El indicador -f obliga a que los archivos puedan confirmarse, incluso cuando normalmente se ignoran.

El 'README' indica que tenemos que enviar un archivo al repositorio. Entonces primero creamos el archivo:

Se puede intentar enviar el nuevo archivo haciendo primero una confirmación y luego enviándolo. Sin embargo, esto no funcionará debido al archivo ".gitignore" en el repositorio. Este archivo enumera archivos/tipos que git no enviará al repositorio. En este caso, exactamente todos los archivos que terminan en '.txt'.

Para agregar el archivo de todos modos, necesitamos usar git add.
## Referencias 

https://www.atlassian.com/es/git/glossary