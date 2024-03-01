## Descripcion 

¿Puedes invocar indicadores de ayuda para una herramienta o binario? Este programa tiene información extraordinariamente útil.
## Solucion
`
``zeroone1233-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/f95b1ee9f29d631d99073e34703a2826/warm`
`--2024-02-26 18:28:28--  https://mercury.picoctf.net/static/f95b1ee9f29d631d99073e34703a2826/warm`
`Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142`
`Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.`
`HTTP request sent, awaiting response... 200 OK`
`Length: 10936 (11K) [application/octet-stream]`
`Saving to: 'warm'`

`warm                         100%[=============================================>]  10.68K  --.-KB/s    in 0s`      

`2024-02-26 18:28:28 (210 MB/s) - 'warm' saved [10936/10936]`

`zeroone1233-picoctf@webshell:~$ ls`
`README.txt  flag  warm`
`zeroone1233-picoctf@webshell:~$ ./warm`
`-bash: ./warm: Permission denied`
`zeroone1233-picoctf@webshell:~$ chmod +x warm`
`zeroone1233-picoctf@webshell:~$ ./warm`
`Hello user! Pass me a -h to learn what I can do!`
`zeroone1233-picoctf@webshell:~$ ./warm -h`
`Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_f0668f62}`
`zeroone1233-picoctf@webshell:~$` 

## Notas adicionales
