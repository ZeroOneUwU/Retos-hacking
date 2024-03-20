## Descripcion 

Encontramos esta captura y clave de paquete. Recuperar la bandera.
## Solucion

┌──(kali㉿kali)-[~/Documents/PicoCTF/Web0]
└─$ wireshark capture.pcap &                                                                        
edit 
preferencs
tls
key browse

packet details string picoCTF
"Pico-Flag: picoCTF{nongshim.shrimp.crackers}\x0d\x0a"


┌──(kali㉿kali)-[~/Documents/PicoCTF/Web0]
└─$ ssldump -r capture.pcap -k picokey.key -d | grep pico -A3 

## Notas adicionales
