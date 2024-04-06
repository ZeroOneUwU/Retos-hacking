## Objetivo

Can you get the flag? Go to this [website](http://saturn.picoctf.net:50920/) and see what you can discover.
## Pistas
## Solución

Inspeccionamos la pagina
Nos vamos al depurar
Colocamos cualquier usuario y password
Se genera un archivo secure.js

function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}

Contiene esto, por lo tanto este usuario es el que usaremos 

picoCTF{j5_15_7r4n5p4r3n7_05df90c8}
## Notas adicionales
## Referencias