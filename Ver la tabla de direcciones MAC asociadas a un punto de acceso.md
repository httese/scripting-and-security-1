# Ver la tabla de direcciones MAC asociadas a un punto de acceso
## Automation, Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/12/15/ver-la-tabla-de-direcciones-mac-asociadas-a-un-punto-de-acceso/
```PowerShell
$user="admin"
$pass="admin"
$pair="${user}:${pass}"
$bytes=[System.Text.Encoding]::ASCII.GetBytes($pair)
$base64=[System.Convert]::ToBase64String($bytes)
$basicAuthValue="Basic $base64"
$headers=@{Authorization=$basicAuthValue}

$url='http://192.168.1.2/wlstatbl.asp'
$result=(Invoke-WebRequest -Uri $url -Headers $headers)
($result.AllElements | Where tagName -eq “title”).outerText
$result.AllElements | Where tagName -eq “td” | %{if($_.innerText -match ':'){$_.innerText}}

```
