# Saving Data as a Comma-Separated Values File
## PowerShell 
### URL: https://www.jesusninoc.com/2014/11/14/saving-data-comma-separated-values-file/
```PowerShell
Get-Process | Export-Csv c:\scripts\test.txt

```
```PowerShell
Get-Process | Export-Csv c:\scripts\test.txt -encoding "unicode"

```
```PowerShell
#TYPE System.Diagnostics.Process

```
```PowerShell
Get-Process | Export-Csv c:\scripts\test.txt -notype

```
```PowerShell
PS C:\Documents and Settings\user> Get-Process | Export-Csv c:\scripts\test.txt
Export-Csv : Access to the path 'C:\scripts\test.txt' is denied.

```
```PowerShell
Get-Process | Export-Csv c:\scripts\test.txt -force

```
