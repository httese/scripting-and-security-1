# Mostrar el nombre y tamaño de los ficheros de una unidad
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2016/04/26/mostrar-el-nombre-y-tamano-de-los-ficheros-de-una-unidad/
```PowerShell
Get-ChildItem D:\ -Recurse | Select-Object Name,Length

```
