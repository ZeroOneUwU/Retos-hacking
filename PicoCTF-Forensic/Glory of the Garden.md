## Descripcion 

Este jardín contiene más de lo que parece.
## Solucion

┌──(kali㉿kali)-[~/Documents/PicoCTF/Garden]
└─$ ls
garden.jpg                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/Garden]
└─$ hexeditor garden.jpg  

Buscamos una cadena "pico"

									"pi
00230570  63 6F 43 54  46 7B 6D 6F   
72 65 5F 74  68 61 6E 5F                                       coCTF{more_than_
00230580  6D 33 33 74  73 5F 74 68   
65 5F 33 79  33 33 64 64                                     m33ts_the_3y33dd
00230590  32 65 45 46  35 7D 22 0A                 2eEF5}".

picoCTF{more_than_m33ts_the_3y33dd2eEF5}

///////////////////////////////Otra opcion

`┌──(kali㉿kali)-[~/Documents/PicoCTF/Garden]`
`└─$ strings garden.jpg | grep "pico"`
`Here is a flag "picoCTF{more_than_m33ts_the_3y33dd2eEF5}"`
                                                        
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Garden]`
`└─$` 


## Notas adicionales
