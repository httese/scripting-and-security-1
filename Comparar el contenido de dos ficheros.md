# Comparar el contenido de dos ficheros
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2015/11/24/comparar-el-contenido-de-dos-ficheros/
```PowerShell
Compare-Object -ReferenceObject $(Get-Content F:\fichero1.txt) -DifferenceObject $(Get-Content F:\fichero2.txt)

```
