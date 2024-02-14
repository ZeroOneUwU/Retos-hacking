## Objetivo 

La contraseña para el siguiente nivel se almacena en un archivo llamado espacios en este nombre de archivo ubicado en el directorio de inicio.
## Datos de acceso al nivel

user bandit2 
pass rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
## Solucion
```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
bandit2@bandit:~$ cat spaces\ in\ this\ filename
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
bandit2@bandit:~$ 
```
## Notas adicionales

Cuando intento usar el comando cat paces in this filename, no entiende que paces in this filename es un argumento único. Trata apaces in this filename como nombres de archivos diferentes.
Para usar un nombre de archivo con espacios, puede encerrarlo entre comillas como esta:
```
cat "paces in this filename"
```
o

```
cat paces/ in/ this/filename
```

para poder entrar a archivos con espacios

Ctrl L -> Borrar la pantalla de la terminal

## Referencias 

https://linuxhandbook.com/filename-spaces-linux/