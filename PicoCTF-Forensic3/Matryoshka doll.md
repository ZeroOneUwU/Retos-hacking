## Descripcion 
Las muñecas matrioskas son un conjunto de muñecas de madera de tamaño decreciente colocadas una dentro de otra. ¿Cuál es el último? Imagen: esto

## Solucion

`┌──(kali㉿kali)-[~/Documents/PicoCTF/Matryoshka]`
`└─$ binwalk dolls.jpg`

`┌──(kali㉿kali)-[~/Documents/PicoCTF/Matryoshka]`
`└─$ unzip dolls.jpg`
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Matryoshka]`
`└─$ ls`
`base_images  dolls.jpg`
                                                               
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Matryoshka]`
`└─$ cd base_images`
                                                        
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Matryoshka/base_images]`
`└─$ ls`
`2_c.jpg`
                                                        
`┌──(kali㉿kali)-[~/Documents/PicoCTF/Matryoshka/base_images]`
`└─$` 

`┌──(kali㉿kali)-[~/…/PicoCTF/Matryoshka/base_images/base_images]`
`└─$ unzip 3_c.jpg` 
`Archive:  3_c.jpg`
`warning [3_c.jpg]:  123606 extra bytes at beginning or within zipfile`
  `(attempting to process anyway)`
  `inflating: base_images/4_c.jpg`     
                                                    
`┌──(kali㉿kali)-[~/…/PicoCTF/Matryoshka/base_images/base_images]`
`└─$ cd base_images`
                                                   
`┌──(kali㉿kali)-[~/…/Matryoshka/base_images/base_images/base_images]`
`└─$ ls`
`4_c.jpg`
                                           
`┌──(kali㉿kali)-[~/…/Matryoshka/base_images/base_images/base_images]`
`└─$ unzip 4_c.jpg` 
`Archive:  4_c.jpg`
`warning [4_c.jpg]:  79578 extra bytes at beginning or within zipfile`
  `(attempting to process anyway)`
  `inflating: flag.txt`                
                                                    
`┌──(kali㉿kali)-[~/…/Matryoshka/base_images/base_images/base_images]`
`└─$ ls`
`4_c.jpg  flag.txt`
           
`┌──(kali㉿kali)-[~/…/Matryoshka/base_images/base_images/base_images]`
`└─$ cat flag.txt`                                                       
`picoCTF{4f11048e83ffc7d342a15bd2309b47de}`                                                                                                           
`┌──(kali㉿kali)-[~/…/Matryoshka/base_images/base_images/base_images]`
`└─$` 

binwalk --extract dolls.jpg
## Notas adicionales
