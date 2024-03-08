## Descripcion 

¿A quién no le encantan las galletas? Intenta descubrir cuál es el mejor. http://mercury.picoctf.net:29649/
## Solucion

┌──(kali㉿kali)-[~]
└─$ for i in {0..20}; do curl -s http://mercury.picoctf.net:29649/check -H "Cookie: name=$i"; done | grep "I love \| PicoCTF"




Con el burp
damos click al check al cargar la pagina
Lo enviamos al repeatr
le damos hasta encontrar la bandera
(name = 28)
click en send 
y en la respuesta lo buscamos

picoCTF{3v3ry1_l0v3s_c00k135_a1f5bdb7}

## Notas adicionales
