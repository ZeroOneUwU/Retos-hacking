## Objetivo 

La contraseña para el siguiente nivel se almacena en un archivo llamado - ubicado en el directorio de inicio
## Datos de acceso al nivel

user bandit1 
password NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
## Solucion

```
bandit1@bandit:~$ ls 
-
bandit1@bandit:~$ cat -

^C
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
bandit1@bandit:~$ pwd
/home/bandit1
bandit1@bandit:~$ cat /home/bandit1/-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
bandit1@bandit:~$ 

```
## Notas adicionales

Este tipo de enfoque genera muchos malentendidos porque el uso - como argumento se refiere a STDIN/STDOUT, es decir, dev/stdin o dev/stdout. Entonces, si desea abrir este tipo de archivo, debe especificar la ubicación completa del archivo, como como ./- .Por ejemplo. , si quieres ver qué hay en ese archivo usa cat ./-

pwd **imprime en pantalla la ruta completa del directorio en el que trabajas**. Este comando sirve especialmente si no quieres perder la visión general de todos los directorios.

Ctrl A -> Manda el cursor al inicio de la linea de comandos 
Ctrl E -> Manda el cursor al inicio de la linea de comandos 

Si un nombre de archivo empieza con - hay que anteponer ./
## Referencias 

https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal

https://tldp.org/LDP/abs/html/special-chars.html

