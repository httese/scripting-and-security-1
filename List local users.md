# List local users
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2016/07/02/list-local-users/
```PowerShell
$adsi = [ADSI]"WinNT://$env:COMPUTERNAME"
$adsi.Children | Where-Object {$_.SchemaClassName  -eq 'user'} | Select-Object Name

```
