# Mover y dividir el contenido de un directorio en varios directorios
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2014/07/13/mover-y-dividir-el-contenido-de-un-directorio-en-varios-directorios/
```PowerShell
$listado=ls F:\usbcanciones
($listado) | %{
$numero=[array]::IndexOf($listado,$_)
Switch($numero)
{
{$_ -le 200}{
$origen='F:\usbcanciones\'+($listado[$numero]).Name
$destino='G:\0\'+($listado[$numero]).Name
Copy-Item $origen $destino
break}
{$_ -gt 200 -and $_ -le 400}{
$origen='F:\usbcanciones\'+($listado[$numero]).Name
$destino='G:\200\'+($listado[$numero]).Name
Copy-Item $origen $destino
break}
{$_ -gt 400 -and $_ -le 600}{
$origen='F:\usbcanciones\'+($listado[$numero]).Name
$destino='G:\400\'+($listado[$numero]).Name
Copy-Item $origen $destino
break}
{$_ -gt 600 -and $_ -le 800}{$_
$origen='F:\usbcanciones\'+($listado[$numero]).Name
$destino='G:\600\'+($listado[$numero]).Name
Copy-Item $origen $destino
break}
{$_ -gt 800 -and $_ -le 1000}{
$origen='F:\usbcanciones\'+($listado[$numero]).Name
$destino='G:\800\'+($listado[$numero]).Name
Copy-Item $origen $destino
break}
{$_ -gt 1000 -and $_ -le 1200}{
$origen='F:\usbcanciones\'+($listado[$numero]).Name
$destino='G:\1000\'+($listado[$numero]).Name
Copy-Item $origen $destino
break}
}
$_
}

```
