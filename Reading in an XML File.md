# Reading in an XML File
## PowerShell 
### URL: https://www.jesusninoc.com/2014/11/13/reading-xml-file/
```PowerShell
Get-ChildItem c:\scripts | Export-Clixml c:\scripts\files.xml

```
```PowerShell
$A = Import-Clixml c:\scripts\files.xml

```
```PowerShell
$A | Sort-Object length

```
