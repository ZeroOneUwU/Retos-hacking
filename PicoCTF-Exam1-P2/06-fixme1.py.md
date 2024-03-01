## Descripcion 

Corrija el error de sintaxis en este script de Python para imprimir la bandera.
## Solucion

zeroone1233-picoctf@webshell:~$ ls
README.txt  file  fixme1.py
zeroone1233-picoctf@webshell:~$ python3 fixme1.py
  File "/home/zeroone1233-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
zeroone1233-picoctf@webshell:~$ vim fixme1.py
zeroone1233-picoctf@webshell:~$ python3 fixme1.py
  File "/home/zeroone1233-picoctf/fixme1.py", line 20
    print('That is correct! Here is your flag: ' + flag)
IndentationError: unexpected indent
zeroone1233-picoctf@webshell:~$ vim fixme1.py
zeroone1233-picoctf@webshell:~$ python3 fixme1.py
  File "/home/zeroone1233-picoctf/fixme1.py", line 20
    print("That is correct! Here is your flag: " + flag)
IndentationError: unexpected indent
zeroone1233-picoctf@webshell:~$ vim
zeroone1233-picoctf@webshell:~$ vim fixme1.py
zeroone1233-picoctf@webshell:~$ python3 fixme1.py
That is correct! Here is your flag: picoCTF{1nd3nt1ty_cr1515_182342f7}
zeroone1233-picoctf@webshell:~$ 
## Notas adicionales

Checar muy bien la sangria