# Leer agenda (versión avanzada 2)
## PowerShell 
### URL: https://www.jesusninoc.com/2015/05/28/leer-agenda-version-avanzada-2/
```PowerShell
#De los datos guardados por "Agenda (versión avanzada 2)"
#https://www.jesusninoc.com/2015/05/27/agenda-version-avanzada-2/

#Mostrar los datos de cada usuario por su DNI utilizando el cmdlet Get-ChildItem, también mostrar la imagen de la calle en donde vive el usuario

#Pedir el DNI al usuario
$dni=Read-Host 'Introduzca DNI: '

#Buscar el fichero cuyo nombre el el DNI junto con la extensión .txt
$fichero=Get-ChildItem $dni'.txt'

#Obtener el contenido del fichero
$contenido=Get-Content $fichero.Name

#Abrir la imagen de la persona
Start-Process C:\WINDOWS\system32\mspaint.exe F:\power\agenda\$dni'_fotopersona.bmp'

#Abrir la imagen de la calle en donde vive el usuario
Start-Process C:\WINDOWS\system32\mspaint.exe F:\power\agenda\$dni'_calle.bmp'

#Imprimir el contenido por pantalla
$contenido

```
