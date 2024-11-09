## Objetivo

How about some hide and seek heh? Look at this image [here](https://artifacts.picoctf.net/c/236/atbash.jpg).
## Pistas
## Solución

```

─(kali㉿kali)-[~/Documents/PicoCTF/HideToSee]
└─$ steghide --extract /sf atbash.jpg
steghide: unknown argument "/sf".
steghide: type "steghide --help" for help.
                                                                                                           
┌──(kali㉿kali)-[~/Documents/PicoCTF/HideToSee]
└─$ steghide --extract -sf atbash.jpg
Enter passphrase: 
wrote extracted data to "encrypted.txt".
                                                                                                           
┌──(kali㉿kali)-[~/Documents/PicoCTF/HideToSee]
└─$ cat encrypted.txt          
krxlXGU{zgyzhs_xizxp_zx751vx6}

picoCTF{atbash_crack_ac751ec6}
```

## Notas adicionales
## Referencias