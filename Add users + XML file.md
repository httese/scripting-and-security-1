# Add users + XML file
## PowerShell 
### URL: https://www.jesusninoc.com/2012/12/30/add-users-xml/
```PowerShell
<?xml version="1.0"?>
<alumnos>
<alumno id="1">
<usuario>juanito</usuario>
<nombrecompleto>Juan Romero</nombrecompleto>
</alumno>
<alumno id="2">
<usuario>pepito</usuario>
<nombrecompleto>José Carromato</nombrecompleto>
</alumno>
</alumnos>

```
```PowerShell
[xml]$al=Get-Content ./alumnos.xml
$al.alumnos.alumno | % {
$psw=-join ([Char[]]'abcdefgABCDEFG0123456&%$' | Get-Random -count 14)
net user $_.usuario $psw /add
}

```
