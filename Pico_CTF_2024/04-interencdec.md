## Objetivo
Can you get the real meaning from this file. Download the file here.
https://artifacts.picoctf.net/c_titan/2/enc_flag

## Solución
El reto consiste en decifrar el mensaje oculto dentro de un archivo que nos piden descargar, el contenido del archivo es el siguiente:

```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==
```

Podemos ver que termina con dos signos de == lo que significa que está codificado con el algoritmo base 64, si lo decodificamos obtenemos

```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='
```

Del que si solo tomamos la parte encerrada en comillas, y lo volvemos a decodificar con el algoritmo base64, obtenemos
```
wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}
```

Como podemos observar ya casi tenemos la bandera, porque ya casi sigue el formato respectivo de las banderas de los retos, entonces, si conocemos la palabra inicial del formato de las banderas, picoCTF, entonces:

```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
    j     m     p       f   v w       a                   1. Sabemos que dentro del abecedario así se localiza picoCTF
    j k l m n o p       f   v w x y z a                   2. Haciendo suposición de completado del abecedario
h i j k l m n o p       f   v w x y z a b c d e f g       3. Haciendo suposición de completado del abecedario
h i j k l m n o p q r s f u v w x y z a b c d e f g       3. Haciendo suposición de completado del abecedario


picoCTF{caesar_d3cr9pt3d_78250afc}

```

Con esto basta para poder decifrar la bandera

## Notas adicionales
## Referencias