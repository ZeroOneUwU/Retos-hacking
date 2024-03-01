## Descripcion 

Este sitio web sólo puede ser renderizado por picobrowser, ¡ve y atrapa la bandera! https://jupiter.challenges.picoctf.org/problem/28921/ (link) o http://jupiter.challenges.picoctf.org:28921
## Solucion

inspeccionar
red
buscamos user-agent 
en la terminal
curl https://jupiter.challenges.picoctf.org/problem/28921/flag -H "User-Agent:picobrowser" | grep pico

┌──(kali㉿kali)-[~]
└─$ curl https://jupiter.challenges.picoctf.org/problem/28921/flag -H "User-Agent:picobrowser" | grep pico
  `% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current`
                                 `Dload  Upload   Total   Spent    Left  Speed`
`100  2115  100  2115    0     0   3404      0 --:--:-- --:--:-- --:--:--  3411`
         `<!-- <strong>Title</strong> --> picobrowser!`
            `<p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{p1c0_s3cr3t_ag3nt_84f9c865}</code></p>`
`┌──(kali㉿kali)-[~]`
`└─$` 


## Notas adicionales
