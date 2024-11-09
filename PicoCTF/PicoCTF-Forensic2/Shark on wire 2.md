## Descripcion 

Encontramos esto [captura de paquetes] (https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recupera la bandera que fue sustraída de la red.
## Solucion

┌──(kali㉿kali)-[~/Documents/PicoCTF/shark2]
└─$ wireshark capture.pcap &                                                                        
[1] 44738

udp.dstport== 22
file /> export packet dise
txt

restamos 5000 a todos los paquetes que salen
Nos da cada letra para armar la bandera

┌──(kali㉿kali)-[~/Documents/PicoCTF/shark2]
└─$ cat data.txt | grep UDP | awk '{print $7}' | cut -c2- | grep -v 000

112
105
099
111
067
084
070
123
112
049
076
076
102
051
114
051
100
095
100
097
116
097
095
118
049
097
095
115
116
051
103
048
125

Lo ponemos en cyberchef
From decimal
line feed

picoCTF{p1LLf3r3d_data_v1a_st3g0}



## Notas adicionales
