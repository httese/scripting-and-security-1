# Eliminar ficheros que contienen una cadena
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2016/04/27/eliminar-ficheros-que-contienen-una-cadena/
```PowerShell
Get-ChildItem D:\prueba | %{if(Get-Content $_.FullName | Select-String "borrar"){Remove-Item $_.FullName -WhatIf}}

```
