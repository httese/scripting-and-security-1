# Apagar equipo
## PowerShell 
### URL: https://www.jesusninoc.com/2014/04/01/apagar-equipo/
```PowerShell
$equipo='.'
(get-wmiobject -class win32_operatingsystem -computername $equipo).win32shutdown(12)

```
