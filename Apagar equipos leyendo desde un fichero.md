# Apagar equipos leyendo desde un fichero
## PowerShell 
### URL: https://www.jesusninoc.com/2014/04/02/apagar-equipos-leyendo-desde-un-fichero/
```PowerShell
$dirpc="F:\pcs.txt"
foreach ($ap in Get-Content $dirpc)
{
(Get-WmiObject -class win32_operatingsystem -computername $ap).win32shutdown(12)
}

```
