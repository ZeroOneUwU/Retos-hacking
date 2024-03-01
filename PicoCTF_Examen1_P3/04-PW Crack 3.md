## Descripcion 

¿Puedes descifrar la contraseña para obtener la bandera? Descargue el verificador de contraseñas aquí y también necesitará la bandera cifrada y el hash en el mismo directorio. Hay 7 contraseñas potenciales y 1 es correcta. Puede encontrarlos examinando el script de verificación de contraseñas.
## Solucion

`zeroone1233-picoctf@webshell:~$ python3 level3.py`
`Please enter correct password for flag: 6997`
`That password is incorrect`
`zeroone1233-picoctf@webshell:~$ python3 level3.py`
`Please enter correct password for flag: f0ac`
`That password is incorrect`
`zeroone1233-picoctf@webshell:~$ python3 level3.py`
`Please enter correct password for flag: 4b17`
`That password is incorrect`
`zeroone1233-picoctf@webshell:~$ python3 level3.py`
`Please enter correct password for flag: ec27`
`That password is incorrect`
`zeroone1233-picoctf@webshell:~$ python3 level3.py`
`Please enter correct password for flag: 865e`
`Welcome back... your flag, user:`
`picoCTF{m45h_fl1ng1ng_2b072a90}`
`zeroone1233-picoctf@webshell:~$` 



level_3_pw_check()

The strings below are 7 possibilities for the correct password. (Only 1 is correct)
 
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]


00000000  1B 18 E1 31 6F 92 18 CC 5B 05 3E 1C EA 28 E0 2E           ...1o...[.>..(..

## Notas adicionales

bvi para entrar a los hash
