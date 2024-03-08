## Descripcion 

Hay información interesante escondida en este sitio http://mercury.picoctf.net:39698/. ¿Puedes encontrarlo?
## Solucion

Vemos el codigo fuente
`</p>`
	`<!-- Here's the first part of the flag: picoCTF{t -->`
      `</div>``
`
le damos click a 
href="[mycss.css](view-source:http://mercury.picoctf.net:39698/mycss.css)">

`#tabintro { background-color: #ccc; }`
`#tababout { background-color: #ccc; }`

`/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */`

Ahora probamos lo siguiente

mercury.picoctf.net:39698/robots.txt

`User-agent: *`
`Disallow: /index.html`
 `Part 3: t_0f_pl4c`
`I think this is an apache server... can you Access the next flag?`

Ahora intentamos esto (un servidor apache):

mercury.picoctf.net:39698/.htaccess

 Part 4: 3s_2_lO0k
I love making websites on my Mac, I can Store a lot of information there.

Vemos lo de .DS_store que es lo de las mac que guarda informacion

mercury.picoctf.net:39698/.DS_Store

Congrats! You completed the scavenger hunt. Part 5: _fa04427c}

picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_fa04427c}
## Notas adicionales
