# Reducir texto con puntos suspensivos
## PowerShell 
### URL: https://www.jesusninoc.com/2015/11/27/reducir-texto-con-puntos-suspensivos/
```PowerShell
$LongitudMax = 10
$Texto = 'Texto para acortar'

if ($Texto.Length -gt $LongitudMax)
{
$Texto.Substring(0,$LongitudMax) + '...'
}
else
{
$Texto
}

```
