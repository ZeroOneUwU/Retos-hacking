## Objetivo 

La contraseña para el siguiente nivel se almacena en el archivo data.txt, que contiene datos codificados en base64.
## Datos de acceso al nivel

user bandit10 
password - G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
## Solucion

```
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ file data.txt
data.txt: ASCII text
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
bandit10@bandit:~$ cat data.txt | grep base64
bandit10@bandit:~$ grep base64 data.txt 
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
bandit10@bandit:~$ base64 --help
Usage: base64 [OPTION]... [FILE]
Base64 encode or decode FILE, or standard input, to standard output.

With no FILE, or when FILE is -, read standard input.

Mandatory arguments to long options are mandatory for short options too.
  -d, --decode          decode data
  -i, --ignore-garbage  when decoding, ignore non-alphabet characters
  -w, --wrap=COLS       wrap encoded lines after COLS character (default 76).
                          Use 0 to disable line wrapping

      --help     display this help and exit
      --version  output version information and exit

The data are encoded as described for the base64 alphabet in RFC 4648.
When decoding, the input may contain newlines in addition to the bytes of
the formal base64 alphabet.  Use --ignore-garbage to attempt to recover
from any other non-alphabet bytes in the encoded stream.

GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
Full documentation <https://www.gnu.org/software/coreutils/base64>
or available locally via: info '(coreutils) base64 invocation'
bandit10@bandit:~$ echo "Nino bb" | base64
TmlubyBiYgo=
bandit10@bandit:~$ echo "TmlubyBiYgo=" | base64
VG1sdWJ5QmlZZ289Cg==
bandit10@bandit:~$ echo "TmlubyBiYgo=" | base64 --decode
Nino bb
bandit10@bandit:~$ base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
bandit10@bandit:~$ 
```

## Notas adicionales

**La codificación Base64 se utiliza principalmente para evitar los problemas de transmisión**, que ocurren cuando se transmiten datos binarios a sistemas basados en texto que no pueden manejar estos datos binarios correctamente. Como resultado, la información se pierde o se corrompe durante la transmisión.

**Base 64 es un sistema de numeración posicional que usa 64 como base**. Es la mayor potencia que puede ser representada usando únicamente los caracteres imprimibles de ASCII.

base64 -d -> Decodifica los datos
base64 -i  -> Decodifica los datos y descarta los caracteres no alfabeticos
base64 -w -> Decodifica los datos

## Referencias 

https://ubunlog.com/base64-codificacion-decodificacion-terminal/