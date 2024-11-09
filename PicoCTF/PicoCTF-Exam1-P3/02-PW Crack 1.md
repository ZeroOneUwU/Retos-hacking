## Descripcion 

¿Puedes descifrar la contraseña para obtener la bandera? Descargue el verificador de contraseñas aquí y también necesitará la bandera cifrada en el mismo directorio.

## Solucion

zeroone1233-picoctf@webshell:~$ ls  
level1.flag.txt.enc  level1.py
zeroone1233-picoctf@webshell:~$ vim level1.py
zeroone1233-picoctf@webshell:~$ python3 level1.py
Please enter correct password for flag: 691d
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_56891419}
zeroone1233-picoctf@webshell:~$ 



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "691d"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

691d

## Notas adicionales

vim para editar el programa 
