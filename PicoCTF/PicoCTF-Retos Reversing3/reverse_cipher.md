## Objetivo

We have recovered a [binary](https://jupiter.challenges.picoctf.org/static/48babf8f8c4c6b8baf336680ea5b9ddf/rev) and a [text file](https://jupiter.challenges.picoctf.org/static/48babf8f8c4c6b8baf336680ea5b9ddf/rev_this). Can you reverse the flag.
## Pistas
## Solución

```

──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ ls
rev  rev_this
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ chmod +x rev  
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ ./rev                                           
No flag found, please make sure this is run on the server
zsh: segmentation fault  ./rev
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ cat rev_this 
picoCTF{w1{1wq8/7376j.:}                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ touch flag.txt  
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ ./rev         
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ ls
flag.txt  rev  rev_this
                                                                                                                    
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$    



Creamos proyecto en el ghidra
Damos importar archivo
Buscamos el rev
Luego en rev damos doble click
Si
si
Entramos al fuctions
y abrimos el main


 oid main(void)

{
  size_t sVar1;
  char flag [23];
  char local_41;
  int local_2c;
  FILE *frev;
  FILE *fflag;
  uint j;
  int i;
  char flagrev;
  
  fflag = fopen("flag.txt","r");
  frev = fopen("rev_this","a");
  if (fflag == (FILE *)0x0) {
    puts("No flag found, please make sure this is run on the server");
  }
  if (frev == (FILE *)0x0) {
    puts("please run this on the server");
  }
  sVar1 = fread(flag,0x18,1,fflag);
  local_2c = (int)sVar1;
  if ((int)sVar1 < 1) {
                    /* WARNING: Subroutine does not return */
    exit(0);
  }
  for (i = 0; i < 8; i = i + 1) {
    flagrev = flag[i];
    fputc((int)flagrev,frev);
  }
  for (j = 8; (int)j < 0x17; j = j + 1) {
    if ((j & 1) == 0) {
      flagrev = flag[(int)j] + '\x05';
    }
    else {
      flagrev = flag[(int)j] + -2;
    }
    fputc((int)flagrev,frev);
  }
  flagrev = local_41;
  fputc((int)local_41,frev);
  fclose(frev);
  fclose(fflag);
  return;
cambiamos los nombres


┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ nano exploit.py  
                                        ┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ cat exploit.py   
d = open("rev_this").read()
flag = ""

for j in range(8,23):
       if j & 1 == 0:
              flag += chr( ord(d[j])-5 )
       else :
              flag += chr( ord(d[j])+2 ) 
print(flag)
                                                            
┌──(kali㉿kali)-[~/Documents/PicoCTF/reverse_cipher]
└─$ python3 exploit.py 
r3v3rs312528e05

picoCTF{r3v3rs312528e05}

```
## Notas adicionales
## Referencias