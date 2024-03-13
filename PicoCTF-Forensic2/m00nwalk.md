## Descripcion 

Decode this [message](https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav) from the moon.
## Solucion

Esta codificado en sstv
https://github.com/colaclanth/sstv
Instalamos el repo

`┌──(kali㉿kali)-[~/Documents/PicoCTF/moonwalk]`
`└─$ sstv -d message.wav -o img.jpg` 
`[sstv] Searching for calibration header... Found!`    
`[sstv] Detected SSTV mode Scottie 1`
`[sstv] Decoding image...   [#########################################################################] 100%`
`[sstv] Drawing image data...`
`[sstv] ...Done!``
`

picoCTF{beep_boop_im_in_space}

## Notas adicionales
