## Objetivo

Using a Secure Shell (SSH) is going to be pretty important.Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `60572` to get the flag?You'll also need the password `1ad5be0d`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#_the_shell](https://primer.picoctf.com/#_the_shell)

## Datos de acceso

```
ssh -l ctf-player titan.picoctf.net -p 60572
```
## Solución

Solo fue necesario conectarse por SSH con el usuario, la dirección y el puerto especificados para lograr conseguir la bandera

```
czarragar-picoctf@webshell:~$ ssh -l ctf-player titan.picoctf.net -p 60572
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_8306c99d}
Connection to titan.picoctf.net closed.
czarragar-picoctf@webshell:~$ timed out waiting for input: auto-logout
```
## Notas adicionales
## Referencias
