## Descripcion 

¿Puedes encontrar la bandera en el archivo sin ejecutarla?
solucion
## Solucion

zeroone1233-picoctf@webshell:~$ ls
README.txt  file  fixme1.py  strings
zeroone1233-picoctf@webshell:~$ strings strings | grep "pico"
picoCTF{5tRIng5_1T_7f766a23}
zeroone1233-picoctf@webshell:~$ 


## Notas adicionales

El 'strings'comando en Linux se utiliza 
para extraer cadenas legibles de un archivo binario. Puedes usarlo con la sintaxis: strings [option] myfile.bin.