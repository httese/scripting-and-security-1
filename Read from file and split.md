# Read from file and split
## PowerShell 
### URL: https://www.jesusninoc.com/2013/01/01/read-from-file-and-split/
```PowerShell
"hola:adios" | Out-File joinCSV.csv
$a=Get-Content joinCSV.csv

foreach($i in $a)
{
    $ii=$i.Split(":")
    $ii[1]
}

```
