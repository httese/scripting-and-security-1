# Ver información en el Registro de Windows sobre las Variables de entorno
## PowerShell, Registry 
### URL: https://www.jesusninoc.com/2015/03/23/ver-informacion-en-el-registro-de-windows-sobre-las-variables-de-entorno/
```PowerShell
Get-ItemProperty -Path ‘Registry::HKEY_CURRENT_USER\Environment’ | % {Write-host $_}

```
