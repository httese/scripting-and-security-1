# Autenticarse en el punto de acceso mediante el usuario y la contraseña
## Automation, Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/12/10/autenticarse-en-el-punto-de-acceso-mediante-el-usuario-y-la-contrasena/
```PowerShell
$user="admin"
$pass="1234"
$pair="${user}:${pass}"
$bytes=[System.Text.Encoding]::ASCII.GetBytes($pair)
$base64=[System.Convert]::ToBase64String($bytes)
$basicAuthValue="Basic $base64"
$headers=@{Authorization=$basicAuthValue}

$url='https://192.168.1.2/index.asp'
$result=(Invoke-WebRequest -Uri $url -Headers $headers)
($result.AllElements | Where tagName -eq “title”).outerText

```
