# Obtener los descriptores de seguridad de todos los ficheros de una unidad
## Filesystem, Permissions, PowerShell 
### URL: https://www.jesusninoc.com/2016/09/10/obtener-los-descriptores-de-seguridad-de-todos-los-ficheros-de-una-unidad/
```PowerShell
Get-ChildItem D:\ -Recurse | %{Get-Acl $_.FullName | Select-Object Sddl}

```
