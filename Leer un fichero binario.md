# Leer un fichero binario
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2015/02/10/leer-un-fichero-binario/
```PowerShell
$bytes = [System.IO.File]::ReadAllBytes('F:\power\dibujos\1.bmp')

foreach($off in $bytes)
{
Write-Host $off
}

```
