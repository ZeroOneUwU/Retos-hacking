## Objetivo

Encontramos este extraño mensaje transmitiéndose a los servidores, creemos que tenemos un esquema de descifrado que funciona. Descarga el mensaje aquí. Tome cada número mod 37 y asígnelo al siguiente conjunto de caracteres: 0-25 es el alfabeto (mayúscula), 26-35 son los dígitos decimales y 36 es un guión bajo. Envuelva su mensaje descifrado en el formato de bandera picoCTF (es decir, picoCTF{decrypted_message})

## Pistas

## Solución

```
──(kali㉿kali)-[~/Documents/PicoCTF/basic-mod1]
└─$ ls
message.txt
                                       
┌──(kali㉿kali)-[~/Documents/PicoCTF/basic-mod1]
└─$ cat message.txt         
350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213                                                                                                            
┌──(kali㉿kali)-[~/Documents/PicoCTF/basic-mod1]
└─$ ls             
eploit1.py  message.txt
                                    
                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/basic-mod1]
└─$ python3 eploit1.py 
R0UND_N_R0UND_ADD17EC2
                                       
┌──(kali㉿kali)-[~/Documents/PicoCTF/basic-mod1]
└─$ 


datos = open ("message.txt").read().split()
flag = ""
c = ""
for n in datos:
     i = int(n) % 37
     if i>=0 and i<=25:
             c = chr(i + 65)
     elif i>=26 and i<=35: 
             c = chr(i+22)
     elif i==36:
             c = "_"

     flag = flag + c

print(flag)
```
## Notas adicionales
## Referencias