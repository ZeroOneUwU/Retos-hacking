## Objetivo
People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate. You can download the challenge files here:

    challenge.zip


## Pistas
- Checksums let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file.
- You can create a SHA checksum of a file with sha256sum <file> or all files in a directory with sha256sum <directory>/*.
- Remember you can pipe the output of one command to another with |. Try practicing with the 'First Grep' challenge if you're stuck!

## Solución
El script no me permitía desencriptar el archivo pero, al abrir con algún editor de código podemos ver el comando que nos permite desencriptar el archivo, entonces ahora la pregunta es ¿Cómo podemos saber cuál archivo es el bueno?. Gracias a que el autor de la bandera nos proporcionó un checksum del archivo legítimo, nosotros podemos usar el comando sha256sum y el comando grep para ver cuál de todos los archivos coincide con el checksum proporcionado, esta herramienta es útil en muchos casos si queremos encontrar por ahí si alguien nos quiere jugar una mala broma.

```bash
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % ls
checksum.txt  decrypt.sh  files
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % cat checksum.txt
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % cd files
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in/files
 % sha256sum * | grep 5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda
5848768e56185707f76c1d74f34f4e03fb0573ecc1ca7b11238007226654bcda  8eee7195
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in/files
 % cp 8eee7195 ../
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in/files
 % cd ..
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % ls
8eee7195  checksum.txt  decrypt.sh  files
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % bash decrypt.sh 8eee7195
Error: '8eee7195' is not a valid file. Look inside the 'files' folder with 'ls -R'!
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % ls -l 8eee7195
-rwxrwxrwx 1 mgarcia mgarcia 64 Mar 14 14:33 8eee7195
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % ls
8eee7195  checksum.txt  decrypt.sh  files
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 % openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in 8eee7195 -k picoCTF
picoCTF{trust_but_verify_8eee7195}
mgarcia@nightmare ~/Desktop/home/ctf-player/drop-in
 %
```

## Notas adicionales
## Referencias