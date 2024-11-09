## Objetivo

This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://jupiter.challenges.picoctf.org/static/87e103a8db01087de9ccf5a7a022ddf8/VaultDoor1.java)

## Pistas
## Solución

```
┌──(kali㉿kali)-[~/Documents/PicoCTF/vault-door-1]
└─$ cat VaultDoor1.java                                        
Copiamos a un nuevo archivo llamado flag


┌──(kali㉿kali)-[~/Documents/PicoCTF/vault-door-1]
└─$ nano flag       

						   
┌──(kali㉿kali)-[~/Documents/PicoCTF/vault-door-1]
└─$ cat flag | sort | awk '{print $3}' | tr -d "'"

┌──(kali㉿kali)-[~/Documents/PicoCTF/vault-door-1]
└─$ cat flag | sort | awk '{print $3}' | tr -d "'" | tr -d "\n"
d35cr4mbl3_tH3_cH4r4cT3r5_f6daf4;==                                                                                       
┌──(kali㉿kali)-[~/Documents/PicoCTF/vault-door-1]
└─$ 

```

## Notas adicionales
## Referencias