# Algoritmo de descifrado sencillo
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2016/03/07/algoritmo-de-descifrado-sencillo-2/
```PowerShell
$cifrado="ijklmnopqr(ijkl"
$var=8
(0..($cifrado.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($cifrado[$_].ToString(),0)-$var)}) -join ""

```
# Algoritmo de descifrado sencillo
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/02/12/algoritmo-de-descifrado-sencillo/
```PowerShell
$text=”ijklmnopqr ijkl”
$e=””

foreach ($line in $text) {
$n=””
$n+= foreach ($word in ($line.Split()))
{
$chars = for ($i=0;$i -lt $word.length;$i++)
{
$x=$word[$i]
$x=[char]::ConvertToUtf32(“$x”,0)
[int]$y=$x-8
[char]::ConvertFromUtf32($y)
}
$chars -join “”
}
$e+=$n
}
$e

```
