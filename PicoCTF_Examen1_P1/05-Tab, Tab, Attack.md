## Descripcion 

El uso de tab complete en la Terminal agregará años a su vida, especialmente. cuando se trata de estructuras de directorios y nombres de archivos largos y confusos: Addadshashanammu.zip
## Solucion

`zeroone1233-picoctf@webshell:~$ ls`
`Addadshashanammu.zip`
`zeroone1233-picoctf@webshell:~$ unzip Addadshashanammu.zip`
`Archive:  Addadshashanammu.zip`
   `creating: Addadshashanammu/`
   `creating: Addadshashanammu/Almurbalarammi/`
   `creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/`
   `creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/`
   `creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/`
   `creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/`
   `creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/`
  `inflating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet`  
`zeroone1233-picoctf@webshell:~$ ls`
`Addadshashanammu  Addadshashanammu.zip`
`zeroone1233-picoctf@webshell:~$ cd Addadshashanammu`
`zeroone1233-picoctf@webshell:~/Addadshashanammu$ ls`
`Almurbalarammi`
`zeroone1233-picoctf@webshell:~/Addadshashanammu$ cd Almurbalarammi`
`TAB`

`zeroone1233-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/`
`Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ls`
`fang-of-haynekhtnamet`
`zeroone1233-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/`
`Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ./ fang-of-haynekhtnamet`
`-bash: ./: Is a directory`
`zeroone1233-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/`
`Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ./fang-of-haynekhtnamet`
`*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_2bcfb2ab}`
`zeroone1233-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/`
`Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$`` 
`
## Notas adicionales
