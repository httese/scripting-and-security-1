# Crear nuevos objetos
## PowerShell 
### URL: https://www.jesusninoc.com/2015/09/04/crear-nuevos-objetos/
```PowerShell
$Nombre='Marta'
$Edad=30

$Persona=New-Object PSObject -Property ([Ordered]@{NombrePersona=$Nombre; EdadPersona=$Edad })

$Persona.NombrePersona
$Persona.EdadPersona

```
