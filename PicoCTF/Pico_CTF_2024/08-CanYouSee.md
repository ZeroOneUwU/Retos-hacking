## Objetivo
How about some hide and seek? Download this file here.
https://artifacts.picoctf.net/c_titan/5/unknown.zip

## Pistas
- How can you view the information about the picture?
- If something isn't in the expected form, maybe it deserves attention?

## Solución
La solución consta de analizar los metadatos de la foto que nos proporcionan

```powershell
C:\Users\mgarcia\Desktop>exiftool ukn_reality.jpg
ExifTool Version Number         : 12.78
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:02:15 16:40:17-06:00
File Access Date/Time           : 2024:03:14 14:18:24-06:00
File Creation Date/Time         : 2024:03:14 14:18:11-06:00
File Permissions                : -rw-rw-rw-
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fNGRhYmRkY2J9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4
```

Esto nos permite observar que el URL está codificado a base64, si nosotros tomamos el url y lo pasamos por un convertidor de base64 nos va a mostrar la bandera

## Notas adicionales
## Referencias