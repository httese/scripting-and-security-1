# Extract images
## PowerShell 
### URL: https://www.jesusninoc.com/2013/01/30/extract-images/
```PowerShell
$urls="https://www.pinterest.es/microsoft/red-green-cyan-yellow/?autologin=true"
$result=(Invoke-WebRequest -Uri $urls -UserAgent " " -UseBasicParsing).Images
$result

```
