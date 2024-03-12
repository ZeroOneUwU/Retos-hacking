## Descripcion 

¿Este es un archivo de texto TXT realmente extraño? ¿Puedes encontrar la bandera?
## Solucion
`
``┌──(kali㉿kali)-[~/Documents/PicoCTF/Ext]`
`└─$ ls`
`flag.txt`
       
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Ext]`
`└─$ xxd flag.txt | head` 
                                                        
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Ext]`
`└─$ mv flag.txt flag.png`
  
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Ext]`
`└─$ open flag.png`           

`┌──(kali㉿kali)-[~/Documents/PicoCTF/Ext]`
`└─$` 

picoCTF{now_you_know_about_extensions}

## Notas adicionales
