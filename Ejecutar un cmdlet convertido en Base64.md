# Ejecutar un cmdlet convertido en Base64
## PowerShell 
### URL: https://www.jesusninoc.com/2016/09/24/ejecutar-un-cmdlet-convertido-en-base64/
```PowerShell
$argumentos = '-encodedcommand ' + [System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes('Get-Process'))
Start-Process -FilePath powershell.exe -ArgumentList $argumentos

#En una línea
Start-Process -FilePath powershell.exe -ArgumentList ('-encodedcommand ' + [System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes('Get-Process')))

```
