## Objetivo

In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/2604f8b51a5cc62d38a3736938f19cef/values)

## Pistas
## Solución

```

┌──(kali㉿kali)-[~/Documents/PicoCTF/MInd your Ps and qS]
└─$ cat values    
Decrypt my super sick RSA:
c: 861270243527190895777142537838333832920579264010533029282104230006461420086153423
n: 1311097532562595991877980619849724606784164430105441327897358800116889057763413423
e: 65537                                                                                                           
┌──(kali㉿kali)-[~/Documents/PicoCTF/MInd your Ps and qS]
└─$ python3
Python 3.11.7 (main, Dec  8 2023, 14:22:46) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

$ python3
Python 3.11.7 (main, Dec  8 2023, 14:22:46) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> p = 1955175890537890492055221842734816092141
>>> q = 670577792467509699665091201633524389157003
>>> n = p*q
>>> e=65537
>>> c=861270243527190895777142537838333832920579264010533029282104230006461420086153423
>>> tn = (p-1)*(q-1)
>>> d = pow(e,-1,tn)
>>> m = pow(c,d,e)
>>> bytes.fromhex(hex(m)[2:])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: non-hexadecimal number found in fromhex() arg at position 3
>>> tn
1311097532562595991877980619849724606783491897137083280307201653693412798558164280
>>> d
693529123416505412979446025120625035374876994645029007711823240743237277989774953
>>> m
3247
>>> bytes.fromhex(hex(m)[2:])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: non-hexadecimal number found in fromhex() arg at position 3
>>> bytes.fromhex( hex(m)[2:])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: non-hexadecimal number found in fromhex() arg at position 3
>>> m = pow(c,d,n)
>>> bytes.fromhex( hex(m)[2:])
b'picoCTF{sma11_N_n0_g0od_13686679}'
>>> 
```


## Notas adicionales
## Referencias