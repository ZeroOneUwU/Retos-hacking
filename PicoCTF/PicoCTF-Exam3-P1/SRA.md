## Objetivo

I just recently learnt about the SRA public key cryptosystem... or wait, was it supposed to be RSA? Hmmm, I should probably check...

Additional details will be available after launching your challenge instance.

## Pistas
## Solución

Entramos a la conexion
Tenemos que crear un programa en python, que sera este :

```

from pwn import *
import primefac
from itertools import combinations
from Crypto.Util.number import long_to_bytes

#function to generate all the sub lists
def sub_lists (l):
   # initializing empty list
    comb = []

    #Iterating till length of list
    for i in range(1,len(l)+1):
  #      Generating sub list
        comb += [list(j) for j in combinations(l, i)]
  #  Returning list
    return comb

def divisors(phi):
   print("Give me the divisors of ", phi-1)
  # this is dangerous, but I'm trusting me
   return(eval(input()))

#connect to the server
r = remote('saturn.picoctf.net', 64866)  
#get ciphertext
r.recvuntil("anger =")
ciphertext=int(r.recvline())
#get d
r.recvuntil("envy =")
d=int(r.recvline())
print("cipher=",ciphertext)
print("d=",d)
print(r.recvuntil("vainglory?"))
r.recvline()
#since d is e^-1 mod (p-1)*(q-1), d*e=k*(p-1)*(q-1)+1
#so (p-1)*(q-1)*k = d*e-1
factors=divisors(d*65537)
combos = sub_lists(factors)
primes = set()
#try all possible subsets of the list of factors as the factors of (p-1)
for l in combos:
   product = 1
#   multiply them together to get p-1
   for k in l:
      product = product * k
 #  if the right length and adding 1 yields a prime, then maybe
   if product.bit_length()==128 and primefac.isprime(product+1):
      primes.add(product+1)
print(primes)
primelist = list(primes)
# try all possible prime pairs
for p in primelist:
   for q in primelist:
      n=p*q
   #   decode with this possible n
      plain = pow(ciphertext,d,n)
      try:
         plaintext = long_to_bytes(plain)
      #   see if it corresponds to text and if so, try it
         print(plaintext.decode())
         r.sendline(plaintext.decode())
         print(r.recvline())
         print(r.recvline())
         print(r.recvline())
      except:
         continue




```

```

                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/SRA]
└─$ python3 sra.py
[+] Opening connection to saturn.picoctf.net on port 64866: Done
/home/kali/Documents/PicoCTF/SRA/sra.py:26: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.recvuntil("anger =")
/home/kali/Documents/PicoCTF/SRA/sra.py:29: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.recvuntil("envy =")
cipher= 21311777371440413387334122058449370471664581415959525641133738300760799450343
d= 93801418314786512352572290732509755228867608187552896296952971967380302406473
/home/kali/Documents/PicoCTF/SRA/sra.py:33: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  print(r.recvuntil("vainglory?"))
b'vainglory?'
Give me the divisors of  6147463552096163660050530217736491828434296437787654164613406923826202878813021000


```

En esta parte vamos a la siguiente pagina para poner el numero
https://www.dcode.fr/prime-factors-decomposition
Tomamos los numeros nos da y lo copiamos a la terminal con "[]"

```
[2, 2, 2, 3, 3, 3, 5, 5, 5, 7, 7, 11, 13, 23, 43, 53, 28879, 4282141, 5131780937711, 127606906199661724291, 7654952794382454820774703]
{216135589529533120676185621514173467001, 281867381961115805890452561598751727431, 332001493178438840562702617850801480901, 201561681778207639052956408989127327001, 268008121984290178225407053586587190667, 242423731811426096788237571902377685111, 305655588301881878752377752657208768151, 276667910982032367135585514875667900751, 176066367501262906902085217094134567701, 317668069115389906459722922732045775101, 299072237169225961363865001061515040837, 198794756821483211209004538687814554571, 271883851972023601239877273692286400761, 219636921008661666927625372674351995401, 312391760719473617614149989366565728611, 178931402195607375883435768722540069241, 185245811092049623486289547064975011001, 201162273377485868038650515745643532389, 309466866826376968240902139895293827751, 234166748090773131047452897328193742789, 255508541328444573778385869349447724451, 209485263697855178501533756236814283401, 190180477979196286782710405244345904909, 179841122608536049468297847335378299901, 180594218816843105580810764655106300051, 190318696380416520867914091584600480533, 217986931192039789497819792592738036201, 182865844210765660367990774273409523951, 287826523228792672822597436051156626531, 243185000930532221109001339246989502903, 235981994200003930512937028315234004361, 264330480516238168918711931067388738651, 215279019003318798323933832436306507801, 215996615733329860985013611877760862827, 307679039465732698396936858301292214901, 225064428958015107338658097547047712701, 271686397113137552546729150349065578441, 243821125614354213823987699031212698601, 239742543890059570860744495213159520051, 336171056672045607791119605202145926501, 251158855503871931377922804509024259101, 220705052310284349443124006747031257001, 317347192277899613624915121799993203611, 218828329343124027713087290178755367251, 302084875111810285698810733604905083721, 203331138858644745322086100821068260501, 280515085367960858422095599841247873801, 295665085973198397787188001677012301501, 323231642415234795717650095869836913481, 298801343860594956506432356065721332811}
DJUokXxpY3HgakI9
/home/kali/Documents/PicoCTF/SRA/sra.py:61: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.sendline(plaintext.decode())
b'> DJUokXxpY3HgakI9\r\n'
b'Conquered!\r\n'
b'picoCTF{7h053_51n5_4r3_n0_m0r3_38268294}\r\n'
DJUokXxpY3HgakI9
[*] Closed connection to saturn.picoctf.net port 64866
                                                                                   
┌──(kali㉿kali)-[~/Documents/PicoCTF/SRA]
└─$ 



```
## Notas adicionales
## Referencias