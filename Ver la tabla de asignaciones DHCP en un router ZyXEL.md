# Ver la tabla de asignaciones DHCP en un router ZyXEL
## Automation, Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/12/16/ver-la-tabla-de-asignaciones-dhcp-en-un-router-zyxel/
```PowerShell
$user="admin"
$pass="admin123"
$pair="${user}:${pass}"
$bytes=[System.Text.Encoding]::ASCII.GetBytes($pair)
$base64=[System.Convert]::ToBase64String($bytes)
$basicAuthValue="Basic $base64"
$headers=@{Authorization=$basicAuthValue}

$url='http://192.168.1.1:89/rpDHCP.html'
$result=(Invoke-WebRequest -Uri $url -Headers $headers)
($result.AllElements | Where tagName -eq “title”).outerText
$result.AllElements | Where tagName -eq “td” | %{if($_.innerText -match '192.168' -and $_.innerText -match '-'){$_.innerText}}

```
