## Descripcion 

¿Puedes descifrar la contraseña para obtener la bandera? Descargue el verificador de contraseñas aquí y también necesitará la bandera cifrada en el mismo directorio.
## Solucion

zeroone1233-picoctf@webshell:~$ ls
level2.flag.txt.enc  level2.py
zeroone1233-picoctf@webshell:~$ vim level2.py
zeroone1233-picoctf@webshell:~$ python3 level2.py
Please enter correct password for flag: 49ce
That password is incorrect
zeroone1233-picoctf@webshell:~$ python3 level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
zeroone1233-picoctf@webshell:~$ 

def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65)
39ce

51 + 57 + 99 + 101
49ce
## Notas adicionales

Usamos un convertir de hexadecimales
