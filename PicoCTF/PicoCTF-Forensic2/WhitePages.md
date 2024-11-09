## Descripcion 

Dejé de usar YellowPages y pasé a WhitePages... ¡pero la página que me dieron está toda en blanco!
## Solucion


`┌──(kali㉿kali)-[~/Documents/PicoCTF/whitepages]`
`└─$ sed 's/\xe2\x80\x83/0/g' whitepages.txt | sed 's/\x20/1/g'`

Agarramos el binario y lo ponemos en cyberchef
From binary

	`picoCTF`

		`SEE PUBLIC RECORDS & BACKGROUND REPORT`
		`5000 Forbes Ave, Pittsburgh, PA 15213`
		`picoCTF{not_all_spaces_are_created_equal_7100860b0fa779a5bd8ce29f24f586dc}``
`
## Notas adicionales
