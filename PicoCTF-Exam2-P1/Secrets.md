## Objetivo

Tenemos varias páginas ocultas. ¿Puedes encontrar el que tiene la bandera? El sitio web se está ejecutando aquí.
## Pistas
## Solución

Vemos el codigo fuente
Vemos esto: 
        src="[secret/assets/DX1KYM.jpg](view-source:http://saturn.picoctf.net:62315/secret/assets/DX1KYM.jpg)"      
Tratamos esto:

http://saturn.picoctf.net:59342/secret/

Luego volvemos a ver el codigo fuente
Encontramos esto:
link rel="stylesheet" href="[hidden/file.css](view-source:http://saturn.picoctf.net:59342/secret/hidden/file.css)" />
Entramos ahora a esa direccion
http://saturn.picoctf.net:59342/secret/hidden/
Volvemos a ver el codigo fuente
Encontramos esto:
input type="hidden" name="db" value="superhidden/xdfgwd.html" />
Entramos ahora a esa carpeta

https://saturn.picoctf.net/secret/hidden/superhidden/

Vemos de nuevo el codigo fuente 

picoCTF{succ3ss_@h3n1c@10n_790d2615}

## Notas adicionales
## Referencias