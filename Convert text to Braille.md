# Convert text to Braille
## PowerShell, Web Service 
### URL: https://www.jesusninoc.com/2016/02/03/convert-text-to-braille/
```PowerShell
$outFile = "D:\power\" + "Braille" + (Get-Date -UFormat %Y%m%d_%H%M%S) + ".jpg"
Set-Content -Path $outFile -Value (New-WebServiceProxy -uri "https://www.webservicex.net/braille.asmx?WSDL").BrailleText('hi',80) -Encoding Byte

```
