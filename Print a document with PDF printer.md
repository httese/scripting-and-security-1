# Print a document with PDF printer
## PowerShell 
### URL: https://www.jesusninoc.com/2014/02/12/print-a-document-with-pdf-printer/
```PowerShell
$a=Get-Content F:\power\ho.txt
Out-Printer -InputObject $a -name "PDF24 PDF"

```
