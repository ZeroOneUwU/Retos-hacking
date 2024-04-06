## Objetivo

Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:57091/), and find the flag!

## Datos de acceso

```
N/A
```
## Solución

En dicha pagina web del reto, se puede observar un apartado con codigo en JavaScrypt, el cual al copearlo y ejecutarlo en la consola del navegador arroja la bandera

```
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓ¨ÍÕÄ¦í";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
    
```

```
Flag: picoCTF{p@g3_turn3r_18d2fa20}
```
## Notas adicionales
## Referencias
