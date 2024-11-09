## Objetivo

La bandera está en algún lugar de esta aplicación web, no necesariamente en el sitio web. Encuéntralo. Mira esto.
## Pistas
## Solución

http://saturn.picoctf.net:62370

Vemos que podemos conseguir con robots

http://saturn.picoctf.net:62370/robots.txt


User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/


ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==

Vemos que esta parte traducida en base64 nos dice:
flag1.txtjs/myfi
js/myfile.txt

Entonces intentamos esto:
http://saturn.picoctf.net:62370/js/myfile.txt

picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}
## Notas adicionales
## Referencias