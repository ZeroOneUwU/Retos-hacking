## Objetivo 

La contraseña para el siguiente nivel se almacena en el archivo data.txt, donde todas las letras minúsculas (a-z) y mayúsculas (A-Z) se han rotado 13 posiciones.
## Datos de acceso al nivel

user bandit11
password -6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
## Solucion

```
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi
bandit11@bandit:~$ cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
bandit11@bandit:~$ 
```
## Notas adicionales

tr (traducir)  -> Toma dos conjuntos como entradas, más un flujo de entrada (en este caso su archivo).

Luego toma y busca cada carácter en el flujo de entrada usando el primer conjunto y lo reemplaza con el carácter del segundo conjunto en la misma posición.

Entonces, en esencia, el primer conjunto es A-Z seguido de a-z y el segundo conjunto es N-ZA-M seguido de n-za-m porque eso es a lo que se asigna en ROT13.


## Referencias 

https://es.wikipedia.org/wiki/ROT13
https://www.xataka.com/historia-tecnologica/asi-rot13-algoritmo-cifrado-simple-que-ha-revivido-para-ocultar-spoilers