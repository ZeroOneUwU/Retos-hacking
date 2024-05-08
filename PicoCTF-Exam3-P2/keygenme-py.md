## Objetivo

[keygenme-trial.py](https://mercury.picoctf.net/static/9055e7d35f5f4646338a1734aea0dda5/keygenme-trial.py)
## Pistas
## Solución

```

┌──(kali㉿kali)-[~/Documents/PicoCTF/keygenme-py]
└─$ ls              
keygenme-trial.py  SOLVE.py
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/keygenme-py]
└─$ python3 SOLVE.py
picoCTF{1n_7h3_|<3y_of_ac73dc29}
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/keygenme-py]
└─$ cat SOLVE.py    
import hashlib

username_trial = b"FRASER"


key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
key_part_dynamic1_trial = ""
key_part_static2_trial = "}"

hash = hashlib.sha256(username_trial).hexdigest()

key_part_dynamic1_trial += hash[4]
key_part_dynamic1_trial += hash[5]
key_part_dynamic1_trial += hash[3]
key_part_dynamic1_trial += hash[6]
key_part_dynamic1_trial += hash[2]
key_part_dynamic1_trial += hash[7]
key_part_dynamic1_trial += hash[1]
key_part_dynamic1_trial += hash[8]


key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial

print(key_full_template_trial)
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/keygenme-py]
└─$ 


```

Ponemos el usuario que esta en el archivo que descargamos
## Notas adicionales
## Referencias