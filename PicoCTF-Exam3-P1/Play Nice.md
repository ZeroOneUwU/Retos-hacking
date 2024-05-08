## Objetivo

Not all ancient ciphers were so bad... The flag is not in standard format. `nc mercury.picoctf.net 19860` [playfair.py](https://mercury.picoctf.net/static/3f082e143dd5b4ffe1a0aaaf317872b8/playfair.py)
## Pistas
## Solución


```                                                                         
┌──(kali㉿kali)-[~/Documents/PicoCTF/Play nice]
└─$ nc mercury.picoctf.net 19860
Here is the alphabet: lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9
Here is the encrypted message: 1x5hqlod8x7oa88h0de1b5r6xja5sd
What is the plaintext message? ^Z
zsh: suspended  nc mercury.picoctf.net 19860
                                                                    

```

Vamos a https://www.dcode.fr/playfair-cipher
Revisamos el programa de python y vemos que tiene un tama;o de 6 la matriz,
entonces en la pagina le damos esa cantidad de resize, ponemos el alfabeto que nos da y el mensaje encriptado 
Ahora volvemos a la consola

```
             
┌──(kali㉿kali)-[~/Documents/PicoCTF/Play nice]
└─$ python -c "print('LHXM62I5LWOI0RLJOR647XQ9WH7WIE'.lower())"
lhxm62i5lwoi0rljor647xq9wh7wie
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Play nice]
└─$ nc mercury.picoctf.net 19860                               
Here is the alphabet: lsi28c14ot0vbf7nagh3mpjuxy5kwz6edqr9
Here is the encrypted message: 1x5hqlod8x7oa88h0de1b5r6xja5sd
What is the plaintext message? lhxm62i5lwoi0rljor647xq9wh7wie
Congratulations! Here's the flag: f391b621282ef5063ab2de93ab9e4bff
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/Play nice]
└─$ 



```
## Notas adicionales
## Referencias