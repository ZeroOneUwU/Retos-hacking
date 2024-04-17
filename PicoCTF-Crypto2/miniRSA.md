## Objetivo

Let's decrypt this: [ciphertext](https://jupiter.challenges.picoctf.org/static/eb5e6df8e14c52873cf88c582a1a4008/ciphertext)? Something seems a bit small.
## Pistas
## Solución

Creamos un programa en python
for t in range(10000):
        m, tr = iroot(n * t + c, e)
        if tr:
                print("Encontr t =", t)
                print("Mensaje   =", bytes.fromhex(hex(m)[2:]))
                break
con este ciclo


──(kali㉿kali)-[~/Documents/PicoCTF/minirsa]
└─$ python3 eploit.py 


Encontr t = 0
Mensaje   = b'picoCTF{n33d_a_lArg3r_e_d0cd6eae}'


## Notas adicionales
## Referencias