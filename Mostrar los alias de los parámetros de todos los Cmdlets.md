# Mostrar los alias de los parámetros de todos los Cmdlets
## PowerShell 
### URL: https://www.jesusninoc.com/2015/11/29/mostrar-los-alias-de-los-parametros-de-todos-los-cmdlets/
```PowerShell
(Get-Command).Parameters.Values | Select-Object -Property Name, Aliases

```
