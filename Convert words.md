# Convert words
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2013/01/06/convert-words/
```PowerShell
$text="abcdefghij abcd"
$e=""

foreach ($line in $text) {
$n=""
$n+= foreach ($word in ($line.Split()))
{
$chars = for ($i=0;$i -lt $word.length;$i++)
{
$x=$word[$i]
$x=[char]::ConvertToUtf32("$x",0)
[int]$y=$x+8
[char]::ConvertFromUtf32($y)
}
$chars -join ""
}
$e+=$n
}
$e

```
