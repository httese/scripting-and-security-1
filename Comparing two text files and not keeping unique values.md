# Comparing two text files and not keeping unique values
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2014/11/29/comparing-two-text-files-keeping-unique-values/
```PowerShell
Compare-Object (get-content .\prueba1.txt) (get-content .\prueba2.txt) | where {$_.SideIndicator -eq "<=" -or $_.SideIndicator -eq "=>"}

```
