# Cifrar utilizando una clave secreta
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/08/18/cifrar-utilizando-una-clave-secreta/
```PowerShell
$cadena='abcdefghijk'
$clave='clavesecreta123'

#La clave para cifrar tiene que ser correcta en tipo System.Byte
#ConvertFrom-SecureString : No se puede enlazar el parámetro 'Key'. No se puede convertir el valor "Some secret key" al tipo "System.Byte". Error: "La cadena de entrada no tiene el formato correcto."

$clavebyte=[Byte[]]($clave.PadRight(24).Substring(0,24).ToCharArray())

$cadenacifrada=$cadena | ConvertTo-SecureString -AsPlainText -Force | ConvertFrom-SecureString -Key $clavebyte
$cadenacifrada

```
