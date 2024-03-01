## Descripcion 

¿Sabes cómo moverte entre directorios y leer archivos en el shell? Inicie el contenedor, "ssh" y luego "ls" una vez conectado para comenzar. Inicie sesión a través de `ssh` como `ctf-player` con la contraseña, `a13b7f9d`

Detalles adicionales estarán disponibles después de lanzar su instancia de desafío.
## Solucion

zeroone1233-picoctf@webshell:~$ ssh ctf-player@venus.picoctf.net -p 53917

ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat ^C
ctf-player@pico-chall$ cat instructions-to-2of3.txt
Next, go to the root of all things, more succinctly `/`
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_

ctf-player@pico-chall$ 
ctf-player@pico-chall$ cd /                        
ctf-player@pico-chall$ ls
2of3.flag.txt  dev   instructions-to-3of3.txt  media  proc  sbin  tmp
bin            etc   lib                       mnt    root  srv   usr
boot           home  lib64                     opt    run   sys   var
ctf-player@pico-chall$ cat 2of3.flag.txt
0ut_0f_\/\/4t3r_

ctf-player@pico-chall$ 
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`
ctf-player@pico-chall$ cd ~ 
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt
71be5264}
ctf-player@pico-chall$

picoCTF{xxsh_0ut_0f_\/\/4t3r_71be5264} 

## Notas adicionales
