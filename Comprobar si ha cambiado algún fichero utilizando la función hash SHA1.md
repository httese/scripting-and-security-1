# Comprobar si ha cambiado algún fichero utilizando la función hash SHA1
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2016/01/27/comprobar-si-ha-cambiado-algun-fichero-utilizando-la-funcion-hash-sha1/
```PowerShell
#Ejecutar la función hash SHA1 en dos momentos distintos y comparar el contenido para descubrir si se producido algún cambio en alguno de los ficheros
ls D:\power\files | % {Get-FileHash $_.FullName -Algorithm SHA1 | Out-File d:\hash.txt -Append}
ls D:\power\files | % {Get-FileHash $_.FullName -Algorithm SHA1 | Out-File d:\hash1.txt -Append}
Compare-Object -ReferenceObject $(Get-Content D:\hash.txt) -DifferenceObject $(Get-Content D:\hash1.txt)

```
