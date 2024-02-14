## Objetivo 
La contraseña para el siguiente nivel se almacena en un archivo llamado **readme** ubicado en el directorio de inicio. Utilice esta contraseña para iniciar sesión en bandit1 mediante SSH. Siempre que encuentres una contraseña para un nivel, usa SSH (en el puerto 2220) para iniciar sesión en ese nivel y continuar el juego.
## Datos de acceso al nivel
user bandit1

## Solucion

```
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
bandit0@bandit:~$ 

```
## Notas adicionales

**Listar archivos** (ls) Si introduce el comando ls solamente, éste listará todos los archivos situados en la posición actual. 

**Cat**  es la abreviatura de **concatenar**. Esto se refiere al hecho de que cat puede ser utilizado para combinar múltiples archivos en un archivo, también se puede utilizar para crear nuevos archivos y para mostrar el contenido de los archivos existentes.
Con estos comandos podemos entrar al archivo readme y ver el password NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL  
## Referencias 

https://man7.org/linux/man-pages/man1/ls.1.html

https://man7.org/linux/man-pages/man1/cat.1.html