# Leer los ficheros que hay dentro de un directorio, cifrarlos, almacenarlos en un directorio y comprimir el directorio
## Cryptography, Filesystem, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/03/27/leer-los-ficheros-que-hay-dentro-de-un-directorio-cifrarlos-almacenarlos-en-un-directorio-y-comprimir-el-directorio/
```PowerShell
#Para descrifrar ver: https://www.jesusninoc.com/2015/02/12/algoritmo-de-descifrado-sencillo/ (Algoritmo de descifrado sencillo)

foreach ($fichero in ls F:\power\ficheros)
{
$e=''
foreach ($line in gc F:\power\ficheros\$fichero) {
$n=''
$n+= foreach ($word in ($line.Split()))
{
$chars = for ($i=0;$i -lt $word.length;$i++)
{
$x=$word[$i]
$x=[char]::ConvertToUtf32(“$x”,0)
[int]$y=$x+8
[char]::ConvertFromUtf32($y)
}
$chars -join ''
}
$e+=$n
}
$e | out-file F:\power\ficherosconvertidos\$fichero
Compress-Archive -LiteralPathF:\power\ficherosconvertidos\$fichero –CompressionLevel Optimal -DestinationPath C:\powershell\comprimidoconvertido.zip
}

```
