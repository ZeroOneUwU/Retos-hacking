## Objetivo

In RSA d is a lot bigger than e, why don't we use d to encrypt instead of e? Connect with `nc jupiter.challenges.picoctf.org 57464`.

## Pistas
## Solución

```
┌──(kali㉿kali)-[~]
└─$ nc jupiter.challenges.picoctf.org 57464.
c: 31921951275339033980991020839242327956025082238529438520941396880880568591836827076071029597995982286194246094627059985106898285179630086432966088618664042617452958917996302723410959566374275420804903329637728969307946371679498515968714044922932065865033005214509295691602982753229886778951794492602520950545
n: 97280125107123416223663193710588263335500412044847319414255209277007925230808382658516562173071058211387056272413048578832227709935422069907500784279280969466981695464166761661418358552408943818147339078871084566742995722945193247359724955891031627518599727043839060756387404637193677576336604593370576193957
e: 22954054269444077520831402528961302839925208231403923698400026797986641984973691646418055715769272993589719367633480068099875937355102718907633735570666960685073204198981223620421698458217059537186282807972915986798276223693166673642268443008661653103868780407827941223560501094215303237250494415259731768033
                                                                                                           
┌──(kali㉿kali)-[~]
└─$ python3                                 
Python 3.11.7 (main, Dec  8 2023, 14:22:46) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> c=31921951275339033980991020839242327956025082238529438520941396880880568591836827076071029597995982286194246094627059985106898285179630086432966088618664042617452958917996302723410959566374275420804903329637728969307946371679498515968714044922932065865033005214509295691602982753229886778951794492602520950545
>>> n=97280125107123416223663193710588263335500412044847319414255209277007925230808382658516562173071058211387056272413048578832227709935422069907500784279280969466981695464166761661418358552408943818147339078871084566742995722945193247359724955891031627518599727043839060756387404637193677576336604593370576193957
>>> d=7633480068099875937355102718907633735570666960685073204198981223620421698458217059537186282807972915986798276223693166673642268443008661653103868780407827941223560501094215303237250494415259731768033
>>> d=22954054269444077520831402528961302839925208231403923698400026797986641984973691646418055715769272993589719367633480068099875937355102718907633735570666960685073204198981223620421698458217059537186282807972915986798276223693166673642268443008661653103868780407827941223560501094215303237250494415259731768033


>>> e=65537
>>> m=pow(c,d,n)
>>> m
55534182121034397606498489583989445150003208795361671490623255961212967660622034238415139982772523020697508457382037581154948374536358401818593222130930633277511052378044185100185216143208150074518780027118555171933481923020987927208634428988526438800011694524733185698793552175690413695929303879677342132030
>>> from Crypto.Util.number import long_to_bytes
>>> long_to_bytes(m)
b"O\x15S,\xf9\xf9\xe15YT\x1c\x1b\xf1\xa0\xc5{\xd7U\x02I\x1c\xce\x9at\xaa\x03\x07\x06{\xa5k\xf5\xb8-\xa5\xfc\x95\x81\xcc*\xc6\x00&\xd8\x84u\xc6\xf4\x1c\x96\xb9t}\xa6z\xd9\x9f \xe6\xa2u\xa8\x9f=\xbe4\xfe\xb5O\x0f\x84\xcd\x100Q\xff\xb7\x8e\x07\xa4\xbe\n\x87\x9c\xfe\xd1\xcbA\x14\x9a}1\xad\xa1\x93\x03\xb8\xfc0<\xe3\xc5\x1fl\xe2\xb0h\x8eu\xc7I\xe2'\xe7\x7f\xfc\x8a2W\x90\x1d\x8e\x04\xde\x81\xb4'>"
>>> m=pow(c,e,n)
>>> m
180638594769037903267909311328535969949661653320322151351464061
>>> long_to_bytes(m)
b'picoCTF{bad_1d3a5_2152720}'
>>> 

```
## Notas adicionales
## Referencias