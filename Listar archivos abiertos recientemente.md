# Listar archivos abiertos recientemente
## Filesystem, Forensic analysis, PowerShell 
### URL: https://www.jesusninoc.com/2016/05/01/listar-archivos-abiertos-recientemente/
```PowerShell
Get-ChildItem ([Environment]::GetFolderPath("Recent"))

```
