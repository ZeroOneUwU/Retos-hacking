## Objetivo
## Pistas
## Solución

```
Existen múltiples formas en las que el malware puede ganar persistencia. Las técnicas utilizadas varían según el sistema operativo de destino, la facilidad de implementación, el nivel de sigilo o, a veces, según la preferencia del autor del malware. Algunos ejemplos de estas técnicas serían modificar el sector de arranque de un sistema operativo, instalar configuraciones maliciosas o secuestrar el flujo de ejecución.

En Windows, la técnica más común y más fácil de implementar es el abuso de las claves de ejecución del Registro de Windows.

El Registro de Windows es una base de datos de sistemas operativos de bajo nivel y configuraciones de aplicaciones. Las claves de ejecución son claves específicas dentro del Registro que contienen una ruta que se ejecuta cada vez que un usuario inicia sesión y se enumeran a continuación:

· HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run: ruta de ejecución cuando el usuario actual inicia sesión

· HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run: ruta de ejecución cuando cualquier usuario inicia sesión

· HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce: ruta de ejecución cuando el usuario actual inicia sesión y luego la elimina

· HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce: ruta de ejecución cuando cualquier usuario inicia sesión y luego la elimina

Para ver estas claves, abra el Editor del Registro buscando "Regedit" en la Búsqueda de Windows o haciendo doble clic en el icono de Regedit anclado en la barra de tareas de Windows.

ver el valor de una de las claves de Ejecutar, expanda las carpetas y sus subcarpetas hasta llegar a la clave que está buscando. Por ejemplo:

· HKEY_LOCAL_MACHINE > Software > Microsoft > Windows > CurrentVersion > Run

(Default)
C:\Users\Administrator\AppData\Local\bd84\24d9.bat
pleaseletmepersist

AutoRuns PowerShell Module logo
La máquina Windows ya tiene instalado el módulo AutoRuns de PowerShell. Para usarlo, abra PowerShell en modo Administrador haciendo clic en el ícono de PowerShell en la barra de tareas de Windows en la parte inferior de la pantalla. Una vez que aparezca la ventana de PowerShell, escriba lo siguiente para ver los comandos disponibles:

Get-Command -Modulo Autoruns

Get-PSAutorun
New-AutoRunsBaseLine
Compare-AutoRunsBaseLine


AutoRuns PowerShell tiene una función llamada Get-PSAutorun que enumerará todos los posibles mecanismos de inicio automático disponibles en la máquina. Esta lista se crea analizando categorías como el Registro, los servicios de Windows, las entradas de WMI, el secuestro de DLL y más. Debido a esto, la salida del comando devolverá muchos resultados que pueden resultar complicados si no se filtran adecuadamente.
Enviar el resultado del comando anterior al cmdlet Out-GridView puede hacer que la salida sea más legible.

Get-Help Get-PSAutorun -detailed
BootExecute
1
PrintMonitorDLLs
5
VerifyDigitalSignature
3

Ejecutar Get-Help Get-PSAutorun -detailed en Powershell
Ejecutar Get-PSAutorun -BootExecute en Powershell (para filtrar los artefactos relacionados con la ejecución de arranque de imágenes)
Ejecutar Get-PSAutorun -PrintMonitorDLLs en Powershell (para filtrar los artefactos relacionados con el controlador de impresora y los monitores de estado)
Ejecutar Get-PSAutorun -VerifyDigitalSignature en Powershell (para mostrar si un archivo está firmado digitalmente)


Después de crear la máquina de esta sala, se generó un archivo de línea base y se guardó en la carpeta ~/Documents. Este archivo sirve como una instantánea del Registro antes de que se ejecutara el malware.

C:\Users\Administrator> Get-PSAutorun -VerifyDigitalSignature
C:\Users\Administrator> Compare-AutorunsBaseLine -Verbose


HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
C:\Windows\systerm32\userinit.exe;C:\Users\Administrator\AppData\Local\THM\789a.bat

Ir a la ruta “C:\Users\Administrator\AppData\Local\THM\” y clic en la opción editar para verificar el contenido.





```
## Notas adicionales
## Referencias