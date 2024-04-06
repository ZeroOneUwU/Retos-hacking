## Objetivo
Do you know how to use the web inspector? Start searching here to find the flag
http://titan.picoctf.net:60527/

## Solución
Al visitar la página web, nos dice que nosotros podemos encontrar la bandera posiblemente inspeccionando el código, y eso hacemos, y obtenemos el siguiente resultado

```html
 <section class="about" notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMTBmOTM3NmZ9">
   <h1>
    Try inspecting the page!! You might find it there
   </h1>
   <!-- .about-container -->
  </section>
  <!-- .about -->
  <section class="why">
   <footer>
    <div class="bottombar">
     Copyright © 2023 Your_Name. All rights reserved.
```

Después de inspeccionar todas las páginas podemos observar que en ningún lado se encuentra una bandera con formato picoCTF, pero si podemos observar que hay un código bastante peculiar por ahí

```
cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMTBmOTM3NmZ9
```

Si utilizamos alguna herramienta de desencripción así como CyberChef, automáticamente detecta que se encuentra codificado en base64 y automáticamente nos arroja la bandera buscada

```
picoCTF{web_succ3ssfully_d3c0ded_10f9376f}
```

## Notas adicionales
## Referencias