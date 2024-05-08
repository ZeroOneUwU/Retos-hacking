## Objetivo

This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program. You can download the file from [here](https://artifacts.picoctf.net/c/506/asciiftw).
## Pistas
## Solución

Descargamos el archivo
Nos vamos a ghidra
Hacemos un nuevo proyecto
Importamos el archivo descargado
Le damos que si lo analice
Abrimos la ventana de listing
Buscamos ____start y click
Bajamos donde diga main (rdi,main)
Vemos un CALL
Damos en crear nuevo script que sea en python

Ponemos este script:
```

```python
from ghidra.program.model.mem import MemoryAccessException

start_addr = currentProgram.getAddressFactory().getAddress("00101184")
end_addr = currentProgram.getAddressFactory().getAddress("001011fc")

byte_list = []


current_addr = start_addr
while current_addr <= end_addr:
	instruction = getInstructionAt(current_addr)
	if instruction is not None:
		
		operand = instruction.getOpObjects(1)[0] # get second operand
		byte_val = operand.getValue() & 0xFF # convert to unsigned byte
		byte_list.append(byte_val)
                
       
        current_addr = current_addr.next()

flag = list(map(chr, byte_list))
print("Flag:", "".join(flag))
```


Lo corremos y nos suelta la bandera
picoCTF{ASCII_IS_EASY_3CF4BFAD}
## Notas adicionales
## Referencias