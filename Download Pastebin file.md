# Download Pastebin file
## PHP, PowerShell 
### URL: https://www.jesusninoc.com/2013/03/26/download-pastebin-file/
```PowerShell
$url='https://pastebin.com/download.php?i='
$par='xxxxxxxx'
$result=(Invoke-WebRequest -Uri $url+$par)
$result.RawContent

```
